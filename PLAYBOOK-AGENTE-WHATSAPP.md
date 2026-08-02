# Playbook — Conectar um agente de IA ao WhatsApp do negócio da sua esposa

> Para quem já tem: um micro SaaS/CRM funcionando com banco de dados próprio.
> Para quem não tem: experiência com APIs de mensageria e agentes.
> Objetivo: o agente responde no WhatsApp, **lê** o banco dela, **registra pedidos** e organiza a rotina — com ela aprovando o que importa.
> Regra de ouro do playbook inteiro: **construa na ordem das fases e não pule o modo-espião (Fase 2).** Cada fase funciona sozinha e já entrega valor.

---

## Visão geral da arquitetura (o mapa mental)

```
Cliente da sua esposa                     Sua esposa
        │  WhatsApp                            │  WhatsApp
        ▼                                      ▼
┌─────────────────────────────────────────────────────┐
│  NÚMERO DO AGENTE (WhatsApp Business Cloud API)     │
│  → tudo que chega vira um webhook (HTTP POST)       │
└──────────────────────────┬──────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────┐
│  SEU SERVIDOR (1 função/endpoint só)                │
│  1. recebe a mensagem                               │
│  2. monta o contexto e chama o Claude com "tools"   │
│  3. executa a tool que o Claude pedir               │
│  4. devolve a resposta pelo WhatsApp                │
│  5. grava TUDO numa tabela de log                   │
└──────────────┬───────────────────────┬──────────────┘
               ▼                       ▼
   ┌───────────────────┐   ┌───────────────────────┐
   │  Claude API       │   │  Banco do CRM dela    │
   │  (o cérebro)      │   │  (leitura via views;  │
   │                   │   │   escrita via tools   │
   │                   │   │   com aprovação)      │
   └───────────────────┘   └───────────────────────┘
```

O agente **não é** um fluxo de chatbot com menuzinhos. É: mensagem → LLM decide qual ferramenta usar → executa → responde. Você escreve as ferramentas (funções pequenas e seguras); o Claude escolhe quando usá-las.

---

## Fase 0 — Quatro decisões antes de escrever qualquer coisa (1 noite)

**D1. Número dedicado para o agente.** Nunca conecte no número pessoal dela. Compre um chip pré-pago novo (ou número virtual). Motivos: (a) se a Meta banir, o número dela sobrevive; (b) separa "falar com a Bia" de "falar com o assistente"; (c) a API oficial exige um número sem WhatsApp comum ativo.

**D2. API oficial (Cloud API da Meta) — recomendada.** Alternativa não-oficial (Z-API, Evolution API) é mais fácil de começar, mas viola os termos da Meta e o risco é banimento do número. Como é o negócio da sua esposa (canal crítico), use a oficial. Custo real: **mensagens de resposta dentro da janela de 24h são gratuitas**; você só paga templates proativos (~R$ 0,03 utility). Para 1 negócio, isso é ~R$ 0–15/mês.

**D3. Onde roda o código.** Se o CRM foi feito no **Lovable** (caso desta seção): isso não é uma escolha, é obrigatório — a *service role key* do banco **não é extraível** do Lovable Cloud (nem pelo dashboard, nem para você copiar). Ela só existe como variável de ambiente dentro de uma Edge Function. Logo, o webhook **tem que** rodar como Edge Function no mesmo projeto; não há como montar um servidor externo (Railway/Render) com acesso de escrita total ao banco. Se sua stack não é Lovable/Supabase: aí sim, servidorzinho Node/Python externo (~US$ 5/mês) com UMA rota HTTPS pública `POST /webhook`.

**D4. Escopo da v1 — escreva numa frase e cole na parede.** Sugestão: *"O agente responde perguntas sobre pedidos/clientes consultando o banco, registra pedido novo como rascunho e envia para ela aprovar."* Tudo fora disso a v1 responde: "Vou passar para a Bia, ela te responde já 😉".

---

## Fase 0.5 — Preparar o backend, se o CRM foi feito no Lovable

**Você não precisa abrir um Supabase separado.** Quando o Lovable Cloud está ativo num projeto, ele já provisiona um projeto Supabase de verdade por baixo dos panos — banco Postgres, autenticação, storage e Edge Functions. O Lovable dá uma casca visual em cima disso, mas o motor é o mesmo banco que o CRM dela já usa. O agente vai ler e escrever nesse banco; não existe "outro banco" para criar.

Isso também resolve a D3: dá para hospedar o webhook do WhatsApp como uma **Edge Function dentro do mesmo projeto** — ela já nasce com acesso ao banco, sem precisar de Railway/Render. E, no Lovable Cloud, essa é a **única** forma de ter acesso de escrita total ao banco (ver D3) — a service role key não sai do projeto.

**O que precisa estar pronto, em ordem:**
1. **Views somente-leitura** — o agente consulta clientes/pedidos/agenda sem ver colunas sensíveis nem rodar SQL livre.
2. **Verificar triggers existentes que reagem a INSERT/UPDATE** nas tabelas que o agente vai escrever (ex.: baixa automática de estoque numa venda). Se algum trigger não distinguir "rascunho ainda não aprovado" de "confirmado", ele vai disparar cedo demais quando o agente criar o registro — descubra e corrija **antes** do próximo passo.
3. **Uma função de escrita controlada (RPC)** — o agente cria pedido como `rascunho`, nunca escreve direto nas tabelas.
4. **A Edge Function do webhook** — recebe a mensagem do WhatsApp, chama o Claude, executa a tool certa, responde.

Você não escreve nada disso à mão — pede ao próprio Lovable, com os três prompts abaixo, **um de cada vez**, nesta ordem.

**Prompt 1 — Descoberta (não muda nada, só mapeia):**

```
Antes de pedir mudanças, preciso entender o backend atual deste projeto.
Por favor, sem alterar nada:
1. Liste todas as tabelas do banco com suas colunas e tipos.
2. Diga se Row Level Security (RLS) está ativado em cada tabela e quais
   políticas existem.
3. Mostre onde nas configurações do projeto eu encontro a URL do projeto
   Supabase, a "anon key" e a "service role key".
4. Diga se este projeto já tem alguma Edge Function criada.
```

Use o resultado para ajustar os nomes de tabela/coluna reais nos prompts seguintes (os nomes abaixo são um chute razoável, não necessariamente os dela).

**Antes do Prompt 2, se o Prompt 1 revelou algum trigger nas tabelas que o agente vai escrever** (baixa de estoque, atualização de saldo, o que for): peça ao Lovable para mostrar o código dele e confirme se ele age em cima do registro *assim que criado* ou só quando algum campo de status/aprovação muda. Se agir sempre, peça a correção (gate por status) antes de seguir — senão o "rascunho" do agente já vai produzir efeito colateral real no banco, antes mesmo de ela aprovar.

**Prompt 2 — Views seguras + função de escrita:**

```
Quero preparar este banco para um agente de IA externo consultar e criar
registros com segurança, sem dar acesso direto às tabelas.

1. Crie estas views somente-leitura (ajuste os nomes de coluna aos nomes
   reais das minhas tabelas):
   - vw_clientes_resumo: id, nome, telefone e outros dados não sensíveis
     (sem documento, endereço completo ou dados de pagamento).
   - vw_pedidos_resumo: id, cliente, itens, valor, status, data.
   - vw_agenda_semana: pedidos ou atendimentos dos próximos 7 dias.
   Se não tiver certeza do que é sensível, me pergunte antes de decidir.

2. Crie uma função no banco (RPC) chamada criar_pedido_rascunho que recebe
   cliente_id, itens, valor e data_entrega, insere um novo pedido com
   status = 'rascunho' e retorna o id criado. Essa função só pode ser
   chamada pela service role, nunca pelo público (anon).

3. Mantenha o RLS das tabelas originais exatamente como está hoje — essas
   views e essa função são a única porta de entrada para o agente.

Não crie nenhuma tela nova no app, isso é só estrutura de banco.
```

**Prompt 3 — A Edge Function do webhook:**

```
Crie uma Edge Function chamada whatsapp-webhook neste projeto que:

1. No método GET, responde ao desafio de verificação da WhatsApp Cloud API
   (parâmetros hub.mode, hub.verify_token, hub.challenge), comparando
   hub.verify_token com um secret chamado WHATSAPP_VERIFY_TOKEN.
2. No método POST, recebe a mensagem do WhatsApp, extrai o número do
   remetente, o texto e o message_id.
3. Chama a API da Anthropic (Claude) usando o secret ANTHROPIC_API_KEY,
   oferecendo como tools: buscar_cliente, pedidos_do_dia, resumo_financeiro,
   pendencias e criar_pedido_rascunho (baseadas nas views e na função
   criadas antes).
4. Envia a resposta de volta usando a WhatsApp Cloud API, com os secrets
   WHATSAPP_TOKEN e WHATSAPP_PHONE_NUMBER_ID.
5. Grava cada mensagem recebida, cada tool chamada e cada resposta enviada
   numa tabela agente_logs (crie se não existir), guardando o message_id
   para não processar a mesma mensagem duas vezes.
6. Importante: essa função é chamada pelo servidor da Meta, não por um
   usuário logado — configure-a como pública, sem verificação de JWT.

Depois de criar, me diga exatamente onde eu cadastro os secrets
ANTHROPIC_API_KEY, WHATSAPP_TOKEN, WHATSAPP_VERIFY_TOKEN e
WHATSAPP_PHONE_NUMBER_ID.
```

**Onde pegar as credenciais depois:** no menu do projeto Lovable, procure algo como **Cloud / Backend / "Manage backend"** — normalmente abre o **Supabase Studio** real do projeto. Lá: Settings → API → Project URL, anon key e service role key; e uma seção de Secrets/Edge Functions para guardar as chaves da Anthropic e do WhatsApp. Se não achar de primeira, pergunte direto ao Lovable: *"onde vejo a URL e as chaves do Supabase deste projeto?"*

**Saída de emergência:** se o Lovable Cloud algum dia se mostrar travado demais (não deixar ver a service role key, por exemplo), existe a opção **"Connect to Supabase"** com uma conta Supabase própria — dashboard completo, sem intermediário. Comece pelo caminho simples; raramente é preciso.

---

## Fase 1 — Conectar o WhatsApp (1 fim de semana)

Passo a passo da Cloud API (gratuita, direto com a Meta, sem BSP):

1. **developers.facebook.com** → criar conta de desenvolvedor → "Criar app" → tipo **Business**.
2. No app, adicionar o produto **WhatsApp**. A Meta te dá um **número de teste** e um token temporário — você já consegue mandar mensagem pra você mesmo em 10 minutos. Faça isso primeiro; é o "hello world" que destrava tudo.
3. Criar/vincular o **Meta Business Manager** e depois **adicionar o número real** (o chip novo da D1). Verificação por SMS. A verificação da empresa (Business Verification) pode ser pedida depois — com CNPJ MEI dela resolve.
4. Gerar **token permanente**: Business Settings → System Users → criar system user → gerar token com permissão `whatsapp_business_messaging`.
5. Configurar o **webhook**: URL da sua função (Fase 0-D3) + um "verify token" que você inventa. Assinar o campo `messages`.
6. Testar o ciclo completo: mandar "oi" do seu celular → ver o JSON chegar no log da função → responder via API (`POST /{phone_number_id}/messages`).

**Se travar em qualquer passo:** cole o erro no Claude e peça o passo seguinte. Esta fase é 90% burocracia de console e 10% código.

**Cheat sheet de custos da API:** receber = grátis · responder em até 24h da última mensagem do cliente = grátis · iniciar conversa (template utility, ex.: "seu pedido está pronto") ≈ R$ 0,03 · template marketing ≈ R$ 0,31 (evite).

---

## Fase 2 — Modo-espião: o agente que só lê e sugere (1–2 fins de semana)

**A fase mais importante — e a mais ignorada.** Antes de deixar o agente falar com clientes, ele fala **só com ela** (e com você), num grupo ou no privado:

- Toda manhã, 8h: *"Bom dia! Hoje: 3 entregas (Ana 14h, Júlia 16h…), 2 pedidos sem sinal pago, 1 cliente sem resposta desde ontem."* (um cron job + 1 template utility)
- Ela pergunta em linguagem natural: *"quanto vendi essa semana?"*, *"o que a Ana pediu da última vez?"* → o agente consulta o banco e responde.

Por que começar assim: risco zero (erro do agente = mensagem errada pra ela, não pra cliente), você aprende o que ela realmente pergunta (isso vira o backlog real), e ela cria confiança no bicho antes de delegar.

### Como dar o banco ao agente COM SEGURANÇA

*Se o CRM é Lovable, isso já foi feito na Fase 0.5 — pule para "O esqueleto do cérebro" abaixo.* Para qualquer outra stack, o princípio é o mesmo:

Nunca dê SQL livre nem a chave admin do banco ao LLM. Em vez disso:

1. Crie **views de leitura** com o que o agente pode ver: `vw_pedidos_resumo`, `vw_clientes_basico`, `vw_agenda_semana` (sem colunas sensíveis).
2. Crie um **usuário/role read-only** no banco que só enxerga essas views.
3. Exponha cada consulta como uma **tool tipada** — função com parâmetros fixos, não SQL:

```
Tools da v1 (leitura):
- buscar_cliente(nome_ou_telefone)     → dados básicos + últimos pedidos
- pedidos_do_dia(data)                 → lista de entregas/atendimentos
- resumo_financeiro(periodo)           → vendido, recebido, pendente
- pendencias()                         → pedidos sem sinal, clientes sem resposta
```

### O esqueleto do cérebro (é menor do que parece)

Pseudocódigo do endpoint — peça ao Claude Code para gerar a versão real na sua stack:

```python
def webhook(msg):
    log(msg)                                   # 1. grava tudo
    historico = ultimas_mensagens(msg.de, 10)  # 2. contexto da conversa
    resposta = claude(
        system = PROMPT_DO_AGENTE,             # quem ele é, o que pode, tom de voz
        messages = historico + [msg],
        tools = [buscar_cliente, pedidos_do_dia, resumo_financeiro, pendencias],
    )                                          # 3. o SDK executa as tools que ele pedir
    enviar_whatsapp(msg.de, resposta)          # 4. responde
```

O `PROMPT_DO_AGENTE` é meia página: quem é o negócio, o que cada tool faz, tom de voz dela, e as regras ("nunca invente dados; se a tool não retornar, diga que não encontrou; assuntos fora do escopo → encaminhar").

**Prompt pronto para você usar no Claude Code:** *"Tenho um CRM em [stack] com estas tabelas: [cole o schema]. Crie: (1) as views read-only acima, (2) uma função webhook para WhatsApp Cloud API que chama a API da Anthropic com tool use usando essas views como tools, (3) tabela de log de todas as mensagens e chamadas de tool. Modelo: claude-sonnet, com respostas curtas em PT-BR."*

---

## Fase 3 — Escrever no banco: pedidos com aprovação (1–2 fins de semana)

Agora o agente passa a **fazer**, não só ler — mas nada vira definitivo sem um toque dela.

1. Nova tool: `criar_pedido_rascunho(cliente, itens, valor, data_entrega)` → grava com `status = 'rascunho'`.
2. O agente manda **para ela**: *"Pedido novo da Ana: 1 bolo red velvet, entrega sáb 15h, R$ 180. Confirmar?"* com **botões** [✓ Confirmar] [✎ Corrigir] [✗ Descartar] (a Cloud API tem botões interativos nativos — use-os, não "responda 1 para sim").
3. Ela toca ✓ → `status = 'confirmado'` → o agente confirma com o cliente e agenda o lembrete de entrega.
4. **Toda escrita passa por rascunho + aprovação.** Sem exceção na v1. Isso é o que o relatório chama de "classe Confirmada" — e é o que evita o desastre de confiança.

Regras de engenharia que evitam 80% das dores:
- **Idempotência:** a Meta reenvia webhooks; guarde o `message_id` processado e ignore duplicatas (senão: pedido em dobro).
- **Log de tudo:** tabela `acoes_agente` (quem pediu, tool, parâmetros, resultado, aprovado por quem, quando). É seu debug e sua auditoria.
- **Fallback humano:** qualquer coisa que o agente não entender com confiança → "vou passar para a Bia" + notificação pra ela. Um agente que sabe dizer "não sei" é confiável; um que chuta, não.

---

## Fase 4 — Abrir para os clientes dela (quando ela pedir, não antes)

Sinal de prontidão: na Fase 2/3, ela usa o agente **todo dia** e a taxa de "resposta errada" no log está baixa. Então:

1. O número do agente entra no perfil/bio dela como "pedidos e agendamentos".
2. Clientes falam com o agente para: consultar status do pedido, fazer novo pedido (vira rascunho→aprovação), receber confirmações e lembretes.
3. Mensagem de apresentação honesta: *"Oi! Sou o assistente da [marca]. Anoto seu pedido e a [nome] confirma em seguida 💚"* — não finja ser humana.
4. Ela mantém um **comando de emergência**: mandar "pausa" pro agente silencia o atendimento automático daquele cliente e ela assume a conversa.

---

## Guardrails permanentes (imprimir e obedecer)

- O agente **nunca**: negocia preço, promete prazo que não está na agenda, apaga registro, fala de assunto pessoal, envia mensagem em massa.
- Dinheiro e compromisso são sempre **rascunho → aprovação**.
- Dados: colete o mínimo; não mande para o LLM nada além do necessário para a tarefa; use endpoint com retenção limitada; apague conversas antigas de clientes num prazo definido (LGPD básico de MEI).
- Um erro com cliente real = post-mortem de 15 minutos no jantar: o que o log mostra? qual regra faltou?

## Custos mensais estimados (1 negócio, uso real)

| Item | Custo |
|---|---|
| WhatsApp Cloud API (majoritariamente respostas na janela 24h) | R$ 0–15 |
| Claude API (Sonnet p/ conversa, ~1–2 mil interações) | R$ 30–80 |
| Servidor/função (Railway/Render ou grátis na infra atual) | R$ 0–30 |
| Chip do número dedicado | R$ 0–20 |
| **Total** | **~R$ 60–145/mês** |

## Cronograma realista (trabalhando fins de semana)

| Semana | Entrega | "Pronto quando…" |
|---|---|---|
| 1 | Fase 0 + 0.5 (se Lovable) + 1: banco preparado, número conectado, webhook vivo | você manda "oi" e recebe eco automático |
| 2–3 | Fase 2: agente-espião com 4 tools de leitura + resumo matinal | ela pergunta "quanto vendi?" e a resposta bate com o CRM |
| 4–5 | Fase 3: pedido-rascunho com botões de aprovação | 5 pedidos reais registrados sem retrabalho |
| 6+ | Fase 4: clientes falando com o agente | 1 semana sem intervenção sua no código |

## Erros de iniciante que este playbook já evitou por você

1. Conectar no número pessoal dela (banimento = catástrofe).
2. Começar pelo atendimento a clientes em vez do modo-espião.
3. Dar SQL livre ou service key ao LLM em vez de tools tipadas sobre views.
4. Fluxo de chatbot com menus em vez de agente com tools (vira árvore infinita de ifs).
5. Esquecer idempotência do webhook (pedidos duplicados no primeiro dia).
6. Não logar as chamadas de tool (sem log, todo bug é um mistério).
7. Prometer autonomia total pra ela ("faz sozinho!") — prometa "anota e te pede ok", entregue isso bem, e a confiança vem.

## O bônus estratégico

Isto **é** a Fase 2 do relatório (`RELATORIO-FINAL.md`) com cliente zero de custo zero e feedback no café da manhã. Tudo o que você medir aqui — quais perguntas ela faz, taxa de exceção, minutos de operação, o que ela aprova sem ler vs. o que ela corrige — é exatamente o dado que o plano de validação pede antes de testar o nicho de mercado (psicólogos) com clientes pagantes. Guarde o log desde o dia 1: ele é a sua pesquisa.

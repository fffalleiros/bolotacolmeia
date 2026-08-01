# Pesquisa de Mercado — Service-as-a-Software para Solopreneurs com WhatsApp como Interface Principal

**Data:** 01/08/2026 · **Metodologia:** pesquisa web em fontes primárias e oficiais (IBGE, Receita Federal/Mapa de Empresas, Sebrae, Banco Central, conselhos de classe), imprensa especializada, sites e preços públicos de empresas, bases de startups e avaliações de usuários (Reclame Aqui, lojas de apps), conduzida por 6 frentes paralelas de pesquisa. Evidência bruta com fontes e URLs nos dossiês em `pesquisa/dossies/`. Este relatório separa **fatos** (com fonte), **estimativas** (com premissa declarada) e **inferências/opiniões** (julgamento analítico).

---

## 1. Resumo executivo

**Decisão: VERTICALIZAR.** A tese "solopreneurs não querem mais um software, querem as tarefas executadas" não é validável — nem financiável — na forma horizontal proposta no briefing ("agente administrativo completo para todo solopreneur"). Mas há um recorte estreito onde a mesma tese tem dor comprovada, frequência semanal, ticket compatível e concorrência mal posicionada: **profissionais de saúde autônomos de sessão recorrente, começando por psicólogos**, com um único fluxo — o **ciclo sessão→dinheiro** (confirmar a sessão, cobrar via Pix após a sessão, dar baixa e avisar quem não pagou).

Os fatos centrais que sustentam essa conclusão:

- **O canal está validado como nenhum outro no mundo:** 82% dos MEIs/MPEs brasileiros usam WhatsApp como principal canal de vendas (Sebrae, 2026); o app está em 99% dos smartphones; 97% dos MEIs aceitam Pix. A infraestrutura conversa+pagamento existe e é hábito.
- **A dor administrativa é real e medida:** PMEs brasileiras gastam ~21h/semana com burocracia financeira; 39% gerem despesas em caderno/planilha; no-show em consultórios é de 20–30% da agenda; 71% dos trabalhadores independentes já tiveram problema para receber; lembretes por WhatsApp reduzem faltas em 19–38% (estudos, não marketing).
- **Mas a tese horizontal falha em três pontos:** (1) **disposição a pagar** — a renda média do MEI é R$ 5,5 mil/mês e ~40% estão inadimplentes até com o DAS de ~R$ 80; o teto realista de preço é R$ 30–150/mês, incompatível com um "back office completo"; (2) **concorrência assimétrica** — a Meta lançou globalmente (jun/2026) o Business Agent gratuito no WhatsApp, o Jota levantou R$ 150M para ser o "agente financeiro do empreendedor" no WhatsApp e o Nubank testa assistente de Pix com 2 milhões de usuários; (3) **confiabilidade** — o melhor agente de IA completa autonomamente ~24% de tarefas reais de escritório (CMU/TheAgentCompany); prometer "funcionário digital que faz tudo" é prometer o que a tecnologia não entrega, e o colapso da Bench (35 mil clientes abandonados) mostra o custo de fingir margem de software num serviço com humanos escondidos.
- **O recorte vertical sobrevive a essas três objeções:** o psicólogo autônomo tem ticket de sessão de R$ 178–258 (referência CFP), então **um único no-show evitado por mês paga 2–3× a assinatura**; a Meta/Jota/Nubank não cobrem o workflow clínico-administrativo brasileiro (confirmação com política de cancelamento, cobrança sem constrangimento, recibo/NFS-e, sigilo); e o fluxo é estreito e padronizado o bastante (sessão de 50 min, horário fixo, semanal) para automação confiável com aprovação humana.

**Score final ponderado de viabilidade: 6,2/10 — oportunidade incerta, no limiar superior da faixa** (o que dita a conduta: não construir plataforma agora; verticalizar, reduzir o escopo ao ciclo sessão→dinheiro e comprar as duas informações que faltam — preço e retenção — com um experimento de < R$ 5 mil).

**Menor experimento comercial:** 20 entrevistas com psicólogos autônomos + **pré-venda paga de um piloto concierge** (R$ 79–99/mês, operado manualmente atrás de um número de WhatsApp com Google Calendar + Asaas) para 10 clientes por 6 semanas. Custo total estimado < R$ 5 mil e ~6 semanas. Critério de avanço: ≥10 pagantes com ≥70% de renovação no 2º mês e redução mensurável de faltas/atrasos de pagamento. Critério de rejeição: <15% de conversão entrevista→pagamento ou churn >40% no 1º mês.

---

## 2. Descrição da oportunidade

A proposta analisada: um "agente administrativo digital" contratado por solopreneurs, operando via WhatsApp, que executa (não apenas registra) tarefas administrativas — agenda, confirmações, cobranças, notas fiscais, despesas, estoque, relatórios — usando um software interno invisível. A empresa vende **serviço executado**, não licença de software.

O que a pesquisa confirmou sobre a oportunidade em tese:
- O trabalho administrativo do pequeno negócio brasileiro acontece hoje em WhatsApp + caderno + planilha (82% / 39% — Sebrae, CNN Brasil 2026). O "sistema" a substituir não é um ERP: é o caderno.
- O mercado formal é grande e cresce: 12,7–13 milhões de MEIs ativos, 3,8 milhões de aberturas em 2025 (recorde), 26,1 milhões de trabalhadores por conta própria (IBGE 2025).
- Há vento regulatório: NFS-e nacional obrigatória para MEI desde 2023, estendida a ME/EPP em set/2026, com API pública do Emissor Nacional.
- Há capital validando a categoria adjacente: Jota (R$ 150M Série A, 2026) e Magie (+150 mil clientes) provam que brasileiros executam operações financeiras por conversa no WhatsApp.

O que a pesquisa refutou:
- **Não há evidência de demanda por um "faz-tudo" administrativo.** A evidência aponta demanda por resultados específicos: não perder cliente por falta, receber sem constrangimento, não anotar errado.
- **"Aprender software" não é a dor que abandona ERPs.** As reclamações reais (Reclame Aqui) são preço, reajuste unilateral, fidelidade e suporte — não complexidade. A narrativa "o cliente odeia telas" é parcialmente mito; o que ele odeia é pagar caro e ficar preso.
- **A emissão de nota fiscal, isolada, vale perto de zero** para MEI: o app oficial gratuito (NFSe Mobile) emite e compartilha no WhatsApp; MEI nem é obrigado a emitir para consumidor final PF.

## 3. Tese central (reformulada após evidência)

Tese original do briefing: *"Solopreneurs não desejam mais um software; desejam que as tarefas administrativas sejam executadas com baixo esforço, baixo custo e alta confiabilidade."*

**Reformulação sustentada pela evidência:** solopreneurs de serviços recorrentes pagam — pouco, mas pagam — por **três resultados** que hoje lhes custam dinheiro e constrangimento: (1) agenda que não fura (no-show de 20–30% com solução comprovada de −19 a −38%); (2) dinheiro que entra sem precisar cobrar pessoalmente (71% já tiveram problema para receber; "cobrar constrange" é documentado em psicólogos e personals); (3) registro que se faz sozinho a partir da conversa que já existe. Tudo o mais — estoque, relatórios, documentos, "memória completa do negócio" — é expansão, não entrada. E a execução precisa nascer **com aprovação humana visível**, porque a delegação autônoma não tem nem confiança do cliente (60% dos empreendedores iniciais receiam IA — GEM 2024) nem confiabilidade técnica (~24% de sucesso autônomo — CMU).

## 4. Problema do cliente (evidência de dor)

| Dor | Evidência | Qualidade da evidência |
|---|---|---|
| Horas de admin | 21h/semana em burocracia financeira (PMEs BR, 2026); 120 dias úteis/ano (Sage, multi-país); 180h/ano só de burocracia (Índice LatAm) | Forte, múltiplas fontes independentes |
| No-show | 20–30% dos agendamentos em clínicas; até 32% da agenda (Doctoralia 2025); R$ 3,2 mil/mês em salões | Média-forte (vendors, mas convergente) |
| Inadimplência/cobrança | 71% dos independentes com problema para receber (Freelancers Union); cobrança manual = mecanismo da inadimplência (personal trainers); "cobrar constrange" (psicólogos, imprensa 2026) | Forte |
| Controle precário | 6/10 com controle financeiro precário; 25% caderno; 10% nada; 61% misturam conta PF/PJ (Sebrae) | Forte |
| Registro com fricção | "Não registra porque não está com o computador aberto na hora" | Média (vendor, mecanismo plausível) |
| Burnout | 62% dos donos relatam burnout mensal; "a papelada nunca acaba" | Média |

Dores **superestimadas** (não construir sobre elas): complexidade de ERPs como causa de abandono; dor fiscal do MEI (obrigação mínima: DAS fixo + declaração anual); desejo de delegar a comunicação com clientes a uma IA falando livremente em nome do profissional — nos nichos de relação pessoal, a conversa É o produto.

## 5. Perfil do solopreneur (Brasil, 2025–2026)

- 12,66 milhões de MEIs ativos (ago/2025, Mapa de Empresas/MDIC) = 52% dos CNPJs do país; 26,1 milhões de conta própria (IBGE), dos quais ~73% informais (19,1 milhões sem CNPJ).
- Renda: MEI médio R$ 5.542/mês de renda familiar; formalizados R$ 6.117/mês; informais ~R$ 2.100–2.300. Teto MEI: R$ 81 mil/ano.
- Fragilidade financeira: ~40% dos MEIs inadimplentes com o próprio DAS (~R$ 80/mês); 29% fecham em até 5 anos — a pior sobrevivência entre pequenos negócios, atribuída pelo Sebrae à baixa capacidade de gestão.
- Digitalização: 82% vendem pelo WhatsApp; 97% aceitam Pix; 47% usam algum software de gestão; 44–51% já usam IA — mas para marketing (74%), não para executar finanças.
- Maiores concentrações de MEI: beleza (>1 milhão), vestuário (~977 mil), construção (~694 mil).

**Implicação dura:** o "solopreneur médio" não é um cliente viável de assinatura — metade é informal, boa parte não paga nem o imposto obrigatório. O cliente viável é o **decil superior profissionalizado**: prestadores de serviço com agenda recorrente, ticket ≥ R$ 100/atendimento e CNPJ ativo.

## 6. Tamanho de mercado — TAM, SAM, SOM (premissas explícitas)

Método: bottom-up por população de profissionais × taxa de adequação × preço realista. Toda linha é **estimativa**; intervalos refletem incerteza.

- **TAM (Brasil, solopreneurs de serviços com agenda/cobrança recorrentes):** dos ~7,6 mi de MEIs de serviços + profissionais liberais fora do MEI, estimamos 4–6 milhões com necessidade recorrente de agenda+cobrança (premissa: exclui comércio puro, construção por obra, informais de baixa renda). A R$ 70–100/mês → **R$ 3,4–7,2 bi/ano**. (Número para dimensionar o horizonte, não para o plano de negócio.)
- **SAM (saúde & bem-estar autônomos, alvo do produto vertical):** psicólogos 437 mil (CFP) + fisioterapeutas ~300 mil (estimativa sobre COFFITO 2018) + nutricionistas ~194 mil (CFN) + personal trainers ~100–150 mil autônomos (premissa: 20–30% dos 500 mil CONFEF) ≈ **~1,03–1,08 milhão de registros**. Premissas de corte: ~45% atuando como autônomos com agenda própria (~470 mil); ~40% digitalizados/compradores plausíveis de software (~190 mil). A R$ 90/mês → **SAM ≈ R$ 200 milhões/ano** (intervalo R$ 120–320 mi).
- **SOM (psicólogos, 3 anos):** 437 mil registros → ~50% clinicando como autônomos (~220 mil, premissa baseada no perfil CFP) → ~40% alcançáveis por canais digitais de nicho (~88 mil) → captura de 3–5% em 3 anos = **2.600–4.400 clientes** × R$ 90/mês ≈ **R$ 2,8–4,8 milhões de ARR**. Isso é um negócio de lifestyle/seed, não um unicórnio — a tese de escala depende de expandir para fisio, nutrição e beleza depois do beachhead.

**Honestidade sobre o TAM:** o briefing pede para não superestimar TAM sem disposição a pagar. Aplicando o filtro de WTP comprovada (R$ 40–150/mês pagos hoje a Bling/Trinks/contador), o mercado economicamente real é uma fração de um dígito percentual dos "26 milhões de autônomos" que o pitch ingênuo usaria.

## 7. Tendências

1. **Agentes de IA são a categoria dominante de 2025–2026** (46% do batch YC Spring 2025; US$ 2,8 bi de funding em agentic no 1S2025), com correção em curso: Gartner prevê >40% dos projetos cancelados até 2027; "agent washing" punido.
2. **"Service-as-Software"/"Services: the new software"** (Foundation Capital, Sequoia) é a tese de fundo — com contraponto público de que a margem real fica entre serviço e software por causa da supervisão humana.
3. **A Meta desceu para a camada de aplicação:** Business AI na Índia (mai/2026), Meta Business Agent global (jun/2026) — agente nativo gratuito que responde clientes e agenda. Cobrança por mensagem (jul/2025) e banimento de chatbots de propósito geral (out/2025–jan/2026) mostram poder unilateral da plataforma.
4. **Fintech conversacional brasileira decolou:** Jota (R$ 150M), Magie, Friday, Nubank+OpenAI — o "dinheiro por conversa" está sendo resolvido por gente muito capitalizada.
5. **Infra fiscal virou API pública:** Emissor Nacional de NFS-e com API gratuita; obrigatoriedade se ampliando em set/2026. Emissão vira commodity; orquestração contextual é o espaço restante.
6. **Pix Automático e Open Finance** habilitam cobrança recorrente e iniciação de pagamento por terceiros — a peça que faltava para "cobrar sozinho".

## 8. Análise do Brasil

Síntese (detalhes no dossiê 1): mercado formal grande e em crescimento recorde; canal WhatsApp e trilho Pix universais; dor de gestão documentada; MAS disposição a pagar frágil (renda baixa, 40% inadimplentes no DAS), substitutos gratuitos patrocinados pelo próprio governo (NFSe Mobile, MarketUP, planilhas Sebrae) e churn estrutural (29% dos MEIs morrem em 5 anos). O Brasil é o melhor lugar do mundo para a **interface** dessa ideia (WhatsApp+Pix) e um dos piores para o **ticket** dela.

## 9. Análise internacional

Síntese (detalhes no dossiê 3): a categoria "AI receptionist/admin p/ micro-negócio" existe, é lotada e comoditizada (Rosie US$ 49/mês; centenas de clones white-label); os vencedores são verticais (Slang/restaurantes, Numa/auto, Finaloop/e-commerce); quem tentou servir o solopreneur puro ou subiu de mercado (Avoca → contractors US$ 3M+) ou explodiu (Bench). Fyxer AI (US$ 1M→17M ARR em 8 meses) é o modelo a imitar: escopo estreitíssimo, zero configuração, resultado imediato. Lições completas no dossiê; as que governam este relatório: vertical estreito, human-in-the-loop precificado, cobrar desde o dia 1, não competir com a Meta na camada de chat.

---

## 10. Concorrentes (mapa consolidado)

Matriz resumida por função, segmento, preço e grau de autonomia (detalhes e fontes nos dossiês 2 e 3):

| Empresa | País | Público | Canal | Funções | Autonomia | Preço | Distância da proposta |
|---|---|---|---|---|---|---|---|
| **Jota** | BR | Micro/PME | WhatsApp | Banco + agente financeiro (Pix, boletos, cobrança, Open Finance) | Alta (proativo) | Grátis (monetiza banking) | **Mínima no eixo dinheiro**; não faz agenda/NF/rotina |
| **Magie** | BR | PF/PJ | WhatsApp | Pix, boletos, lembretes | Média-alta | Grátis | Próxima em pagamentos; sem admin |
| **Friday/Fred** | BR | PF | WhatsApp+app | Pagamento de contas | Média | Grátis/freemium | Executor de contas pessoais |
| **Meu Assessor** | BR | Autônomos | WhatsApp | "Equipe" de personas IA: finanças, agenda, tarefas, docs | Média | ~R$ 19,90–40/mês (Hotmart) | **Proposta idêntica**, execução artesanal — valida demanda e teto de preço |
| **Cloudia / ZapAgenda / Clinia / Lia One / Secretária IA** | BR | Clínicas/serviços | WhatsApp | Recepcionista IA: agenda, dúvidas, lembretes | Média | não público / R$ 500–1.400/mês via agências | Executam só agenda; foco no cliente final, não no dono |
| **Anota AI** | BR | Restaurantes | WhatsApp | Pedido→cozinha→pagamento | Alta no vertical | ~R$ 100–210/mês | Prova o modelo "agente vertical que executa" (40 mil estabelecimentos) |
| **MaisMEI** | BR | MEI | App | DAS, NFS-e, declarações | Baixa (self-service) | Freemium | Burocracia MEI sem conversa; 4,7–4,8★, forte em distribuição |
| **Contabilizei** | BR | ME/EPP/autônomos PJ | Web | Contabilidade executada (guias, folha) | Humanos+automação | R$ 195–395/mês | Executa fiscal, não conversacional; 8,9/10 RA |
| **Trinks / AppBarber / Booksy / Fresha** | BR/global | Beleza | App/web | Agenda, comissões, estoque | Baixa (usuário opera) | R$ 0–249/mês | Ferramenta, não agente; base instalada grande |
| **Bling / Conta Azul / Kyte** | BR | Micro/PME | Web/app | ERP completo | Baixa; Kyte PRIME tem IA de conselho | R$ 35–199/mês | Integrações prontas, zero conversa; entrantes óbvios |
| **Meta Business Agent** | Global | Pequenos negócios | WhatsApp | Responde clientes, recomenda, **agenda** | Média | **Grátis** (camada básica) | Comoditiza a camada de atendimento/agendamento genérico |
| **Rosie / Goodcall / Smith.ai** | EUA | Serviços locais | Voz/SMS | AI receptionist | Média (Smith híbrido) | US$ 49–299/mês | Prova preço e commoditização da categoria |
| **Fyxer AI** | UK | Profissionais | E-mail | Triagem inbox, drafts | Média | ~US$ 30/mês | Modelo de execução: escopo estreito, zero setup, ARR explosivo |
| **Collective / Pilot / Bench†** | EUA/CA | Solopreneur S-Corp / SMB | Web | Back-office contábil executado | Humanos+IA | US$ 296–699/mês († faliu) | Teto de preço e lição de margem |

**Classificação:** *Diretos:* Jota, Magie, Meu Assessor (e, no futuro próximo, Meta Business Agent). *Indiretos:* recepcionistas de IA verticais, Anota AI, MaisMEI, organizadores financeiros de WhatsApp (GranaZen, Organizy, Focca, Finlancer). *Substitutos:* NFSe Mobile gratuito, secretária humana (R$ 35–80/h), Contabilizei, planilha+WhatsApp Business (o incumbente real). *Habilitadores:* eNotas/NFE.io/Focus NFe/PlugNotas, Asaas/Efí (Pix), Iniciador/Open Finance, BSPs WhatsApp, Zaia/BotConversa. *Entrantes potenciais:* Nubank (assistente Pix em teste com 2 mi de usuários + OpenAI), Meta, Bling/Conta Azul/Kyte, iFood, Zapia (1M+ usuários, capital Prosus), Sebrae (distribuição gratuita).

## 11. Substitutos

O substituto dominante não é software: é **o próprio dono fazendo à noite, de graça**, com WhatsApp Business gratuito + caderno + Pix no app do banco. Qualquer proposta de valor precisa vencer "grátis + hábito", o que exige ROI monetário demonstrável (falta evitada, pagamento recuperado), não "organização". Substitutos pagos: secretária remota (R$ 500+/mês, qualidade superior, preço proibitivo — delimita o teto), contador de MEI (R$ 50–150/mês por comodidade — delimita a faixa), marketplaces que "resolvem" agenda em troca de comissão de 20% (Zenklub — mostra que o profissional aceita pagar caro quando vem com demanda junto).

## 12. Lacunas de mercado (onde ninguém está)

1. **Ninguém executa o ciclo completo sessão→dinheiro no WhatsApp do profissional autônomo** (confirmação com política de cancelamento + cobrança pós-sessão + baixa + follow-up de inadimplente). Recepcionistas de IA param na agenda; fintechs conversacionais param no pagamento sem contexto de agenda; ERPs têm tudo menos a conversa.
2. **Ninguém é dono do workflow administrativo do profissional de saúde solo** — iClinic/Amplimed servem clínicas; Zenklub/Vittude cobram comissão de marketplace; PsicoManager é prontuário web.
3. **Ninguém empacota "cobrança sem constrangimento" como produto** — a dor emocional de cobrar (documentada em psicólogos e personals) é atacada só por réguas genéricas de cobrança B2B.
4. Emissão de NFS-e/recibo **a partir da conversa** (não de um formulário) segue inexistente como produto massificado.

## 13–15. Segmentação, ranking de nichos e nicho recomendado

Matriz completa com notas 1–5 em 11 critérios no dossiê 5. Ranking final (médias): **1º Psicólogos (4,2)** · 2º Beleza solo (3,9) · 3º Personal trainers (3,8) · 4º empate Fisioterapeutas autônomos (3,7) e Professores particulares (3,7) · 6º Nutricionistas (3,5) · 7º empate Confeiteiras (3,3) e Fotógrafos (3,3) · 9º Advogados/contadores (3,2) · 10º Técnicos de manutenção (3,1).

**Beachhead escolhido: PSICÓLOGOS AUTÔNOMOS.** Justificativa: único segmento que combina (i) recorrência semanal do mesmo pagante — cada paciente gera confirmação+cobrança+recibo toda semana, valor visível em dias; (ii) ticket R$ 178–258/sessão (referência CFP) — 1 no-show evitado/mês ≈ 2–3× a assinatura; um paciente inadimplente recuperado ≈ 8–10×; (iii) unidade de trabalho hiperpadronizada (sessão de 50 min, horário fixo) — automação confiável; (iv) hábito de pagar por plataforma (Zenklub: 20% de comissão ou R$ 499/mês); (v) concorrência posicionada em prontuário/web ou marketplace, não no WhatsApp onde a relação paciente-terapeuta já vive; (vi) aquisição concentrável (CRPs, Instagram "psi empreendedora", contabilidades de nicho como Attualize); (vii) 437 mil registros (CFP) com telepsicologia regulamentada (Res. CFP 09/2024). O risco LGPD/sigilo é real, é administrável mantendo o agente **estritamente administrativo** (zero conteúdo clínico), e uma vez resolvido vira barreira contra genéricos.

**Segunda alternativa:** fisioterapeutas autônomos/domiciliares — mesma mecânica e compliance, frequência maior (2–3 sessões/semana), nenhum incumbente dedicado ao solo; reusa ~90% do produto. **Terceira (escala futura):** beleza solo — maior mercado (~1,3 mi MEIs), mas competição máxima (Fresha grátis, Trinks, AppBarber); entrar só com o motor validado.

**Segmento-armadilha (evitar): confeiteiras/produtores artesanais.** Parece perfeito (o mais WhatsApp-first, dor visceral de pedido errado/sinal não cobrado, pouca concorrência) — mas: disposição a pagar quase nula (margem espremida por insumos, âncora "app grátis"), pedido hipercustomizado que quebra automação e vira atendimento humano disfarçado, receita sazonal → churn no mês fraco. Ganha-se audiência, não receita recorrente.

## 16. Jobs to Be Done (priorizados)

Formato: *Quando ___, eu quero ___, para conseguir ___.* Prioridade = frequência × impacto financeiro × inadequação das soluções atuais × automatizabilidade.

| # | Job | Prioridade |
|---|---|---|
| 1 | Quando um paciente marca uma sessão, quero que a confirmação e o lembrete aconteçam sozinhos, para não perder R$ 200+ com uma falta que eu poderia ter evitado | **P0** |
| 2 | Quando a sessão termina, quero que a cobrança chegue ao paciente sem eu precisar pedir, para receber em dia sem constrangimento | **P0** |
| 3 | Quando um pagamento não cai, quero que alguém insista educadamente por mim, para não acumular inadimplência nem virar "o chato da cobrança" | **P0** |
| 4 | Quando um paciente desmarca em cima da hora, quero que a política de cancelamento seja aplicada automaticamente, para não ter que negociar caso a caso | P1 |
| 5 | Quando recebo um pagamento, quero o registro e o recibo/NF feitos sozinhos, para ter tudo organizado sem digitar em sistema | P1 |
| 6 | Quando termino o mês, quero saber quanto ganhei, quem deve e quantas faltas tive, para decidir preço e agenda sem montar planilha | P1 |
| 7 | Quando um paciente novo chega, quero que os dados dele sejam cadastrados a partir da conversa, para não manter fichas manuais | P2 |
| 8 | Quando estou atendendo o dia inteiro, quero que as mensagens administrativas sejam triadas, para separar vida pessoal e trabalho | P2 |
| 9 | Quando o DAS/obrigações vencem, quero ser lembrado e guiado, para não cair em dívida ativa | P2 |
| 10 | Quando quero crescer, quero preencher horários vagos (lista de espera, remarcações), para aumentar receita sem contratar ninguém | P3 |

Os três P0 formam o **primeiro fluxo operacional**: o ciclo sessão→dinheiro.

## 17. Proposta de valor

Formulações testadas contra os critérios (clareza, credibilidade, apelo econômico, risco de promessa excessiva):

- ❌ "Um funcionário digital para quem trabalha sozinho" — promessa excessiva (a tecnologia entrega ~24% de autonomia real); convida comparação com humano que a IA perde.
- ❌ "Seu negócio organizado sem aprender mais um sistema" — "organização" não tem ROI mensurável; a dor de "aprender sistema" é superestimada (evidência RA).
- ✅ **Principal: "Sua agenda confirmada e seu pagamento na conta — direto no WhatsApp, sem você cobrar ninguém."** Clara, mensurável, emocionalmente calibrada (ataca o constrangimento de cobrar), não promete autonomia total.
- Secundárias: "Cada falta evitada paga o mês do serviço" (apelo econômico, âncora no ticket da sessão); "Você atende. A gente confirma, cobra e anota." (divisão de trabalho honesta); "Sem fidelidade, sem multa, cancele em uma mensagem" (posicionamento direto contra a reclamação nº 1 da categoria no Reclame Aqui).

## 18–19. Produto recomendado e MVP

### 9.1 MVP mínimo (o que testar)
- **Nicho:** psicólogos autônomos com consultório próprio/online, 10–30 sessões/semana.
- **Problema central:** ciclo sessão→dinheiro (confirmação, cobrança, baixa, follow-up).
- **Cinco funções, nada mais:** (1) confirmação de sessão D-1 com botões Sim/Remarcar; (2) cobrança Pix pós-sessão (Asaas) enviada ao paciente ou ao profissional para repasse; (3) conciliação automática ("caiu o Pix da Juliana ✓") e lista viva de pendentes; (4) follow-up de inadimplente em régua educada aprovada pelo profissional; (5) resumo semanal (sessões, faltas, recebido, a receber) por áudio/texto.
- **Integrações mínimas:** WhatsApp (número da empresa, API oficial), Google Calendar (leitura/escrita), Asaas (Pix). Sem NF no MVP (recibo simples em PDF; NFS-e na fase 2).
- **Aprovação vs. automático:** confirmações e lembretes = automáticos; cobrança nova e follow-up = aprovação por 1 toque nas 4 primeiras semanas, depois automático por opt-in; qualquer mensagem fora de template = aprovação sempre.
- **Onboarding:** 1 chamada de 30 min + importação da agenda + cadastro da política de cancelamento e preços. Meta: primeiro valor em 24h.
- **Cobrança do MVP:** R$ 79–99/mês, sem fidelidade, cancelamento por mensagem.
- **Métricas de sucesso:** ver seção 20 (validação).

### 9.2 Produto comercial (pós-validação)
Adiciona: NFS-e/recibo automático a partir do pagamento (via Focus NFe/eNotas ou app nacional com mandato), cadastro de pacientes a partir da conversa, política de cancelamento com cobrança de percentual, lista de espera para horários vagos, painel web mínimo (histórico, exportações, LGPD). Planos: Entrada R$ 79 / Profissional R$ 129 / Premium R$ 199 (ver seção 24).

### 9.3 Visão de plataforma (18–36 meses)
"Sistema operacional do profissional de sessão": múltiplos verticais de saúde/bem-estar, Pix Automático para pacotes/mensalidades, antecipação de recebíveis (receita financeira — onde a margem real pode estar, seguindo o modelo Jota/Anota AI), rede de indicação entre profissionais. **Não construir:** prontuário eletrônico (regulatório pesado, mercado ocupado), marketing/captação de pacientes (vira marketplace, outro negócio), estoque/pedidos (irrelevante no nicho), app próprio para o paciente final.

## 20. Arquitetura conceitual (avaliação)

Camadas propostas no briefing avaliadas contra a evidência de custos (dossiê 6):

- **Interface:** WhatsApp API oficial (Cloud API) — obrigatório; não-oficial (Z-API) é risco existencial de banimento. Custo favorável: mensagens dentro da janela de 24h iniciada pelo usuário são **gratuitas**; templates utility ~R$ 0,034. Áudio: transcrição a US$ 0,006/min — suportar áudio é barato e essencial (formato dominante do público). Painel web: mínimo, apenas para histórico/compliance.
- **Agente:** LLM com tool-use + confirmação por botões; memória = banco de dados estruturado (não "memória de LLM"); tratamento de exceção = fila humana. Custo por tarefa: US$ 0,01–0,10 com caching. **Restrição de design:** autonomia progressiva por classe de ação (ver seção 22); nunca texto livre em nome do profissional sem aprovação.
- **Aplicações:** agenda (Google Calendar no MVP; própria depois), cobrança (Asaas), fiscal (provedor API fase 2), CRM leve próprio. Não construir ERP.
- **Dados:** cadastro, eventos, transações, logs imutáveis de toda ação executada (trilha de auditoria é requisito de confiança e de defesa jurídica).
- **Governança:** mandato contratual expresso para agir em nome do cliente; confirmação humana para dinheiro/fiscal; DPA (LGPD) com cada cliente; minimização — o agente não lê nem armazena conteúdo clínico; endpoints de LLM com não-treinamento e retenção limitada.

## 21. Make or Buy

| Componente | Decisão | Critério |
|---|---|---|
| WhatsApp Business API | **Comprar** (Cloud API direto ou BSP com markup por msg — Gupshup/Twilio; evitar licença fixa por número em baixo volume) | Custo fixo por cliente é o assassino da margem |
| Banco de dados / autenticação | Construir sobre managed (Postgres/Supabase-like) | Commodity |
| CRM leve / agenda interna | **Construir** (é o core do workflow) | Diferenciação |
| Integração Google Calendar | **Integrar** (OAuth verificado) | Rápido, gratuito |
| Pagamentos/Pix/cobrança | **Integrar** (Asaas: R$ 1,99/transação, 30 grátis/mês, régua pronta) | Velocidade, regulação BACEN fica no parceiro |
| Emissão fiscal | **Adiar** (fase 2); então integrar (Focus NFe/eNotas, R$ 1–5/nota) | Valor baixo no MVP; complexidade alta |
| OCR / transcrição | Integrar (LLM multimodal + Whisper) | Commodity barata |
| LLM | Comprar (API; roteamento barato→caro por complexidade) | Nunca é diferencial; custo cai continuamente |
| Orquestração do agente / automações | **Construir** (fina, própria) | É onde mora a confiabilidade — o produto real |
| Observabilidade / logs / auditoria | Construir mínimo próprio | Requisito de confiança e compliance |
| Atendimento humano (exceções) | Interno no início (founders) | Aprendizado; vira playbook de automação |
| Painel administrativo | Construir mínimo; adiar tudo além de histórico/export | Não é onde o valor está |

## 22. Modelo operacional

**Decisão: IA com supervisão humana, autonomia progressiva por classe de ação** (modelo 2 do briefing, migrando seletivamente para o 1). Margem-alvo honesta: tech-enabled service (55–70%), não SaaS puro, enquanto houver revisão humana.

| Ação | Classe inicial | Classe madura |
|---|---|---|
| Lembrete/confirmação de sessão | Autônoma | Autônoma |
| Resposta a "confirmo/remarco" do paciente | Autônoma (botões) | Autônoma |
| Envio de cobrança pós-sessão | Confirmada (1 toque) | Autônoma (opt-in) |
| Follow-up de inadimplente | Confirmada | Autônoma com limite de tentativas |
| Aplicação de multa de cancelamento | Confirmada | Confirmada |
| Emissão de NFS-e/recibo | Confirmada | Autônoma com teto de valor |
| Remarcação proposta pelo agente | Confirmada | Confirmada |
| Mensagem em texto livre ao paciente | Supervisionada | Confirmada |
| Alteração de preço/política | Manual (só o cliente) | Manual |
| Pagamento/transferência em nome do cliente | **Fora de escopo** | Reavaliar (regulação ITP) |
| Exclusão de dados (LGPD) | Manual com trilha | Manual |

---

## 23–24. Modelo de negócio e precificação

**Modelo:** mensalidade fixa por plano vertical, **sem fidelidade e sem multa** (posicionamento direto contra a reclamação dominante da categoria no Reclame Aqui), com taxa de transação repassada (Asaas) e, na maturidade, receita financeira (antecipação/Pix Automático) como segunda linha. Rejeitados: cobrança por conversa (imprevisível para o cliente, âncora ruim), por resultado (difícil de atribuir e auditar), revenue share (rejeição em profissionais de saúde — associação com comissão de marketplace tipo Zenklub é negativa).

| Plano | Preço | Inclui | Custo variável estimado | Margem bruta estimada |
|---|---|---|---|---|
| **Entrada** | R$ 79/mês | Confirmação + cobrança + conciliação, até 40 sessões/mês | ~R$ 25 (LLM ~R$ 10, WhatsApp/BSP ~R$ 5, Asaas repassado, infra ~R$ 10) | ~68% (sem custo humano) |
| **Profissional** | R$ 129/mês | + NFS-e/recibo automático, política de cancelamento, 80 sessões | ~R$ 45 (+ fiscal R$ 15–20) | ~65% |
| **Premium** | R$ 199/mês | + lista de espera, relatórios avançados, prioridade humana | ~R$ 60 | ~70% |

Custos ocultos a vigiar (por cliente/mês): supervisão humana de exceções (R$ 100+ na fase concierge → precisa cair para < R$ 15 com automação para as margens acima valerem); suporte/onboarding (~R$ 150 one-off); erro operacional (provisão ~2% da receita).

## 25. Unit economics (três cenários)

Premissas explícitas: ARPU do mix = R$ 95; CAC via canais de nicho (conteúdo + parcerias + founder-led); churn inclui mortalidade do negócio do cliente; margem = (ARPU − custo variável − supervisão humana rateada)/ARPU. Benchmark sombrio a respeitar: retenção anual de apps de IA ~21% (Localogy 2026) e GRR de SaaS AI-native 27–40% (ChartMogul) — os cenários base/pessimista assumem que NÃO escapamos totalmente disso.

| Métrica | Pessimista | Base | Otimista |
|---|---|---|---|
| ARPU | R$ 79 | R$ 95 | R$ 120 |
| Custo variável + supervisão/cliente | R$ 55 | R$ 40 | R$ 28 |
| Margem bruta | 30% | 58% | 77% |
| CAC | R$ 500 | R$ 250 | R$ 120 |
| Churn mensal | 9% | 5% | 3% |
| Vida média (meses) | 11 | 20 | 33 |
| LTV (margem × vida) | R$ 264 | R$ 1.100 | R$ 3.050 |
| **LTV/CAC** | **0,5 ❌** | **4,4 ✓** | **25 ✓** |
| Payback CAC | nunca | ~4,5 meses | ~1,3 mês |

Leitura: o cenário pessimista é **letal e plausível** — é exatamente o cenário Bench/churn-de-IA. As duas variáveis que decidem o negócio são **churn mensal ≤5%** e **supervisão humana < R$ 15/cliente**. Ambas são testáveis no concierge antes de escrever software de verdade. O experimento de validação existe para medir essas duas variáveis, não para "ver se as pessoas gostam".

## 26. Go-to-market

- **Canal inicial:** founder-led + conteúdo de nicho no Instagram ("psi empreendedora" é uma comunidade densa e ativa) + parceria com contabilidades especializadas em psicólogos (ex.: Attualize) e cursos de precificação/gestão para psicólogos. CAC-alvo R$ 120–250.
- **Mensagem:** a proposta de valor principal (seção 17) + prova: "recupere 1 falta por mês e o serviço se paga 2×".
- **Oferta de entrada:** 30 dias, R$ 79, sem fidelidade, setup feito por nós em 24h.
- **Ciclo de venda:** individual, 1 conversa de WhatsApp + 1 call de 30 min; ativação = primeira confirmação automática enviada (D+1); retenção = resumo semanal com dinheiro recuperado explicitado em R$; expansão = fisio/nutrição pelo mesmo motor + indicação entre profissionais (supervisão/grupos de estudo são redes densas).
- **Posicionamento:** "assistente administrativa no WhatsApp para psicólogos" — deliberadamente NÃO "IA", NÃO "funcionário digital", NÃO "plataforma". Categoria-âncora: secretária (que custaria R$ 1.500+), não software (que custa R$ 50).

## 27. Riscos (probabilidade × impacto, com sinais e mitigação)

| Risco | P | I | Sinal de alerta | Mitigação |
|---|---|---|---|---|
| Disposição a pagar < R$ 79 | Alta | Crítico | Conversão de pré-venda <15% | Validar preço com dinheiro real antes de construir; subir ticket via ROI (falta evitada) |
| Churn ≥ 8%/mês (padrão IA + mortalidade MEI) | Alta | Crítico | Cancelamentos no mês 2–3; uso semanal caindo | Resumo semanal com R$ recuperado; nicho com renda estável; sem fidelidade (retenção por valor, não contrato) |
| Meta Business Agent absorve o caso de uso | Média | Alto | Meta lança agenda/cobrança nativa no Brasil | Fosso na camada BR: Pix+Asaas, política de cancelamento, NFS-e, LGPD-saúde; velocidade |
| Jota/Nubank descem para o workflow de agenda | Média | Alto | Lançamento de "agenda" por fintech conversacional | Profundidade vertical (política de cancelamento, recibo psi, ética CFP) que generalistas não priorizam |
| Supervisão humana não cai (vira BPO disfarçado) | Média | Crítico | >20% das tarefas precisando de humano após 3 meses | Medir taxa de intervenção no concierge; cortar funções não-automatizáveis do escopo (lição Bench) |
| Erro do agente em dinheiro/cobrança destrói confiança | Média | Alto | 1º incidente de cobrança errada | Confirmação humana em toda ação financeira; trilha de auditoria; resposta a incidente < 1h |
| Banimento/limite do número WhatsApp | Baixa (API oficial) | Crítico | Queda de quality rating | API oficial, opt-in documentado, número dedicado por cliente (blast radius 1) |
| Mudança de preço/política da Meta | Alta | Médio | Anúncios da Meta (histórico: 3 mudanças em 3 anos) | Agente majoritariamente reativo (janela 24h gratuita); margem folgada para absorver |
| LGPD/dados sensíveis (nicho saúde) | Média | Alto | Paciente enviando conteúdo clínico ao bot | Agente não lê conteúdo clínico; DPA; minimização; endpoints sem treinamento; resposta padrão que redireciona assuntos clínicos ao profissional |
| Responsabilidade por erro fiscal | Baixa no MVP (sem NF) | Médio | — | Mandato contratual + confirmação por nota + seguro E&O na escala |
| Ética/publicidade CFP (mensagens em nome do psicólogo) | Média | Médio | Questionamento de CRP | Mensagens transacionais em nome próprio do serviço; nada de captação de pacientes; revisão por assessoria familiarizada com Res. CFP 03/2007 |
| Fundador único operando concierge não escala | Alta | Médio | Fila de exceções > 2h de trabalho/dia | Limitar piloto a 10–15 clientes; automatizar a partir da frequência real |

## 28. Defensabilidade (horizonte 3 anos)

| Fonte | Força | Comentário |
|---|---|---|
| Workflows verticais (política de cancelamento, ética CFP, ciclo sessão→dinheiro) | **Moderada→Forte** | Único fosso real disponível no curto prazo; profundidade que Meta/fintechs não priorizam |
| Confiança + marca no nicho | Moderada, lenta | Em saúde, confiança composta; 1 erro público a destrói |
| Custos de troca (histórico de pagamentos, políticas, hábito do paciente de responder ao número) | Moderada | Cresce com o tempo de uso; o paciente final treinado a responder é switching cost real |
| Dados proprietários (padrões de no-show/inadimplência por segmento) | Fraca→Moderada | Só vale com escala; útil para pricing e risco |
| Parceria com contadores/associações de nicho | Moderada | Distribuição defensável se exclusiva |
| Integrações (Asaas, fiscal, agenda) | Fraca | Todas compráveis por qualquer um |
| Tecnologia de LLM | **Nula** | Commodity — por instrução do briefing e por evidência |
| Efeitos de rede | Fraca | Indicação entre profissionais é o único vetor plausível |

Veredito: defensabilidade global **fraca-a-moderada nos primeiros 18 meses** — a vantagem é velocidade + profundidade vertical + confiança acumulada, não barreira estrutural. É um negócio de execução, não de patente. Aceitável para bootstrapping/seed; frágil para tese de VC sem prova de expansão multi-vertical.

## 29. Plano de validação (3 fases) e 30. Roadmap 12 meses

**Fase 1 — Descoberta (mês 1–1,5; custo ~R$ 0, só tempo).** 20 entrevistas com psicólogos autônomos (recrutados via Instagram/indicação; roteiro: rotina de confirmação/cobrança, nº de faltas/mês, R$ perdidos, quem cobra hoje, reação a preço). 5 observações de rotina (shadowing do WhatsApp administrativo com consentimento). Teste de mensagem: landing + anúncio R$ 300 medindo CTR/conversão de lista de espera. **Gate de avanço:** ≥60% relatam a dor P0 espontaneamente; ≥30% aceitam pagar piloto; CPL < R$ 20. **Gate de parada:** <15% de interesse pago → pivotar nicho (fisio) ou encerrar.

**Fase 2 — Concierge MVP (mês 2–3,5; 10 clientes pagantes; custo < R$ 5 mil).** Número de WhatsApp da empresa + operação manual (founder) com Google Calendar + Asaas; automação só de lembretes. Medir: tarefas/cliente/semana, taxa de exceção (% que exigiu julgamento humano), faltas antes/depois, R$ recuperado, tempo de operação por cliente, NPS, renovação m2. **Gates:** renovação ≥70%; faltas −20%+; taxa de exceção <30%; tempo de operação <20 min/cliente/dia. **Parada:** churn m1 >40% ou operação >45 min/cliente/dia sem caminho claro de automação.

**Fase 3 — MVP automatizado (mês 4–8; 30–50 clientes).** Automatizar apenas os 3 fluxos mais frequentes medidos na fase 2. Gates: taxa de automação ≥70%; supervisão < R$ 15/cliente/mês; margem bruta ≥55%; churn ≤5%/mês; LTV/CAC ≥3 projetado.

**Mês 8–12:** NFS-e/recibo, 2º nicho (fisio), parcerias de distribuição, 100–150 clientes, decisão de captação vs. bootstrap com dados reais.

## 31. Métricas de validação (metas mínimas)

Entrevistas: 20 · Interessados pagantes: ≥10 · Conversão entrevista→pagamento: ≥30% (validação) / 15–30% (parcial) / <15% (reprovação) · Ativação (1ª confirmação em 48h): ≥90% · Uso: ≥4 ciclos sessão→dinheiro/cliente/semana · Redução de faltas: ≥20% · Redução de inadimplência: ≥30% do valor em atraso recuperado · Retenção m2: ≥70% · Taxa de automação (fase 3): ≥70% · Intervenção humana: ≤30% (fase 2) → ≤10% (fase 3) · Taxa de erro com impacto no cliente final: <1% das ações · Margem bruta: ≥55% · NPS: ≥50.

## 32. Testes de hipótese (16)

| # | Hipótese | Evidência necessária | Método | Critério |
|---|---|---|---|---|
| 1 | Psicólogos perdem ≥R$ 400/mês com faltas e atrasos | Auto-relato + dados de agenda | Entrevistas + shadowing | ≥60% confirmam |
| 2 | Cobrar constrange a ponto de adiar/evitar cobrança | Relato espontâneo | Entrevistas | ≥50% citam sem estímulo |
| 3 | Existe disposição a pagar R$ 79–99/mês | Compra real | Pré-venda paga | ≥30% dos entrevistados |
| 4 | Confirmação automática reduz faltas ≥20% | Antes/depois | Concierge 6 semanas | Medido em ≥7/10 clientes |
| 5 | Régua de cobrança recupera ≥30% dos atrasos | Baixas no Asaas | Concierge | Medido |
| 6 | Cliente delega cobrança a um agente com aprovação 1-toque | Uso real | Concierge | ≥80% aprovam em <2h |
| 7 | Cliente NÃO delega texto livre ao paciente | Recusa observada | Concierge | Confirmar para calibrar escopo |
| 8 | WhatsApp é suficiente; painel é dispensável no dia a dia | Uso sem painel | Concierge | <20% pedem painel |
| 9 | Áudio é formato relevante de entrada | % de comandos por áudio | Concierge | ≥30% dos comandos |
| 10 | Taxa de exceção cai com padronização | Log de exceções | Concierge→MVP | <30%→<10% |
| 11 | Operação automatizável a <R$ 15/cliente de supervisão | Tempo humano medido | Fase 3 | Medido |
| 12 | Churn mensal ≤5% no nicho | Coorte 3 meses | Fase 3 | Medido |
| 13 | Verticalização converte melhor que mensagem genérica | A/B de landing/anúncio | Fase 1 | Diferença ≥2× |
| 14 | Recibo/NFS-e automático é gatilho de upgrade | % que paga plano Profissional | Fase 3 | ≥25% upgrade |
| 15 | Paciente final responde bem ao número do serviço (não estranha) | Taxa de resposta a confirmações | Concierge | ≥85% respondem |
| 16 | O motor se transfere para fisioterapeutas sem reescrita | Piloto 5 fisios | Mês 8+ | ≥80% dos fluxos reusados |

## Análises estratégicas complementares

**Cinco Forças de Porter (mercado de "agente administrativo para solopreneurs BR"):** Rivalidade: ALTA (dezenas de micro-SaaS, recepcionistas de IA, fintechs conversacionais). Novos entrantes: ALTA (barreira técnica desabou; infra de agentes é commodity). Substitutos: ALTA (grátis do governo, o próprio dono, secretária humana, Meta nativo). Poder dos compradores: ALTO (troca fácil, sensibilidade extrema a preço, zero lock-in aceitável). Poder dos fornecedores: ALTO (Meta muda preço/regra unilateralmente; LLM providers; Asaas/fiscal substituíveis = médio). **Estrutura setorial hostil — a atratividade precisa vir do nicho e da execução, não da indústria.** É a razão estrutural para verticalizar: no recorte "workflow administrativo de psicólogos", rivalidade e substituição caem para MÉDIA-BAIXA.

**SWOT (proposta verticalizada):** *Forças:* canal+pagamento universais (WhatsApp+Pix), fluxo P0 com ROI mensurável, custo variável baixo (R$ 25–45), timing de categoria. *Fraquezas:* defensabilidade estrutural fraca, dependência da Meta, marca zero num nicho que compra por confiança, fundador precisa operar concierge. *Oportunidades:* NFS-e API nacional, Pix Automático, incumbentes de nicho sem conversa (PsicoManager/iClinic), comunidade psi densa e alcançável, expansão fisio/nutrição. *Ameaças:* Meta Business Agent no Brasil, Jota/Nubank descendo para workflow, churn estrutural de IA (retenção anual ~21%), reajuste de API da Meta, ética CFP.

**Value Proposition Canvas (psicólogos):** *Jobs:* manter agenda cheia e recebida; preservar a relação terapêutica (não ser "o cobrador"); cumprir obrigações sem esforço. *Dores:* falta sem aviso (R$ 200+/evento), inadimplência acumulada, constrangimento de cobrar, admin noturno, medo de parecer não-profissional. *Ganhos:* previsibilidade de receita, profissionalismo percebido pelo paciente, tempo clínico líquido. *Analgésicos:* confirmação D-1 automática, cobrança pós-sessão pelo número do serviço (terceiro cobra, relação preservada), régua educada de inadimplência, resumo semanal em R$. *Criadores de ganho:* política de cancelamento aplicada sem negociação, recibo automático, lista de espera para horário vago.

**Business Model Canvas (resumo):** Segmento: psicólogos autônomos 10–30 sessões/semana. Proposta: agenda confirmada + pagamento na conta, no WhatsApp, sem cobrar ninguém. Canal: WhatsApp (produto), Instagram+parcerias contábeis (aquisição). Relacionamento: agente + humano em exceções, sem fidelidade. Receita: assinatura R$ 79–199 + futura receita financeira. Recursos-chave: orquestração confiável, playbook do nicho, trilha de auditoria. Atividades-chave: operar/automatizar ciclo sessão→dinheiro, compliance. Parcerias: Asaas, BSP WhatsApp, provedor fiscal, contabilidades de nicho. Custos: LLM/mensageria/infra (variável baixo), supervisão humana (o custo a matar), CAC.

**Pre-mortem ("fracassou após 2 anos — por quê?"):** 1º Churn: clientes adoraram no mês 1, cancelaram no mês 4 — o resumo semanal parou de mostrar dinheiro novo recuperado e a assinatura virou custo percebido (padrão AI churn wave). 2º Concierge que nunca virou software: exceções mantiveram 40 min/dia/cliente de trabalho humano; margem de agência com preço de SaaS (Bench em miniatura). 3º Meta lançou agendamento+cobrança nativos no WhatsApp Brasil e a camada de entrada virou grátis antes de construirmos o fosso fiscal-financeiro. 4º Um incidente de cobrança errada viralizou num grupo de psicólogas e a confiança — único ativo — evaporou. 5º Escopo inflou para "back office completo" atendendo pedidos individuais e o produto virou consultoria não escalável. 6º CAC real (R$ 600+) nunca fechou com ticket de R$ 89 — o nicho era alcançável mas não convertia sem prova social que não tínhamos. As mitigação de 1, 2 e 6 são exatamente o que o experimento de validação mede; 3–5 são disciplina de escopo.

---

## Score final de viabilidade

Notas 0–10, com pesos (soma 100). Direção: nota alta = favorável ao negócio.

| Dimensão | Peso | Nota | Justificativa (evidência) |
|---|---|---|---|
| Intensidade da dor | 10 | 7,0 | 21h/semana de admin, no-show 20–30%, "cobrar constrange" documentado; mas a dor é tolerada há décadas com soluções gratuitas — intensa, não desesperada |
| Frequência de uso | 8 | 8,5 | No nicho: 10–30 ciclos sessão→dinheiro/semana por cliente; contato diário natural |
| Tamanho de mercado | 7 | 6,5 | 437 mil psicólogos + ~1 mi no SAM saúde; TAM amplo existe mas colapsa sob o filtro de WTP; SOM 3 anos ≈ R$ 3–5 mi ARR — nicho, não oceano |
| Disposição a pagar | 10 | 4,5 | Elo mais fraco: faixa comprovada R$ 40–150/mês; 40% dos MEIs nem pagam DAS; nenhuma evidência direta de WTP para ESTE produto — só âncoras vizinhas |
| Facilidade de aquisição | 7 | 6,0 | Comunidade psi densa e alcançável (Instagram, CRPs, contabilidades de nicho); mas venda 1-a-1 de ticket baixo é cara — CAC é hipótese, não fato |
| Retenção potencial | 8 | 5,0 | Contra: retenção anual de apps IA ~21%, GRR AI-native 27–40%, mortalidade MEI. A favor: dor semanal recorrente e switching cost do paciente treinado. Incerto |
| Margem bruta | 7 | 6,0 | Variável baixo (R$ 25–45) permite 58–70%; mas supervisão humana pode derrubar para 30% (cenário Bench) — depende da taxa de exceção |
| Escalabilidade | 6 | 6,0 | Motor replicável para fisio/nutrição; mas cada vertical exige playbook próprio e o concierge não escala sem automação comprovada |
| Complexidade técnica | 5 | 6,5 | Stack toda disponível como API (WhatsApp, Asaas, Calendar, LLM, NFS-e); a dificuldade real é confiabilidade do agente, não construção |
| Complexidade operacional | 5 | 5,0 | Exceções, onboarding assistido, suporte a público não técnico; risco de virar BPO disfarçado |
| Risco regulatório | 5 | 5,5 | MVP sem NF e sem conteúdo clínico é leve (LGPD administrável, Res. ANPD 2/2022); cresce ao adicionar fiscal e dados de saúde — administrável com desenho |
| Diferenciação | 6 | 5,5 | O pacote (ciclo completo no WhatsApp do profissional) é genuinamente vago no mercado; mas cada peça isolada existe e é copiável |
| Defensabilidade | 6 | 4,0 | Fraca-a-moderada; sem barreira estrutural nos primeiros 18 meses; workflow vertical + confiança são o único fosso e demoram |
| Timing de mercado | 5 | 8,0 | Pix Automático + NFS-e API + custo de LLM caindo + categoria quente; janela real, mas fechando (Meta jun/2026) |
| Adequação ao WhatsApp | 5 | 9,0 | O melhor fit do mundo: 82% dos MEIs vendem lá, 99% dos smartphones, custo zero em conversa reativa |
| Potencial de verticalização | 5 | 8,0 | Saúde/bem-estar tem 4+ verticais adjacentes com o mesmo motor e o mesmo compliance |

**Nota ponderada final: 6,2/10** (Σ peso×nota / Σ pesos). Faixa 5,0–6,4 do briefing = "oportunidade incerta"; a 0,3 da faixa "executável com ajustes". Interpretação honesta: **na forma horizontal original, a nota seria ~4,5 (pouco atrativa — WTP, retenção e defensabilidade afundam); na forma verticalizada com escopo reduzido, fica no teto da faixa incerta, o que significa: não construir plataforma — comprar informação.** As duas variáveis que mudariam a nota para ≥7 (WTP real ≥30% de conversão paga; churn ≤5%) custam < R$ 5 mil e 3 meses para medir. É exatamente o que a decisão recomenda fazer.

## Decisão estratégica (obrigatória)

**VERTICALIZAR** — não avançar como concebido; não abandonar. Concretamente: abandonar o conceito horizontal de "agente administrativo completo para solopreneurs em geral" (reprovado por WTP, concorrência assimétrica e confiabilidade técnica) e executar a versão estreita: **agente do ciclo sessão→dinheiro para psicólogos autônomos, via WhatsApp, com autonomia progressiva**, condicionado aos gates do plano de validação. A construção de software fica **proibida** até o gate da Fase 2 (concierge) ser batido.

## Recomendação final — respostas diretas

1. **A ideia é boa?** Na forma proposta (horizontal, "faz-tudo"), não — é uma tese de 2024 que a evidência de 2026 (churn de IA, Bench, Meta nativo, WTP do MEI) já puniu. Na forma verticalizada, é uma oportunidade real de nicho, testável por quase nada.
2. **O problema é forte?** A dor agregada (admin, no-show, cobrança) é real e medida. A dor *pela qual se paga* é estreita: agenda que fura e dinheiro que não entra. Forte no nicho; difusa no horizontal.
3. **Existe mercado?** Sim, mas pequeno sob filtro de WTP: SAM saúde-autônomos ≈ R$ 200 mi/ano; SOM 3 anos ≈ R$ 3–5 mi ARR no beachhead. Mercado de empresa saudável, não de blitzscaling.
4. **Já existem empresas fazendo algo semelhante?** Sim: Jota/Magie (dinheiro por WhatsApp, muito capitalizadas), recepcionistas de IA verticais (Cloudia etc.), Meu Assessor (proposta idêntica, execução fraca), Meta Business Agent (grátis, global). Ninguém faz o ciclo completo sessão→dinheiro no WhatsApp do profissional.
5. **Onde está a lacuna?** Na orquestração vertical: confirmação com política de cancelamento + cobrança pós-sessão + conciliação + follow-up + recibo, no contexto e no tom de um nicho específico. E na camada Brasil (Pix, NFS-e, LGPD-saúde) que Meta e clones internacionais não cobrem.
6. **Melhor nicho para começar?** Psicólogos autônomos. (2ª: fisioterapeutas; evitar: confeiteiras.)
7. **Primeira tarefa a resolver?** Confirmação de sessão D-1 com botões + cobrança Pix pós-sessão com conciliação — o ciclo sessão→dinheiro.
8. **Qual deve ser o MVP?** Concierge: número de WhatsApp operado manualmente sobre Google Calendar + Asaas para 10 clientes pagantes, 6 semanas; automatizar depois só o que a frequência medida justificar.
9. **Quanto o cliente provavelmente pagaria?** R$ 79–99/mês na entrada (âncoras: Dietbox R$ 59,90, Simples Dental R$ 99, contador MEI R$ 50–150), com teto de ~R$ 199 para plano completo. Acima disso, só com ROI provado em R$.
10. **Principal risco?** Churn/retenção (padrão de apps de IA + mortalidade do cliente) combinado com WTP não comprovada — o cenário pessimista de unit economics (LTV/CAC 0,5) é plausível.
11. **Principal vantagem possível?** Ser dono do workflow administrativo de um nicho de confiança antes dos generalistas, com o paciente final treinado a responder ao número do serviço (switching cost real) e compliance de saúde como barreira contra genéricos.
12. **Deve-se construir agora?** Software, não. Experimento comercial, sim — imediatamente.
13. **Próximo experimento?** 20 entrevistas + pré-venda paga do concierge (10 vagas, R$ 79–99/mês) em até 6 semanas; gates definidos nas seções 29/31.
14. **Qual evidência mudaria a recomendação?** Para melhor: conversão paga ≥30% + renovação m2 ≥70% + taxa de exceção <30% → construir o MVP automatizado e considerar captação. Para pior: conversão <15%, ou churn m1 >40%, ou Meta lançando cobrança Pix + agenda nativas no Brasil antes da Fase 3 → pivotar (fisio/beleza via parceiros) ou encerrar sem construir nada.

---

*Evidência bruta, fontes e URLs: `pesquisa/dossies/01` (Brasil oficial), `02` (concorrentes BR), `03` (internacional), `04` (evidências de usuários), `05` (segmentos), `06` (custos/infra/regulação). Fatos citados sem fonte inline neste relatório têm a fonte no dossiê correspondente. Limitações declaradas: sem pesquisa primária própria (entrevistas) nesta etapa; alguns portais (IBGE, Sebrae, Reddit, Google Play) bloquearam acesso direto — dados obtidos via imprensa/snippets; números de no-show provêm majoritariamente de fornecedores de software (viés declarado); projeções de mercado de consultorias tratadas com desconto.*

---
name: profit-automacao-alarmes-e-robos
description: Automação no Profit — Gerenciador de Alarmes (8 tipos), Central de Alertas, Automação de Estratégias (planos, limites de exposição, conta simulada x conta real), Replay de Mercado e séries históricas, backtest e otimização de parâmetros, Editores de Estratégias, robôs prontos (Máximas e Mínimas, Termômetro de Mercado, Euroinvest, FGZ, 2MV Force AT), Profit AI Code Builder, Copilot, Inside Track, Motion Tracker e Loja de Estratégias. Use quando a pergunta for como automatizar, quanto custa, qual o limite de contratos, como testar ou por que a automação não abriu ordem.
---

# Automação, alarmes e robôs no Profit

Base: seções "Automação de Estratégias" (21), "Editor de Estratégias" (22), "Replay de Mercado", "Robôs" e "Profit AI Code Builder" da Central de Ajuda Nelogica, 12/11/2026. A sintaxe da linguagem fica nas skills `ntsl-*`; aqui é a parte da plataforma.

## Alarmes e alertas

- **Gerenciador de Alarmes** (menu Ferramentas) tem oito tipos: Ativos, Inversão, Estratégias, Horário, Meta, Notícia, Correlação e Rompimento. Funciona sem o gráfico aberto e aceita alarme preso a um estudo (ex.: rompimento de linha de tendência).
- **Central de Alertas** (menu Exibir) é o histórico único: rejeições de ordens, alarmes de ativos, ordens executadas, instabilidade de conexão e outros.

## Automação de Estratégias — a regra que quase todo mundo erra

Quem tem **Profit Pro ou Profit Ultra** cria e opera estratégias automatizadas **de graça na Conta de Simulação**. Para operar em **conta real**, é preciso contratar o **módulo opcional de Automação de Estratégias** na Profit Store (planos mensal/anual, e o plano **Plus** eleva o limite de exposição de 5 para 50 minicontratos). Ou seja: "já paguei o Pro, por que não envia ordem automática?" — porque falta o módulo e o limite de exposição.

Detalhes que decidem se a automação roda: conta habilitada, estratégia publicada e instanciada no ativo/período correto, limite de exposição do plano, permissão de operação na conta (DMA/mesa), conexão estável e "o que acontece se eu fechar o Profit" (há artigo próprio — a resposta depende do tipo de publicação).

## Teste e validação

- **Replay de Mercado**: reproduz o pregão para testar manualmente; aceita Séries Históricas (WINFUT, INDFUT, WDOFUT, DOLFUT), que são a união dos vencimentos — é assim que se testa contrato já vencido.
- **Backtest**: na própria estratégia, com custos, resultados e otimização de parâmetros (recurso do Ultra). As funções de resultado de backtest estão na skill `ntsl-funcoes-backtesting`.

## Criação

- **Editor de Estratégias**: NTSL, com as ferramentas de depuração, exportação/importação de estratégias e publicação.
- **Profit AI Code Builder**: descreve a estratégia em português e a IA gera o código; é módulo pago, com planos por número de requisições (o Code Builder ONE tem 20 requisições mensais).
- **Copilot**: exclusivo do Profit Ultra e dos planos de Automação Premium ou superiores; cria gatilhos, confirma entrada de automação e traz notícias do portfólio (menu Ultra).
- **Loja de Estratégias**: compra e venda de estratégias entre usuários, com manual de boas práticas próprio.
- **Robôs prontos**: Máximas e Mínimas, Termômetro de Mercado, Euroinvest, FGZ, 2MV Force AT — cada um com configuração documentada.

## Pegadinhas

- "Alarme não dispara" quase sempre é ativo sem negócio no período, condição mal configurada ou alerta silenciado — a Central de Alertas mostra.
- Hora do servidor: alarme de horário segue o fuso da plataforma, não o do computador.
- Backtest com contrato contínuo (série histórica) tem descontinuidade no vencimento: resultado em WINFUT não é o resultado do contrato específico.

## Arquivos de referência

- `refs/01-editor-de-estrategias.md` — profit-automacao-alarmes-e-robos — Editor de Estratégias (21 verbetes)
- `refs/02-automacao-de-estrategias.md` — profit-automacao-alarmes-e-robos — Automação de Estratégias (19 verbetes)
- `refs/03-loja-de-estrategias.md` — profit-automacao-alarmes-e-robos — Loja de Estratégias (11 verbetes)
- `refs/04-duvidas-comuns.md` — profit-automacao-alarmes-e-robos — Dúvidas Comuns (5 verbetes)
- `refs/05-replay-de-mercado.md` — profit-automacao-alarmes-e-robos — Replay de Mercado (4 verbetes)
- `refs/06-robos.md` — profit-automacao-alarmes-e-robos — Robôs (4 verbetes)
- `refs/07-robo-euroinvest.md` — profit-automacao-alarmes-e-robos — Robô Euroinvest (3 verbetes)
- `refs/08-profit-ai-code-builder.md` — profit-automacao-alarmes-e-robos — Profit AI Code Builder (2 verbetes)
- `refs/09-robo-2mv-force-at.md` — profit-automacao-alarmes-e-robos — Robô 2MV Force AT (2 verbetes)
- `refs/10-robo-maximas-e-minimas.md` — profit-automacao-alarmes-e-robos — Robô Máximas e Mínimas (2 verbetes)
- `refs/11-robo-termometro-de-mercado.md` — profit-automacao-alarmes-e-robos — Robô Termômetro de Mercado (2 verbetes)
- `refs/12-robos-fgz.md` — profit-automacao-alarmes-e-robos — Robôs FGZ (2 verbetes)

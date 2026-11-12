# Skills Nelogica / NTSL / Profit Pro

Skills da Nelodoc (agente especialista em documentação Nelogica) para agentes que escrevem e revisam algoritmos de trade em NTSL no Profit Pro.

Fontes: Manual NTSL — Módulo Estratégias, versão 4.7, de 14/10/2026 (documento oficial da Nelogica, 575 páginas) e a Central de Ajuda Nelogica (ajuda.nelogica.com.br, 780 artigos lidos pela API pública em 12/11/2026).

Cada skill é uma pasta com `SKILL.md` (regras e índice) e `refs/` (conteúdo extraído do manual, com referência de página).

## Skills

- **ntsl-automacao-e-estrategias** — Como se cria, testa e coloca no ar uma estratégia no Profit Pro — backtest OHLC e tick a tick, backtest em gráfico atemporal, Automação de Estratégias (opções de entrada e saída, horários, risco, segurança, acompanhamento, raio-X, regras de execução), Central de Estratégias, Screening com Select, Block Builder e ConsoleLog. Use quando a pergunta for "como automatizo", "por que a automação não entr
  - refs: 01-automacao.md, 02-estrategias-e-screening.md
- **ntsl-backtesting-e-ordens** — Funções de backtesting e de ordem do NTSL — envio e cancelamento de ordens a mercado, limitada e stop, covers, reversão, posição, preço médio e resultado do backtest, mais as regras de execução que fazem uma ordem desaparecer. Use ao escrever a lógica de entrada/saída de uma estratégia, ao depurar por que uma ordem não foi enviada, ou ao ler resultados do backtest.
  - refs: 01-conceitos-de-backtest.md, 02-ordens-posicao-e-resultados.md
- **ntsl-calendario-e-tempo** — Funções de data e hora do NTSL — pregão, dia útil, feriado, vencimento, semana/mês/ano, primeira e última barra do dia, OHLC de períodos maiores (OpenD/HighW/CloseM), minutos e segundos. Use quando a estratégia ou indicador depender de tempo, data, dia da semana, vencimento de opção ou de agregar por dia/semana/mês/ano.
  - refs: 01-calendario.md
- **ntsl-fundamentos** — Fundamentos da linguagem NTSL do Profit — as três áreas do código, fluxo de execução barra a barra, tipos de dados, séries e séries históricas, arrays, correlação de múltiplos ativos, controle de fluxo, operadores, funções e procedimentos do usuário, Initialization e as armadilhas de compilação. Use ao escrever, revisar ou explicar qualquer código NTSL.
  - refs: 01-estrutura-e-fluxo.md, 02-variaveis-tipos-series.md, 03-controle-de-fluxo-e-operadores.md, 04-funcoes-e-procedimentos.md, 05-anexos-erros-comuns.md
- **ntsl-graficos-e-candlestick** — Funções gráficas do NTSL (Plot até Plot99, PlotN, PaintBar, linhas horizontais, cores, ConsoleLog) e as funções de padrão de candlestick (engolfo, martelo, doji, harami, estrela). Use quando o pedido for desenhar algo no gráfico do Profit a partir de uma estratégia, colorir candles, plotar indicador próprio ou detectar padrão de vela em código.
  - refs: 01-funcoes-graficas.md, 02-candlestick.md, 03-exemplos.md
- **ntsl-indicadores** — Catálogo completo dos 159 indicadores do Profit que existem como funções NTSL, com assinatura, parâmetros e o que cada um mede. Use quando alguém perguntar qual indicador usar para uma necessidade, qual é o nome exato da função do indicador no Editor de Estratégias, ou ao montar o cálculo de um indicador dentro de uma estratégia NTSL.
  - refs: 01-a-f.md, 02-g-m.md, 03-n-s.md, 04-t-z.md
- **ntsl-livro-e-opcoes** — Funções de livro de ofertas (BidPrice, AskPrice, BidSize, AskSize, BookSpread, BuyOfferCount, TotalBuyQtd/TotalSellQtd, Lote, MinPriceIncrement, GetAsset, IsBMF) e funções gregas/opções (Delta, Gamma, Theta, Vega, Rho, Strike). Use quando a estratégia precisar do livro, do ticker, do lote, da BMF, da volatilidade implícita ou de precificar opção.
  - refs: 01-livro.md, 02-opcoes.md
- **ntsl-matematica-e-series** — Funções matemáticas e utilitárias do NTSL — ABS, Round, Power, Sqrt, Max/Min, Random, FastK/FastD/SlowK, ExtremePriceRatio, Volatility, PercentR, comparação segura de Float (CompareFloat), conversão de número/texto (FloatToString, BoolToString) e funções de texto (SubString, StringContains, StringPos). Use em cálculo dentro de estratégia, arredondamento, comparação de float, montagem de texto e op
  - refs: 01-matematicas.md, 02-funcoes-de-usuario.md, 03-utils-e-string.md
- **profit-pro-e-produtos** — A plataforma Profit Pro e o ecossistema Nelogica fora da linguagem — versões (Profit Ultra, Pro, Plus, One, Training), módulos opcionais, como a interpolação de indicador funciona, primeiro uso, e o índice completo dos 780 artigos da Central de Ajuda para achar o artigo certo por assunto. Use quando a pergunta for sobre a plataforma, uma tela, um módulo, uma versão/licença, ou quando precisar loca
  - refs: 01-plataformas-e-produtos.md, 02-indicadores-da-plataforma.md, 03-indice-central-de-ajuda.md

Total: 9 skills, 25 arquivos de referência, 486 seções do manual e 780 artigos da Central de Ajuda indexados.

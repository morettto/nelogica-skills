# 01 Conceitos De Backtest

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Backtesting

### Backtesting
*Manual NTSL v4.7 (14/10/2026) — p. 38*

Backtesting

A funcionalidade de backtesting permite avaliar estratégias desenvolvidas em NTSL por meio da execução sobre dados históricos, possibilitando a análise de desempenho antes da utilização em automação.

Após a criação de uma estratégia, ela pode ser adicionada ao gráfico por meio da opção "Inserir Estratégia de
Execução", disponível no menu acionado com o botão direito do mouse.

O mecanismo de backtest reproduz a lógica utilizada na automação. A simulação das ordens é processada ao final do fluxo de execução de cada candle. Quando ocorre aumento de posição nesse momento, o código é automaticamente reprocessado para possibilitar o disparo das ordens de cobertura da operação (ordens ToCover).

Esse comportamento pode ser acompanhado pelo usuário por meio do modo debug, permitindo visualizar as etapas de processamento e a sequência de geração das ordens.

10.1 Modo de Execução do Backtest: OHLC e Tick a Tick

O Profit Ultra permite dois modos de execução para o backtest: OHLC e Tick a Tick. Cada modo utiliza diferentes níveis de detalhamento do histórico de preços para simular a execução das ordens.

No modo OHLC (Open, High, Low, Close), são considerados apenas os preços de abertura, máxima, mínima e fechamento de cada candle. As ordens do tipo Limit e Stop são avaliadas com base nesses quatro níveis, sem considerar o fluxo de preços ocorrido dentro do candle. Por esse motivo, a simulação apresenta menor detalhamento em relação ao comportamento real do mercado intraday.

No modo Tick a Tick, é utilizado o fluxo completo de negócios dentro de cada candle, permitindo reproduzir com maior precisão o momento exato em que uma ordem seria executada. Nesse modo, saídas Limit e Stop podem ser simuladas nos níveis efetivamente negociados durante o pregão.

Em simulações OHLC, o backtest pode indicar que um stop ou um objetivo não foi atingido ao avaliar apenas os preços do candle, enquanto no modo Tick a Tick a mesma ordem poderia ser executada corretamente ao considerar os preços intraday. Isso proporciona maior aderência à lógica operacional utilizada na automação.

Devido à maior granularidade dos dados, o modo Tick a Tick possui menor disponibilidade de histórico quando comparado ao modo OHLC, podendo limitar simulações de períodos mais longos.

A imagem a seguir ilustra um candle de alta em que a linha verde representa o movimento real dos preços e o ponto vermelho indica o nível de envio de uma ordem. No modo OHLC, a execução ocorreria apenas após o preço atingir os níveis de mínima (LOW) ou fechamento (CLOSE). No modo Tick a Tick, a ordem pode ser executada assim que o preço alcança o nível programado, mesmo antes da conclusão do candle, possibilitando, por exemplo, o disparo de um stop antes do fechamento.

Essas diferenças tornam-se mais relevantes em gráficos atemporais, conforme descrito na seção seguinte.

10.2 Backtest em Gráficos Atemporais

Gráficos atemporais, como Kagi, Renko e Ponto & Figura, não possuem candles baseados em tempo, mas sim em critérios de variação de preço. Por essa característica, o momento lógico de formação do candle não coincide necessariamente com o momento cronológico do mercado.

Nesses gráficos, o preço de abertura de um novo candle corresponde ao nível onde a reversão se iniciou, e não ao preço vigente no instante em que o candle é efetivamente concluído e exibido. Assim, o candle pode representar um evento iniciado em um preço histórico, enquanto o mercado já se encontra em outro patamar.

No modo de backtest OHLC, as ordens são simuladas com base no preço de abertura do candle. Como esse valor pode estar defasado em relação ao preço real de negociação, a execução simulada pode ocorrer em níveis que já não estavam mais disponíveis, produzindo diferenças relevantes quando comparadas à automação.

Na automação em tempo real, as ordens são enviadas utilizando o preço atual de mercado, respeitando as condições reais de liquidez e negociação. Dessa forma, o preço de execução tende a ser diferente daquele utilizado na simulação por candles.

Observação: essa diferença de comportamento é inerente ao modelo de construção dos gráficos atemporais e ao método de backtest baseado em candles, não se tratando de falha da plataforma.

Boas práticas recomendadas:

• utilizar preferencialmente o modo Tick a Tick, que representa com maior fidelidade o fluxo real de preços;

• validar a estratégia no modo Replay antes da automação;

• considerar a aplicação de slippage e custos operacionais nas simulações;

• evitar lógicas que dependam exclusivamente da execução no preço de abertura de candles atemporais.

### Modo de Execução do Backtest: OHLC e Tick a Tick
*Manual NTSL v4.7 (14/10/2026) — p. 38*

10 Backtesting

A funcionalidade de backtesting permite avaliar estratégias desenvolvidas em NTSL por meio da execução sobre dados históricos, possibilitando a análise de desempenho antes da utilização em automação.

Após a criação de uma estratégia, ela pode ser adicionada ao gráfico por meio da opção "Inserir Estratégia de
Execução", disponível no menu acionado com o botão direito do mouse.

O mecanismo de backtest reproduz a lógica utilizada na automação. A simulação das ordens é processada ao final do fluxo de execução de cada candle. Quando ocorre aumento de posição nesse momento, o código é automaticamente reprocessado para possibilitar o disparo das ordens de cobertura da operação (ordens ToCover).

Esse comportamento pode ser acompanhado pelo usuário por meio do modo debug, permitindo visualizar as etapas de processamento e a sequência de geração das ordens.

10.1 Modo de Execução do Backtest: OHLC e Tick a Tick

O Profit Ultra permite dois modos de execução para o backtest: OHLC e Tick a Tick. Cada modo utiliza diferentes níveis de detalhamento do histórico de preços para simular a execução das ordens.

No modo OHLC (Open, High, Low, Close), são considerados apenas os preços de abertura, máxima, mínima e fechamento de cada candle. As ordens do tipo Limit e Stop são avaliadas com base nesses quatro níveis, sem considerar o fluxo de preços ocorrido dentro do candle. Por esse motivo, a simulação apresenta menor detalhamento em relação ao comportamento real do mercado intraday.

No modo Tick a Tick, é utilizado o fluxo completo de negócios dentro de cada candle, permitindo reproduzir com maior precisão o momento exato em que uma ordem seria executada. Nesse modo, saídas Limit e Stop podem ser simuladas nos níveis efetivamente negociados durante o pregão.

Em simulações OHLC, o backtest pode indicar que um stop ou um objetivo não foi atingido ao avaliar apenas os preços do candle, enquanto no modo Tick a Tick a mesma ordem poderia ser executada corretamente ao considerar os preços intraday. Isso proporciona maior aderência à lógica operacional utilizada na automação.

Devido à maior granularidade dos dados, o modo Tick a Tick possui menor disponibilidade de histórico quando comparado ao modo OHLC, podendo limitar simulações de períodos mais longos.

A imagem a seguir ilustra um candle de alta em que a linha verde representa o movimento real dos preços e o ponto vermelho indica o nível de envio de uma ordem. No modo OHLC, a execução ocorreria apenas após o preço atingir os níveis de mínima (LOW) ou fechamento (CLOSE). No modo Tick a Tick, a ordem pode ser executada assim que o preço alcança o nível programado, mesmo antes da conclusão do candle, possibilitando, por exemplo, o disparo de um stop antes do fechamento.

Essas diferenças tornam-se mais relevantes em gráficos atemporais, conforme descrito na seção seguinte.

### Backtest em Gráficos Atemporais
*Manual NTSL v4.7 (14/10/2026) — p. 39*

Gráficos atemporais, como Kagi, Renko e Ponto & Figura, não possuem candles baseados em tempo, mas sim em critérios de variação de preço. Por essa característica, o momento lógico de formação do candle não coincide necessariamente com o momento cronológico do mercado.

Nesses gráficos, o preço de abertura de um novo candle corresponde ao nível onde a reversão se iniciou, e não ao preço vigente no instante em que o candle é efetivamente concluído e exibido. Assim, o candle pode representar um evento iniciado em um preço histórico, enquanto o mercado já se encontra em outro patamar.

No modo de backtest OHLC, as ordens são simuladas com base no preço de abertura do candle. Como esse valor pode estar defasado em relação ao preço real de negociação, a execução simulada pode ocorrer em níveis que já não estavam mais disponíveis, produzindo diferenças relevantes quando comparadas à automação.

Na automação em tempo real, as ordens são enviadas utilizando o preço atual de mercado, respeitando as condições reais de liquidez e negociação. Dessa forma, o preço de execução tende a ser diferente daquele utilizado na simulação por candles.

Observação: essa diferença de comportamento é inerente ao modelo de construção dos gráficos atemporais e ao método de backtest baseado em candles, não se tratando de falha da plataforma.

Boas práticas recomendadas:

• utilizar preferencialmente o modo Tick a Tick, que representa com maior fidelidade o fluxo real de preços;

• validar a estratégia no modo Replay antes da automação;

• considerar a aplicação de slippage e custos operacionais nas simulações;

• evitar lógicas que dependam exclusivamente da execução no preço de abertura de candles atemporais.

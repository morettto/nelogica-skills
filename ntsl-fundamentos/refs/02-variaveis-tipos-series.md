# 02 Variaveis Tipos Series

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Variáveis, tipos de dados e constantes

### Variáveis, tipos de dados e constantes
*Manual NTSL v4.7 (14/10/2026) — p. 15*

Variáveis, tipos de dados e constantes

As variáveis são utilizadas para armazenar dados, conforme seu tipo específico.

4.1 Tipos de dados

• Float ou Real - Representa números de ponto flutuante.

• Integer ou Inteiro - Representa números inteiros.

• Boolean ou Booleano - Representação lógica: True ou Verdadeiro e False ou Falso

• Serie - Representa uma série de dados.

A NTSL suporta a conversão implícita de valores Float a Inteiros, isto é, atribuir um valor Float diretamente a um valor
Integer. O valor inteiro será o valor do ponto flutuante, descartando as casas decimais. Por exemplo, se eu atribuir
2.99 ou 2.35 a um inteiro, o valor do inteiro será 2. Para outros comportamentos de arredondamento, a linguagem disponibiliza as funções Ceiling, Floor e Round. Para mais detalhes sobre essas funções, consulte esse mesmo manual na seção de funções.
As variáveis na linguagem oferecem uma flexibilidade muito maior do que na maioria dos sistemas de programação conhecidos.
Todas as variáveis são globais, e deve ser dada uma atenção especial quando utilizadas. Ao programar usando variáveis globais, deve ser levado em consideração o comportamento do processamento do fluxo de execução, a cada vez que o fluxo de execução é realizado as variáveis podem ter seu valor alterado com base no último valor que tinham.
Quando uma variável for acessada utilizando colchetes (exemplo: [x]), ela será considerada uma série de dados pelo compilador. Seu comportamento é diferente: séries iniciam cada candle com seu valor zerado. Também é possível navegar entre valores atuais e passados, mediante indexação.

4.2 Séries de dados

As séries de dados são utilizadas para obter dados específicos de cada Candle.
Séries:

• Abertura ou Open - Retorna o valor de abertura de cada candle.

• Fechamento ou Close - Retorna o dado de fechamento.

• Minima ou Low - Retorna o valor de mínima.

• Maxima ou High - Retorna o dado de máxima.

• Quantidade ou Quantity - Retorna o valor de contratos negociados de cada candle.

• Volume - Retorna o dado de volume financeiro de cada candle.

4.3 Arrays

Análogo ao tipo Serie, a estrutura de um Array permite o armazenamento de dados de um tipo específico, contudo, após sua criação, seu comprimento será fixo, o que permite uma alocação menor de memória.
O acesso aos elementos de um Array é efetuado mediante indexação.
Estrutura da declaração:

var

Variavel : Array[Tamanho] Of Tipo;

A fim de exemplificação, segue um exemplo de declaração de um Array estático de 10 elementos, o qual é preenchido com valores de 1 a 10 (primeira estrutura de repetição), e efetuado o somatório dos valores:

var

i, sum : Integer;
lista : array[1..10] of Integer;

begin

for i := 1 to 10 do lista[i] := i;

sum := 0;
for i := 1 to 10 do sum := sum + i;
Plot(sum);

end;

4.4 Correlação de múltiplos ativos

A função Asset permite acessar dados de outros ativos dentro da estratégia, possibilitando correlações, comparações entre períodos e aplicação de indicadores em múltiplos instrumentos. Essa funcionalidade amplia consideravelmente as possibilidades de análise e automação, permitindo o uso de séries de diferentes ativos, intervalos e tipos de gráfico.

Estrutura básica: A função Asset pode ser instanciada de formas diferentes, dependendo do contexto de uso
(const ou input) e da origem do ativo (ticker explícito ou ativo do gráfico).

Asset(Ticker : String, Bolsa : Const, Período : Período, Offset : Integer,

Fator : Integer);

**Parâmetros**

Ticker: String; Ticker do ativo.

Bolsa: Const; Bolsa na qual o ativo está listado.

Período: Período [Opcional]; Define o tipo de gráfico (ex: itMinute, itDaily).

Offset: Integer [Opcional]; Define o valor numérico do período.

Fator: Integer [Opcional]; Aplicável apenas para gráficos do tipo ponto figura.

Importante:

• Os parâmetros Período e Offset são opcionais apenas quando omitidos em conjunto.

• Não é permitido informar apenas um dos dois parâmetros.

• O uso de Período, Offset e Fator está disponível apenas para usuários das plataformas Ultra ou Automação

2.0.

Declaração como const

Quando declarada como constante, a função Asset cria uma série fixa durante toda a execução da estratégia, permitindo o uso de ativos distintos ou do mesmo ativo do gráfico principal.

const

A1 = Asset("WINFUT", feedBMF, itSecond, 10);

begin

Plot(A1.close);
Plot2(A1.open);

end;

Declaração como input

Também é possível declarar ativos como entradas da estratégia, permitindo alterar o ativo e seus parâmetros sem recompilar o código.

input

A1("DOLFUT", feedBMF, itSecond, 10);

begin

Plot(A1.ADX(9, 9));

end;

Uso de GetAsset e período personalizado

A função Asset pode ser instanciada utilizando GetAsset, que representa o ativo carregado no gráfico principal. Essa forma de uso permite acessar o mesmo ativo, porém utilizando um período ou intervalo diferente do gráfico principal.
Atenção: Ao utilizar o Asset com períodos divergentes (isto é, um período diferente do gráfico principal), os dados retornados podem não coincidir com os valores esperados para aquele período. Isso ocorre porque a função utiliza como referência o candle mais próximo do candle atual do ativo analisado. Por exemplo, ao acessar a abertura diária de um ativo a partir de um gráfico de 1 minuto ou Renko, o valor de open retornado pode divergir do valor real de abertura daquele período. Para garantir a precisão dos dados, é recomendável especificar explicitamente a série desejada na declaração do Asset, como em: Asset("INDFUT", feedBMF, itDaily).

const

A1 = Asset(GetAsset, itSecond, 10);

begin

Plot(A1.close);

end;

Regras de uso:

• GetAsset substitui simultaneamente os parâmetros Ticker e Bolsa.

• A variável que utiliza Asset com GetAsset deve obrigatoriamente ser declarada como const.

• Os parâmetros Período e Offset tornam-se obrigatórios.

• Quando o período informado for do tipo Ponto & Figura, o parâmetro Fator torna-se obrigatório.

• O parâmetro Fator é exclusivo para períodos do tipo Ponto & Figura e não deve ser utilizado com períodos

temporais ou outros períodos atemporais.

Uso de indicadores com Asset

_Indicadores podem agora ser utilizados diretamente como propriedades do Asset, permitindo aplicar estudos técnicos sobre diferentes ativos e períodos.

const

A1 = Asset("WINFUT", feedBMF, itSecond, 10);

begin

Plot(A1.ADX(9, 9));

end;

Indicadores compatíveis com Asset

Os seguintes indicadores podem ser utilizados como propriedades do Asset:

• AccuDistr

• AccuDistrW

• ADX

• AgressionVolBalance

• AgressionVolBuy

• AgressionVolSell

• AroonLin

• AroonOsc

• ForceIndex

• FrassonATR

• FullStochastic

• FuraChao

• FuraTeto

• HILOActivator

• HistVolatility

• IchimokuCloud

• ArmsEaseOfMov

• KeltnerCh

• AvgSeparation

• AvgTrueRange

• BalanceOfPower

• BollingerBandW

• BollingerBands

• CCI

• KVO

• MACD

• MFI

• MIMA

• MIMAROC

• Momentum

• ChaikinMoneyFlow

• MomentumStochastic

• ContadorDeCandle

• MoneyFlow

• DiPDiM

• DidiIndex

• DonchianCh

• EMA

• Envelope

• FastStochastic

• FastWMA

• MoneyFlowIndex

• OBV

• OBVAvg

• ParabolicSAR

• PhIbo

• Pivot

• PriceVolumeTrend

• PriorCote

• Ravi

• RenkoVTwo

• ROC

• RSI

• RSIStochastic

• SafeZoneDownTrend

• SafeZoneUpTrend

• Santo

• SMA

• SlowStochastic

• StopATR

• Tilson

• TopBottomDetector

• TRIX

• TRIXM

• VWAP

• VWAPDate

• VWAPMonthly

• VWAPWeekly

• VWMA

• Williams

Consultando o nome e feed do ativo

As funções GetAsset e GetFeed retornam respectivamente o ticker e a bolsa do ativo declarado.

const

WDO = Asset("WDOFUT", feedBMF);

begin

if (MaxBarsForward = 0) then

PlotText("Ticker: " + WDO.GetAsset +

" - Bolsa: " + WDO.GetFeed , clRed, 0, 7);

end;

Propriedades acessíveis via função Asset

A função Asset permite acessar e manipular um ativo diferente do gráfico principal e acessar suas informações e séries de preço e volume. As séries de preço e volume podem ser consultadas na seção 4.2 deste manual.

• GetFeed – Retorna o feed de dados do ativo.

• GetAsset – Retorna o próprio ativo.

• AskPrice – Preço do ask (preço de venda).

• AskSize – Tamanho do ask (quantidade disponível para venda).

• BidPrice – Preço do bid (preço de compra).

• BidSize – Tamanho do bid (quantidade disponível para compra).

• BookSpread – Diferença entre o melhor bid e o melhor ask.

• Lote – Tamanho do lote do ativo.

• MinPriceIncrement – Incremento mínimo de preço.

• Strike – Preço de exercício (para derivativos como opções).

Bolsas disponíveis

As bolsas disponíveis dependem do acesso do usuário. A relação completa das constantes de bolsa está na seção
4.7 deste manual, e os feeds liberados para a conta podem ser consultados na aba "Constantes" da plataforma.

Exemplo de correlação entre múltiplos ativos

Exemplo de estratégia que colore os candles conforme a relação entre WDO e WIN.

const

WDO = Asset("WDOFUT", feedBMF);
WIN = Asset("WINFUT", feedBMF);

input

Periodo(20);

var

wdoMedia : Float;
winMedia : Float;

begin

wdoMedia := MediaExp(Periodo , WDO.close);
winMedia := MediaExp(Periodo , WIN.close);

if (WDO.close > wdoMedia) and (WIN.close < winMedia) then

PaintBar(clLime)

else if (WDO.close < wdoMedia) and (WIN.close > winMedia) then

PaintBar(clAqua);

end;

Observações e limitações

• O parâmetro Fator é utilizado apenas para gráficos de ponto figura.

• Cada ativo pode ter seu próprio intervalo e período, independentes do ativo principal.

• O limite máximo é de 30 ativos por estratégia.

• Em gráficos atemporais, o fechamento dos candles auxiliares pode não coincidir com o do ativo principal, o que

pode causar divergências entre o backtest/replay e a automação em tempo real.

4.5 Acessando dados anteriores

O dado atual de uma variável pode ser descrito por Variavel[0]. O número entre colchetes indica quantos períodos anteriores devem ser acessados, sendo 0 sempre referente à barra corrente. Para ilustrar melhor, vamos a um exemplo:

sResult := Preco[1];

A linha de código acima está atribuindo o valor da variável Preco[1] para a variável sResult. Imagine que Preço corresponde a todos os valores de fechamento da série de dados de um certo ativo, como na tabela abaixo:

Data

05/10/2010

04/10/2010

01/10/2010

30/09/2010

29/09/2010

dd/mm/aaaa

Posição

Preco[0]

Preco[1]

Preco[2]

Preco[3]

Preco[4]

Preco[5]

Valor

12,43

12,40

11,39

12,51

12,38

xx,xx

Portanto, Preco[1] refere-se ao valor de ontem do preço de fechamento (sResult vale então 12,40 em nosso ex- emplo). Dessa forma, o número inteiro que especificarmos entre colchetes indica ao sistema quantos períodos no passado deve-se acessar a informação.

Uso de dados anteriores em funções de execução e do Livro

Embora o acesso a dados anteriores seja plenamente suportado para séries históricas de preços e indicadores, é importante observar que nem todos os contextos possuem histórico disponível.

No modo de backtest, o sistema dispõe de histórico completo de preços, posições e ordens, permitindo o uso de acessos posicionais nesses contextos. Já na automação em tempo real, essas informações existem apenas em seu estado atual, não havendo histórico armazenado para posições, ordens ou dados do Livro de Ofertas.

Em especial, o uso de acessos posicionais em funções de execução de estratégias ou em funções relacionadas ao Livro de Ofertas pode resultar em comportamento indefinido. Nesses casos, o parser pode emitir a seguinte mensagem:

Parser: Acessos a contextos posicionais dentro de escopos condicionais e de laços possuem comportamento indefinido!
O uso de contextos posicionais em funções de execução ou do Livro, como HasPosition[1] ou AskPrice[1], geram resultados inconsistentes na automação de estratégias. Isso ocorre porque, na automação, não existem dados históricos de posição, preço de posição ou ordens, como ocorre no modo de backtest.

Isso significa que, durante a automação de estratégias em tempo real, o sistema não mantém histórico para infor- mações como:

• estado de posição (comprado, vendido, zerado);

• preço médio da posição;

• ordens executadas ou pendentes;

• dados do Livro de Ofertas.

Dessa forma, expressões como HasPosition[1], AvgPrice[1], BidPrice[1] ou AskPrice[1] não possuem referência válida e podem produzir resultados imprevisíveis.

Exemplo de uso incorreto:

if (HasPosition[1]) then

SellShortAtMarket;

No exemplo acima, o acesso a HasPosition[1] não possui referência válida durante a automação, podendo gerar resultados inconsistentes.

Atenção: O uso de acessos posicionais ([n]) em funções de execução ou do Livro é desaconselhado em automações, mesmo que o código funcione corretamente em modo de backtest.

Recomendação: Caso seja necessário comparar estados anteriores durante a automação, recomenda-se armazenar explicitamente os valores desejados em variáveis auxiliares no momento em que eles ocorrem, garantindo assim um comportamento determinístico.

4.6 Sombreamento de funções por variáveis

Na NTSL, variáveis e funções compartilham o mesmo espaço de nomes no escopo do script. Isso significa que, ao declarar uma variável com o mesmo identificador de uma função existente, a função será sobrescrita por essa variável no contexto atual. Esse comportamento é conhecido como sombreamento.
Quando isso ocorre, a função original deixa de estar acessível enquanto a variável estiver em escopo, o que pode resultar em erros de execução, especialmente ao utilizar nomes de funções nativas como BuyToCover, SellToCover, entre outras.

Exemplo: Sombreamento de função nativa

var

BuyToCover: integer;

begin

BuyToCover := 1; // A função BuyToCover é sobrescrita por esta variável if Close > Media(Close, 20) then

BuyToCover(); // Erro: BuyToCover agora é um inteiro , não uma função

end;

No exemplo acima, a função BuyToCover é uma função nativa usada para envio de ordens de recompra a descoberto.
No entanto, ao declarar uma variável com o mesmo nome (BuyToCover: integer), a função original foi sobrescrita.
A tentativa de invocação da função resulta em erro, pois o nome agora se refere a um valor inteiro.

Boas práticas

• Evite declarar variáveis com nomes iguais a funções nativas, como BuyToCover, SellShortStop, Media, etc.

• Prefira nomes mais descritivos para variáveis, como qtdeCompra, reversaoLong, ativarSinal, etc.

• Sempre revise se o nome escolhido para a variável não corresponde a nenhuma função da linguagem.

4.7 Constantes

São utilizadas para a inserção de parâmetros de determinadas funções, estes valores não podem ser alterados pelo usuário.

Booleanos:
Representam o estado lógico de uma variável ou expressão.

• True - Verdadeiro.

• False - Falso.

Lado da Ordem:

• osBuy - Ordem de compra.

• osSell - Ordem de venda.

Opções:

• optCall - Opção de compra.

• optPut - Opção de venda.

Tipo de Ordem:

• otLimit - Tipo limite.

• otMarket - A mercado.

• otStopLimit - Tipo stop.

Bolsa:
Identificam o feed de dados (bolsa) de um ativo. São utilizadas pela função Asset() e retornadas pela função
GetFeed. As bolsas disponíveis dependem do acesso do usuário, portanto nem todas aparecem na aba "Constantes" da plataforma.

• feedActivTrades - ActivTrades.

• feedAmex - NYSE American (AMEX).

• feedBCB - Banco Central do Brasil.

• feedBMF - B3, segmento de derivativos (BM&F).

• feedBMFSynthetic - B3, contratos sintéticos (contínuos) de derivativos.

• feedBovespa - B3, segmento de ações (Bovespa).

• feedCBOT - Chicago Board of Trade.

• feedCME - Chicago Mercantile Exchange.

• feedCOMEX - Commodity Exchange.

• feedDooPrime - Doo Prime.

• feedDowJones - Índices Dow Jones.

• feedEconomic - Indicadores econômicos.

• feedFXGlobe - FXGlobe.

• feedMetrics - Métricas e índices proprietários Nelogica.

• feedNasdaq - Nasdaq.

• feedNyse - New York Stock Exchange.

• feedOXR - Open Exchange Rates (moedas).

• feedVector - Vector.

• feedZeroMarket - ZeroMarkets.

Agentes:
Identificam a corretora (participante de negociação) usada para filtrar os dados. São utilizadas no parâmetro AgentID das funções VolumeAgent(), AvgAgent() e BalanceAgent(). O valor ao lado de cada constante é o código do participante na B3.

• baAgora - 39

• baAlfa - 4

• baAmaril - 226

• baAdvalor - 979

• baAtiva - 147

• baC6 - 6003

• baGradual - 227

• baCapital - 88

• baGuide - 15

• baCitigroup - 77

• baHCommcor - 115

• baCGD - 102

• baClear - 308

• baIcap - 735

• baIdeal - 1618

• baInter - 1099

• baBanrisul - 172

• baCodepe - 234

• baBradesco - 1346

• baCoinvalores - 74

• baIntlFcStone - 1130

• baBradesco2 - 72

• baCreditSuisse - 45

• baItau - 114

• baBB - 254

• baBB2 - 2659

• baBGC - 122

• baBNP - 251

• baBTG - 1026

• baBTG2 - 85

• baBTG3 - 119

• baDiferencial - 140

• baJPMorgan - 16

• baNuInvest - 90

• baElite - 174

• baFator - 131

• baGenial - 120

• baGeral - 186

• baMirae - 262

• baModal - 1982

• baMorgan - 40

• baNecton - 23

• baNovaFutura - 93

• baGoldman - 238

• baOrama - 3701

• baPlanner - 129

• baRico - 386

• baSafra - 59

• baSantander - 27

• baSicredi - 1850

• baSpinelli - 10

• baTerra - 107

• baToro - 4090

• baTov - 82

• baVitreo - 1855

• baWarren - 92

• baXP - 3

• baUm - 37

• baUBS - 8

• baBES - 54

• baCriptoXP - 188

• baLev - 746

• baLiga - 7029

• baMerc - 106

• baMerrill - 13

• baRBCapital - 1089

• baRenascenca - 92

• baSenso - 191

• baSicoob - 1953

• baSita - 187

• baTullett - 127

• baMaster - 83

• baScotiabank - 7078

• baSocopa - 58

• baSolidus - 177

• baVotorantim - 21

• baNoInvest - 63

• baNovaFutura2 - 564

• baPicchioni - 232

• baWalpires - 86

Nas plataformas da família Black Arrow (ativos internacionais), o grupo Agentes é substituído pelas constantes abaixo:

• baFXGlobe - 344

• baZeroMarket - 338

• baZimtra - 356

• baActivTrades - 328

• baNinjaTrader - 347

• baPlus500 - 365

Estado do Ativo:
Representam o estado da sessão de negociação do ativo, retornado pela função AssetState().

• esFechado - Mercado fechado (equivale ao valor 0).

• esLeilaoAbertura - Leilão de abertura, incluindo leilão prolongado (equivale ao valor 1).

• esPregao - Pregão regular (equivale ao valor 2).

• esLeilaoFechamento - Leilão de fechamento (equivale ao valor 3).

• esAfterMarket - After-market (equivale ao valor 4).

Cores:

• clAqua ou clAzulClaro - Cor azul-claro

• clBlack ou clPreto - Cor preta

• clAzul - Cor azul

• clCreme - Cor creme

• clCinzaEscuro - Cor cinza-escuro

• clFucsia - Cor fúcsia

• clCinza - Cor cinza

• clVerde - Cor verde

• clVerdeLimao - Cor verde-limão

• clCinzaClaro - Cor cinza-claro

• clMarrom - Cor marrom

• clCinzaMedio - Cor Cinza médio

• clVerdeClaro - Cor verde-claro

• clAzulMarinho - Cor azul-marinho

• clVerdeOliva - Cor verde-oliva

• clPurpura - Cor púrpura

• clVermelho - Cor vermelha

• clPrata - Cor prata

• clAzulClaro - Cor azul-claro

• clTeal - Cor Verde-azulado

• clBranco - Cor branca

• clAmarelo - Cor amarela

Tipo Gráfico:
Representam o tipo de gráfico utilizado em um plot. São utilizadas pela função SetPlotType().

• igLine - Linha (equivale ao valor 0).

• igHistogram - Histograma (equivale ao valor 1).

Estilo de Linha:
Representam o estilo de linha utilizado em um plot ou em um estudo desenhado no gráfico. São utilizadas pelas funções SetPlotStyle(), HorizontalLineCustom(), VerticalLineCustom() e LineSegment().

• psSolid - Linha contínua (equivale ao valor 0).

• psDash - Linha tracejada, traço longo (equivale ao valor 1).

• psDot - Linha tracejada, traço curto (equivale ao valor 2).

• psDashDot - Linha tracejada, traço longo e curto (equivale ao valor 3).

• psDashDotDot - Linha tracejada, traço longo e dois curtos (equivale ao valor 4).

Posição do Texto:
Definem o canto em que o texto é ancorado em uma linha ou segmento desenhado no gráfico. São utilizadas no parâmetro TextPosition das funções HorizontalLineCustom(), VerticalLineCustom() e LineSegment().

• tpTopLeft - Texto no canto superior esquerdo (equivale ao valor 0).

• tpTopRight - Texto no canto superior direito (equivale ao valor 1).

• tpBottomLeft - Texto no canto inferior esquerdo (equivale ao valor 2).

• tpBottomRight - Texto no canto inferior direito (equivale ao valor 3).

Posição no Candle:
Definem o posicionamento vertical de um texto em relação ao candle. São utilizadas no parâmetro Position da função PlotText().

• posBottom - Abaixo do candle (equivale ao valor 0).

• posCenter - Centralizado no candle (equivale ao valor 1).

• posTop - Acima do candle (equivale ao valor 2).

• posPrice - No preço informado no parâmetro Price (equivale ao valor 3).

Constantes Matemáticas:

• Math_PI – Número Pi

• Math_Sqrt2 – Raiz quadrada de 2

• Math_Euler – Número de Euler

• Math_Log2E – log2(e)

• Math_Log10E – log10(e)

• Math_Ln2 – ln(2)

• Math_Ln10 – ln(10)

• Math_PI_Div2 – π/2

• Math_PI_Div4 – π/4

• Math_1DivPI – 1/π

• Math_2DivPI – 2/π

• Math_2DivSqrtPI – 2/
√

√

π

• Math_1DivSqrt2 – 1/

• Math_SqrtPI – Raiz quadrada de π

• Math_EulerMascheroni – Constante de Euler-Mascheroni

• Math_Phi – Número de Ouro

• Math_EmbreeTrefethen – Constante de Embree-Trefethen

• Math_FeigenbaumDelta – Constante de Feigenbaum (δ)

• Math_FeigenbaumAlpha – Constante de Feigenbaum (α)

• Math_TwinPrime – Constante dos primos gêmeos

• Math_MeisselMertens – Constante de Meissel-Mertens

• Math_BrunTwinPrimes – Constante de Brun para primos gêmeos

• Math_BrunQuadruples – Constante de Brun para primos quádruplos

• Math_BruijnNewman – Constante de Bruijn-Newman

• Math_Catalan – Constante de Catalan

• Math_LandauRamanujan – Constante de Landau-Ramanujan

• Math_Viswanath – Constante de Viswanath

• Math_Legendre – Constante de Legendre

• Math_RamanujanSoldner – Constante de Ramanujan-Soldner

• Math_ErdosBorwein – Constante de Erdős-Borwein

• Math_Liouville – Constante de Liouville

• Math_MinInt – Menor inteiro suportado

• Math_MaxInt – Maior inteiro suportado

Constantes de Período:

• itAggressor – Período baseado no agressor da operação (quem iniciou a negociação).

• itDaily – Período diário.

• itInversion – Período por inversão de direção do preço.

• itKagiChart – Período Kagi, muda de direção conforme variação definida.

• itLote – Período baseado em quantidade de lotes negociados.

• itMinute – Período por minutos fixos.

• itMonthly – Período mensal.

• itPointFigure – Período Ponto Figura, baseado em variação de preço.

• itQtd – Período baseado em quantidade de negócios.

• itRange – Período baseado em variação de preço fixa.

• itRenko – Período Renko, muda conforme variação de preço definida.

• itSecond – Período por segundos fixos.

• itTrade – Período por microquantidade de trades.

• itVarInv – Período por variação inversa.

• itVariation – Período baseado em variação de preço ou percentual.

• itWeekly – Período semanal.

• itYearly – Período anual.

Tipo de Média:

• kaADX - Média baseada no indicador ADX.

• kaArithmetic - Média aritmética simples.

• kaExponential - Média móvel exponencial.

• kaWeighted - Média móvel ponderada.

• kaWelles - Média de Welles Wilder.

Tipo de Valor:

• tvClose - Valor de fechamento.

• tvMax - Valor máximo.

• tvMin - Valor mínimo.

• tvOpen - Valor de abertura.

Tipo de Volume:
Definem qual medida de volume será analisada. São utilizadas no parâmetro Type das funções HighestVolume(),
HighestVolumePrice() e VolumeAtPrice().

• vtFinancial - Volume financeiro.

• vtQuantity - Quantidade de papéis (contratos).

• vtTrades - Número de negócios.

Comparação:
Representam o resultado da comparação entre dois valores, retornado pela função CompareFloat().

• LessThanValue - O primeiro valor é menor que o segundo (equivale ao valor -1).

• EqualsValue - Os dois valores são iguais (equivale ao valor 0).

• GreaterThanValue - O primeiro valor é maior que o segundo (equivale ao valor 1)._

### Tipos de dados
*Manual NTSL v4.7 (14/10/2026) — p. 15*

4 Variáveis, tipos de dados e constantes

As variáveis são utilizadas para armazenar dados, conforme seu tipo específico.

4.1 Tipos de dados

• Float ou Real - Representa números de ponto flutuante.

• Integer ou Inteiro - Representa números inteiros.

• Boolean ou Booleano - Representação lógica: True ou Verdadeiro e False ou Falso

• Serie - Representa uma série de dados.

A NTSL suporta a conversão implícita de valores Float a Inteiros, isto é, atribuir um valor Float diretamente a um valor
Integer. O valor inteiro será o valor do ponto flutuante, descartando as casas decimais. Por exemplo, se eu atribuir
2.99 ou 2.35 a um inteiro, o valor do inteiro será 2. Para outros comportamentos de arredondamento, a linguagem disponibiliza as funções Ceiling, Floor e Round. Para mais detalhes sobre essas funções, consulte esse mesmo manual na seção de funções.
As variáveis na linguagem oferecem uma flexibilidade muito maior do que na maioria dos sistemas de programação conhecidos.
Todas as variáveis são globais, e deve ser dada uma atenção especial quando utilizadas. Ao programar usando variáveis globais, deve ser levado em consideração o comportamento do processamento do fluxo de execução, a cada vez que o fluxo de execução é realizado as variáveis podem ter seu valor alterado com base no último valor que tinham.
Quando uma variável for acessada utilizando colchetes (exemplo: [x]), ela será considerada uma série de dados pelo compilador. Seu comportamento é diferente: séries iniciam cada candle com seu valor zerado. Também é possível navegar entre valores atuais e passados, mediante indexação.

4.2 Séries de dados

As séries de dados são utilizadas para obter dados específicos de cada Candle.
Séries:

• Abertura ou Open - Retorna o valor de abertura de cada candle.

• Fechamento ou Close - Retorna o dado de fechamento.

• Minima ou Low - Retorna o valor de mínima.

• Maxima ou High - Retorna o dado de máxima.

• Quantidade ou Quantity - Retorna o valor de contratos negociados de cada candle.

• Volume - Retorna o dado de volume financeiro de cada candle.

4.3 Arrays

Análogo ao tipo Serie, a estrutura de um Array permite o armazenamento de dados de um tipo específico, contudo, após sua criação, seu comprimento será fixo, o que permite uma alocação menor de memória.
O acesso aos elementos de um Array é efetuado mediante indexação.
Estrutura da declaração:

var

Variavel : Array[Tamanho] Of Tipo;

A fim de exemplificação, segue um exemplo de declaração de um Array estático de 10 elementos, o qual é preenchido com valores de 1 a 10 (primeira estrutura de repetição), e efetuado o somatório dos valores:

### Séries de dados
*Manual NTSL v4.7 (14/10/2026) — p. 15*

4 Variáveis, tipos de dados e constantes

As variáveis são utilizadas para armazenar dados, conforme seu tipo específico.

4.1 Tipos de dados

• Float ou Real - Representa números de ponto flutuante.

• Integer ou Inteiro - Representa números inteiros.

• Boolean ou Booleano - Representação lógica: True ou Verdadeiro e False ou Falso

• Serie - Representa uma série de dados.

A NTSL suporta a conversão implícita de valores Float a Inteiros, isto é, atribuir um valor Float diretamente a um valor
Integer. O valor inteiro será o valor do ponto flutuante, descartando as casas decimais. Por exemplo, se eu atribuir
2.99 ou 2.35 a um inteiro, o valor do inteiro será 2. Para outros comportamentos de arredondamento, a linguagem disponibiliza as funções Ceiling, Floor e Round. Para mais detalhes sobre essas funções, consulte esse mesmo manual na seção de funções.
As variáveis na linguagem oferecem uma flexibilidade muito maior do que na maioria dos sistemas de programação conhecidos.
Todas as variáveis são globais, e deve ser dada uma atenção especial quando utilizadas. Ao programar usando variáveis globais, deve ser levado em consideração o comportamento do processamento do fluxo de execução, a cada vez que o fluxo de execução é realizado as variáveis podem ter seu valor alterado com base no último valor que tinham.
Quando uma variável for acessada utilizando colchetes (exemplo: [x]), ela será considerada uma série de dados pelo compilador. Seu comportamento é diferente: séries iniciam cada candle com seu valor zerado. Também é possível navegar entre valores atuais e passados, mediante indexação.

4.2 Séries de dados

As séries de dados são utilizadas para obter dados específicos de cada Candle.
Séries:

• Abertura ou Open - Retorna o valor de abertura de cada candle.

• Fechamento ou Close - Retorna o dado de fechamento.

• Minima ou Low - Retorna o valor de mínima.

• Maxima ou High - Retorna o dado de máxima.

• Quantidade ou Quantity - Retorna o valor de contratos negociados de cada candle.

• Volume - Retorna o dado de volume financeiro de cada candle.

4.3 Arrays

Análogo ao tipo Serie, a estrutura de um Array permite o armazenamento de dados de um tipo específico, contudo, após sua criação, seu comprimento será fixo, o que permite uma alocação menor de memória.
O acesso aos elementos de um Array é efetuado mediante indexação.
Estrutura da declaração:

var

Variavel : Array[Tamanho] Of Tipo;

A fim de exemplificação, segue um exemplo de declaração de um Array estático de 10 elementos, o qual é preenchido com valores de 1 a 10 (primeira estrutura de repetição), e efetuado o somatório dos valores:

### Arrays
*Manual NTSL v4.7 (14/10/2026) — p. 15*

4 Variáveis, tipos de dados e constantes

As variáveis são utilizadas para armazenar dados, conforme seu tipo específico.

4.1 Tipos de dados

• Float ou Real - Representa números de ponto flutuante.

• Integer ou Inteiro - Representa números inteiros.

• Boolean ou Booleano - Representação lógica: True ou Verdadeiro e False ou Falso

• Serie - Representa uma série de dados.

A NTSL suporta a conversão implícita de valores Float a Inteiros, isto é, atribuir um valor Float diretamente a um valor
Integer. O valor inteiro será o valor do ponto flutuante, descartando as casas decimais. Por exemplo, se eu atribuir
2.99 ou 2.35 a um inteiro, o valor do inteiro será 2. Para outros comportamentos de arredondamento, a linguagem disponibiliza as funções Ceiling, Floor e Round. Para mais detalhes sobre essas funções, consulte esse mesmo manual na seção de funções.
As variáveis na linguagem oferecem uma flexibilidade muito maior do que na maioria dos sistemas de programação conhecidos.
Todas as variáveis são globais, e deve ser dada uma atenção especial quando utilizadas. Ao programar usando variáveis globais, deve ser levado em consideração o comportamento do processamento do fluxo de execução, a cada vez que o fluxo de execução é realizado as variáveis podem ter seu valor alterado com base no último valor que tinham.
Quando uma variável for acessada utilizando colchetes (exemplo: [x]), ela será considerada uma série de dados pelo compilador. Seu comportamento é diferente: séries iniciam cada candle com seu valor zerado. Também é possível navegar entre valores atuais e passados, mediante indexação.

4.2 Séries de dados

As séries de dados são utilizadas para obter dados específicos de cada Candle.
Séries:

• Abertura ou Open - Retorna o valor de abertura de cada candle.

• Fechamento ou Close - Retorna o dado de fechamento.

• Minima ou Low - Retorna o valor de mínima.

• Maxima ou High - Retorna o dado de máxima.

• Quantidade ou Quantity - Retorna o valor de contratos negociados de cada candle.

• Volume - Retorna o dado de volume financeiro de cada candle.

4.3 Arrays

Análogo ao tipo Serie, a estrutura de um Array permite o armazenamento de dados de um tipo específico, contudo, após sua criação, seu comprimento será fixo, o que permite uma alocação menor de memória.
O acesso aos elementos de um Array é efetuado mediante indexação.
Estrutura da declaração:

var

Variavel : Array[Tamanho] Of Tipo;

A fim de exemplificação, segue um exemplo de declaração de um Array estático de 10 elementos, o qual é preenchido com valores de 1 a 10 (primeira estrutura de repetição), e efetuado o somatório dos valores:

### Correlação de múltiplos ativos
*Manual NTSL v4.7 (14/10/2026) — p. 16*

var

i, sum : Integer;
lista : array[1..10] of Integer;

begin

for i := 1 to 10 do lista[i] := i;

sum := 0;
for i := 1 to 10 do sum := sum + i;
Plot(sum);

end;

4.4 Correlação de múltiplos ativos

A função Asset permite acessar dados de outros ativos dentro da estratégia, possibilitando correlações, comparações entre períodos e aplicação de indicadores em múltiplos instrumentos. Essa funcionalidade amplia consideravelmente as possibilidades de análise e automação, permitindo o uso de séries de diferentes ativos, intervalos e tipos de gráfico.

Estrutura básica: A função Asset pode ser instanciada de formas diferentes, dependendo do contexto de uso
(const ou input) e da origem do ativo (ticker explícito ou ativo do gráfico).

Asset(Ticker : String, Bolsa : Const, Período : Período, Offset : Integer,

Fator : Integer);

**Parâmetros**

Ticker: String; Ticker do ativo.

Bolsa: Const; Bolsa na qual o ativo está listado.

Período: Período [Opcional]; Define o tipo de gráfico (ex: itMinute, itDaily).

Offset: Integer [Opcional]; Define o valor numérico do período.

Fator: Integer [Opcional]; Aplicável apenas para gráficos do tipo ponto figura.

Importante:

• Os parâmetros Período e Offset são opcionais apenas quando omitidos em conjunto.

• Não é permitido informar apenas um dos dois parâmetros.

• O uso de Período, Offset e Fator está disponível apenas para usuários das plataformas Ultra ou Automação

2.0.

Declaração como const

Quando declarada como constante, a função Asset cria uma série fixa durante toda a execução da estratégia, permitindo o uso de ativos distintos ou do mesmo ativo do gráfico principal.

const

A1 = Asset("WINFUT", feedBMF, itSecond, 10);

begin

Plot(A1.close);
Plot2(A1.open);

end;

Declaração como input

Também é possível declarar ativos como entradas da estratégia, permitindo alterar o ativo e seus parâmetros sem recompilar o código.

input

A1("DOLFUT", feedBMF, itSecond, 10);

begin

Plot(A1.ADX(9, 9));

end;

Uso de GetAsset e período personalizado

A função Asset pode ser instanciada utilizando GetAsset, que representa o ativo carregado no gráfico principal. Essa forma de uso permite acessar o mesmo ativo, porém utilizando um período ou intervalo diferente do gráfico principal.
Atenção: Ao utilizar o Asset com períodos divergentes (isto é, um período diferente do gráfico principal), os dados retornados podem não coincidir com os valores esperados para aquele período. Isso ocorre porque a função utiliza como referência o candle mais próximo do candle atual do ativo analisado. Por exemplo, ao acessar a abertura diária de um ativo a partir de um gráfico de 1 minuto ou Renko, o valor de open retornado pode divergir do valor real de abertura daquele período. Para garantir a precisão dos dados, é recomendável especificar explicitamente a série desejada na declaração do Asset, como em: Asset("INDFUT", feedBMF, itDaily).

const

A1 = Asset(GetAsset, itSecond, 10);

begin

Plot(A1.close);

end;

Regras de uso:

• GetAsset substitui simultaneamente os parâmetros Ticker e Bolsa.

• A variável que utiliza Asset com GetAsset deve obrigatoriamente ser declarada como const.

• Os parâmetros Período e Offset tornam-se obrigatórios.

• Quando o período informado for do tipo Ponto & Figura, o parâmetro Fator torna-se obrigatório.

• O parâmetro Fator é exclusivo para períodos do tipo Ponto & Figura e não deve ser utilizado com períodos

temporais ou outros períodos atemporais.

Uso de indicadores com Asset

_Indicadores podem agora ser utilizados diretamente como propriedades do Asset, permitindo aplicar estudos técnicos sobre diferentes ativos e períodos.

const

A1 = Asset("WINFUT", feedBMF, itSecond, 10);

begin

Plot(A1.ADX(9, 9));

end;

Indicadores compatíveis com Asset

Os seguintes indicadores podem ser utilizados como propriedades do Asset:

• AccuDistr

• AccuDistrW

• ADX

• AgressionVolBalance

• AgressionVolBuy

• AgressionVolSell

• AroonLin

• AroonOsc

• ForceIndex

• FrassonATR

• FullStochastic

• FuraChao

• FuraTeto

• HILOActivator

• HistVolatility

• IchimokuCloud

• ArmsEaseOfMov

• KeltnerCh

• AvgSeparation

• AvgTrueRange

• BalanceOfPower

• BollingerBandW

• BollingerBands

• CCI

• KVO

• MACD

• MFI

• MIMA

• MIMAROC

• Momentum

• ChaikinMoneyFlow

• MomentumStochastic

• ContadorDeCandle

• MoneyFlow

• DiPDiM

• DidiIndex

• DonchianCh

• EMA

• Envelope

• FastStochastic

• FastWMA

• MoneyFlowIndex

• OBV

• OBVAvg

• ParabolicSAR

• PhIbo

• Pivot

• PriceVolumeTrend

• PriorCote

• Ravi

• RenkoVTwo

• ROC

• RSI

• RSIStochastic

• SafeZoneDownTrend

• SafeZoneUpTrend

• Santo

• SMA

• SlowStochastic

• StopATR

• Tilson

• TopBottomDetector

• TRIX

• TRIXM

• VWAP

• VWAPDate

• VWAPMonthly

• VWAPWeekly

• VWMA

• Williams

Consultando o nome e feed do ativo

As funções GetAsset e GetFeed retornam respectivamente o ticker e a bolsa do ativo declarado.

const

WDO = Asset("WDOFUT", feedBMF);

begin

if (MaxBarsForward = 0) then

PlotText("Ticker: " + WDO.GetAsset +

" - Bolsa: " + WDO.GetFeed , clRed, 0, 7);

end;

Propriedades acessíveis via função Asset

A função Asset permite acessar e manipular um ativo diferente do gráfico principal e acessar suas informações e séries de preço e volume. As séries de preço e volume podem ser consultadas na seção 4.2 deste manual.

• GetFeed – Retorna o feed de dados do ativo.

• GetAsset – Retorna o próprio ativo.

• AskPrice – Preço do ask (preço de venda).

• AskSize – Tamanho do ask (quantidade disponível para venda).

• BidPrice – Preço do bid (preço de compra).

• BidSize – Tamanho do bid (quantidade disponível para compra).

• BookSpread – Diferença entre o melhor bid e o melhor ask.

• Lote – Tamanho do lote do ativo.

• MinPriceIncrement – Incremento mínimo de preço.

• Strike – Preço de exercício (para derivativos como opções).

Bolsas disponíveis

As bolsas disponíveis dependem do acesso do usuário. A relação completa das constantes de bolsa está na seção
4.7 deste manual, e os feeds liberados para a conta podem ser consultados na aba "Constantes" da plataforma._

### Acessando dados anteriores
*Manual NTSL v4.7 (14/10/2026) — p. 20*

Exemplo de correlação entre múltiplos ativos

Exemplo de estratégia que colore os candles conforme a relação entre WDO e WIN.

const

WDO = Asset("WDOFUT", feedBMF);
WIN = Asset("WINFUT", feedBMF);

input

Periodo(20);

var

wdoMedia : Float;
winMedia : Float;

begin

wdoMedia := MediaExp(Periodo , WDO.close);
winMedia := MediaExp(Periodo , WIN.close);

if (WDO.close > wdoMedia) and (WIN.close < winMedia) then

PaintBar(clLime)

else if (WDO.close < wdoMedia) and (WIN.close > winMedia) then

PaintBar(clAqua);

end;

Observações e limitações

• O parâmetro Fator é utilizado apenas para gráficos de ponto figura.

• Cada ativo pode ter seu próprio intervalo e período, independentes do ativo principal.

• O limite máximo é de 30 ativos por estratégia.

• Em gráficos atemporais, o fechamento dos candles auxiliares pode não coincidir com o do ativo principal, o que

pode causar divergências entre o backtest/replay e a automação em tempo real.

4.5 Acessando dados anteriores

O dado atual de uma variável pode ser descrito por Variavel[0]. O número entre colchetes indica quantos períodos anteriores devem ser acessados, sendo 0 sempre referente à barra corrente. Para ilustrar melhor, vamos a um exemplo:

sResult := Preco[1];

A linha de código acima está atribuindo o valor da variável Preco[1] para a variável sResult. Imagine que Preço corresponde a todos os valores de fechamento da série de dados de um certo ativo, como na tabela abaixo:

Data

05/10/2010

04/10/2010

01/10/2010

30/09/2010

29/09/2010

dd/mm/aaaa

Posição

Preco[0]

Preco[1]

Preco[2]

Preco[3]

Preco[4]

Preco[5]

Valor

12,43

12,40

11,39

12,51

12,38

xx,xx

### Sombreamento de funções por variáveis
*Manual NTSL v4.7 (14/10/2026) — p. 21*

Portanto, Preco[1] refere-se ao valor de ontem do preço de fechamento (sResult vale então 12,40 em nosso ex- emplo). Dessa forma, o número inteiro que especificarmos entre colchetes indica ao sistema quantos períodos no passado deve-se acessar a informação.

Uso de dados anteriores em funções de execução e do Livro

Embora o acesso a dados anteriores seja plenamente suportado para séries históricas de preços e indicadores, é importante observar que nem todos os contextos possuem histórico disponível.

No modo de backtest, o sistema dispõe de histórico completo de preços, posições e ordens, permitindo o uso de acessos posicionais nesses contextos. Já na automação em tempo real, essas informações existem apenas em seu estado atual, não havendo histórico armazenado para posições, ordens ou dados do Livro de Ofertas.

Em especial, o uso de acessos posicionais em funções de execução de estratégias ou em funções relacionadas ao Livro de Ofertas pode resultar em comportamento indefinido. Nesses casos, o parser pode emitir a seguinte mensagem:

Parser: Acessos a contextos posicionais dentro de escopos condicionais e de laços possuem comportamento indefinido!
O uso de contextos posicionais em funções de execução ou do Livro, como HasPosition[1] ou AskPrice[1], geram resultados inconsistentes na automação de estratégias. Isso ocorre porque, na automação, não existem dados históricos de posição, preço de posição ou ordens, como ocorre no modo de backtest.

Isso significa que, durante a automação de estratégias em tempo real, o sistema não mantém histórico para infor- mações como:

• estado de posição (comprado, vendido, zerado);

• preço médio da posição;

• ordens executadas ou pendentes;

• dados do Livro de Ofertas.

Dessa forma, expressões como HasPosition[1], AvgPrice[1], BidPrice[1] ou AskPrice[1] não possuem referência válida e podem produzir resultados imprevisíveis.

Exemplo de uso incorreto:

if (HasPosition[1]) then

SellShortAtMarket;

No exemplo acima, o acesso a HasPosition[1] não possui referência válida durante a automação, podendo gerar resultados inconsistentes.

Atenção: O uso de acessos posicionais ([n]) em funções de execução ou do Livro é desaconselhado em automações, mesmo que o código funcione corretamente em modo de backtest.

Recomendação: Caso seja necessário comparar estados anteriores durante a automação, recomenda-se armazenar explicitamente os valores desejados em variáveis auxiliares no momento em que eles ocorrem, garantindo assim um comportamento determinístico.

4.6 Sombreamento de funções por variáveis

Na NTSL, variáveis e funções compartilham o mesmo espaço de nomes no escopo do script. Isso significa que, ao declarar uma variável com o mesmo identificador de uma função existente, a função será sobrescrita por essa variável no contexto atual. Esse comportamento é conhecido como sombreamento.
Quando isso ocorre, a função original deixa de estar acessível enquanto a variável estiver em escopo, o que pode resultar em erros de execução, especialmente ao utilizar nomes de funções nativas como BuyToCover, SellToCover, entre outras.

### Constantes
*Manual NTSL v4.7 (14/10/2026) — p. 22*

Exemplo: Sombreamento de função nativa

var

BuyToCover: integer;

begin

BuyToCover := 1; // A função BuyToCover é sobrescrita por esta variável if Close > Media(Close, 20) then

BuyToCover(); // Erro: BuyToCover agora é um inteiro , não uma função

end;

No exemplo acima, a função BuyToCover é uma função nativa usada para envio de ordens de recompra a descoberto.
No entanto, ao declarar uma variável com o mesmo nome (BuyToCover: integer), a função original foi sobrescrita.
A tentativa de invocação da função resulta em erro, pois o nome agora se refere a um valor inteiro.

Boas práticas

• Evite declarar variáveis com nomes iguais a funções nativas, como BuyToCover, SellShortStop, Media, etc.

• Prefira nomes mais descritivos para variáveis, como qtdeCompra, reversaoLong, ativarSinal, etc.

• Sempre revise se o nome escolhido para a variável não corresponde a nenhuma função da linguagem.

4.7 Constantes

São utilizadas para a inserção de parâmetros de determinadas funções, estes valores não podem ser alterados pelo usuário.

Booleanos:
Representam o estado lógico de uma variável ou expressão.

• True - Verdadeiro.

• False - Falso.

Lado da Ordem:

• osBuy - Ordem de compra.

• osSell - Ordem de venda.

Opções:

• optCall - Opção de compra.

• optPut - Opção de venda.

Tipo de Ordem:

• otLimit - Tipo limite.

• otMarket - A mercado.

• otStopLimit - Tipo stop.

Bolsa:
Identificam o feed de dados (bolsa) de um ativo. São utilizadas pela função Asset() e retornadas pela função
GetFeed. As bolsas disponíveis dependem do acesso do usuário, portanto nem todas aparecem na aba "Constantes" da plataforma.

• feedActivTrades - ActivTrades.

• feedAmex - NYSE American (AMEX).

• feedBCB - Banco Central do Brasil.

• feedBMF - B3, segmento de derivativos (BM&F).

• feedBMFSynthetic - B3, contratos sintéticos (contínuos) de derivativos.

• feedBovespa - B3, segmento de ações (Bovespa).

• feedCBOT - Chicago Board of Trade.

• feedCME - Chicago Mercantile Exchange.

• feedCOMEX - Commodity Exchange.

• feedDooPrime - Doo Prime.

• feedDowJones - Índices Dow Jones.

• feedEconomic - Indicadores econômicos.

• feedFXGlobe - FXGlobe.

• feedMetrics - Métricas e índices proprietários Nelogica.

• feedNasdaq - Nasdaq.

• feedNyse - New York Stock Exchange.

• feedOXR - Open Exchange Rates (moedas).

• feedVector - Vector.

• feedZeroMarket - ZeroMarkets.

Agentes:
Identificam a corretora (participante de negociação) usada para filtrar os dados. São utilizadas no parâmetro AgentID das funções VolumeAgent(), AvgAgent() e BalanceAgent(). O valor ao lado de cada constante é o código do participante na B3.

• baAgora - 39

• baAlfa - 4

• baAmaril - 226

• baAdvalor - 979

• baAtiva - 147

• baC6 - 6003

• baGradual - 227

• baCapital - 88

• baGuide - 15

• baCitigroup - 77

• baHCommcor - 115

• baCGD - 102

• baClear - 308

• baIcap - 735

• baIdeal - 1618

• baInter - 1099

• baBanrisul - 172

• baCodepe - 234

• baBradesco - 1346

• baCoinvalores - 74

• baIntlFcStone - 1130

• baBradesco2 - 72

• baCreditSuisse - 45

• baItau - 114

• baBB - 254

• baBB2 - 2659

• baBGC - 122

• baBNP - 251

• baBTG - 1026

• baBTG2 - 85

• baBTG3 - 119

• baDiferencial - 140

• baJPMorgan - 16

• baNuInvest - 90

• baElite - 174

• baFator - 131

• baGenial - 120

• baGeral - 186

• baMirae - 262

• baModal - 1982

• baMorgan - 40

• baNecton - 23

• baNovaFutura - 93

• baGoldman - 238

• baOrama - 3701

• baPlanner - 129

• baRico - 386

• baSafra - 59

• baSantander - 27

• baSicredi - 1850

• baSpinelli - 10

• baTerra - 107

• baToro - 4090

• baTov - 82

• baVitreo - 1855

• baWarren - 92

• baXP - 3

• baUm - 37

• baUBS - 8

• baBES - 54

• baCriptoXP - 188

• baLev - 746

• baLiga - 7029

• baMerc - 106

• baMerrill - 13

• baRBCapital - 1089

• baRenascenca - 92

• baSenso - 191

• baSicoob - 1953

• baSita - 187

• baTullett - 127

• baMaster - 83

• baScotiabank - 7078

• baSocopa - 58

• baSolidus - 177

• baVotorantim - 21

• baNoInvest - 63

• baNovaFutura2 - 564

• baPicchioni - 232

• baWalpires - 86

Nas plataformas da família Black Arrow (ativos internacionais), o grupo Agentes é substituído pelas constantes abaixo:

• baFXGlobe - 344

• baZeroMarket - 338

• baZimtra - 356

• baActivTrades - 328

• baNinjaTrader - 347

• baPlus500 - 365

Estado do Ativo:
Representam o estado da sessão de negociação do ativo, retornado pela função AssetState().

• esFechado - Mercado fechado (equivale ao valor 0).

• esLeilaoAbertura - Leilão de abertura, incluindo leilão prolongado (equivale ao valor 1).

• esPregao - Pregão regular (equivale ao valor 2).

• esLeilaoFechamento - Leilão de fechamento (equivale ao valor 3).

• esAfterMarket - After-market (equivale ao valor 4).

Cores:

• clAqua ou clAzulClaro - Cor azul-claro

• clBlack ou clPreto - Cor preta

• clAzul - Cor azul

• clCreme - Cor creme

• clCinzaEscuro - Cor cinza-escuro

• clFucsia - Cor fúcsia

• clCinza - Cor cinza

• clVerde - Cor verde

• clVerdeLimao - Cor verde-limão

• clCinzaClaro - Cor cinza-claro

• clMarrom - Cor marrom

• clCinzaMedio - Cor Cinza médio

• clVerdeClaro - Cor verde-claro

• clAzulMarinho - Cor azul-marinho

• clVerdeOliva - Cor verde-oliva

• clPurpura - Cor púrpura

• clVermelho - Cor vermelha

• clPrata - Cor prata

• clAzulClaro - Cor azul-claro

• clTeal - Cor Verde-azulado

• clBranco - Cor branca

• clAmarelo - Cor amarela

Tipo Gráfico:
Representam o tipo de gráfico utilizado em um plot. São utilizadas pela função SetPlotType().

• igLine - Linha (equivale ao valor 0).

• igHistogram - Histograma (equivale ao valor 1).

Estilo de Linha:
Representam o estilo de linha utilizado em um plot ou em um estudo desenhado no gráfico. São utilizadas pelas funções SetPlotStyle(), HorizontalLineCustom(), VerticalLineCustom() e LineSegment().

• psSolid - Linha contínua (equivale ao valor 0).

• psDash - Linha tracejada, traço longo (equivale ao valor 1).

• psDot - Linha tracejada, traço curto (equivale ao valor 2).

• psDashDot - Linha tracejada, traço longo e curto (equivale ao valor 3).

• psDashDotDot - Linha tracejada, traço longo e dois curtos (equivale ao valor 4).

Posição do Texto:
Definem o canto em que o texto é ancorado em uma linha ou segmento desenhado no gráfico. São utilizadas no parâmetro TextPosition das funções HorizontalLineCustom(), VerticalLineCustom() e LineSegment().

• tpTopLeft - Texto no canto superior esquerdo (equivale ao valor 0).

• tpTopRight - Texto no canto superior direito (equivale ao valor 1).

• tpBottomLeft - Texto no canto inferior esquerdo (equivale ao valor 2).

• tpBottomRight - Texto no canto inferior direito (equivale ao valor 3).

Posição no Candle:
Definem o posicionamento vertical de um texto em relação ao candle. São utilizadas no parâmetro Position da função PlotText().

• posBottom - Abaixo do candle (equivale ao valor 0).

• posCenter - Centralizado no candle (equivale ao valor 1).

• posTop - Acima do candle (equivale ao valor 2).

• posPrice - No preço informado no parâmetro Price (equivale ao valor 3).

Constantes Matemáticas:

• Math_PI – Número Pi

• Math_Sqrt2 – Raiz quadrada de 2

• Math_Euler – Número de Euler

• Math_Log2E – log2(e)

• Math_Log10E – log10(e)

• Math_Ln2 – ln(2)

• Math_Ln10 – ln(10)

• Math_PI_Div2 – π/2

• Math_PI_Div4 – π/4

• Math_1DivPI – 1/π

• Math_2DivPI – 2/π

• Math_2DivSqrtPI – 2/
√

√

π

• Math_1DivSqrt2 – 1/

• Math_SqrtPI – Raiz quadrada de π

• Math_EulerMascheroni – Constante de Euler-Mascheroni

• Math_Phi – Número de Ouro

• Math_EmbreeTrefethen – Constante de Embree-Trefethen

• Math_FeigenbaumDelta – Constante de Feigenbaum (δ)

• Math_FeigenbaumAlpha – Constante de Feigenbaum (α)

• Math_TwinPrime – Constante dos primos gêmeos

• Math_MeisselMertens – Constante de Meissel-Mertens

• Math_BrunTwinPrimes – Constante de Brun para primos gêmeos

• Math_BrunQuadruples – Constante de Brun para primos quádruplos

• Math_BruijnNewman – Constante de Bruijn-Newman

• Math_Catalan – Constante de Catalan

• Math_LandauRamanujan – Constante de Landau-Ramanujan

• Math_Viswanath – Constante de Viswanath

• Math_Legendre – Constante de Legendre

• Math_RamanujanSoldner – Constante de Ramanujan-Soldner

• Math_ErdosBorwein – Constante de Erdős-Borwein

• Math_Liouville – Constante de Liouville

• Math_MinInt – Menor inteiro suportado

• Math_MaxInt – Maior inteiro suportado

Constantes de Período:

• itAggressor – Período baseado no agressor da operação (quem iniciou a negociação).

• itDaily – Período diário.

• itInversion – Período por inversão de direção do preço.

• itKagiChart – Período Kagi, muda de direção conforme variação definida.

• itLote – Período baseado em quantidade de lotes negociados.

• itMinute – Período por minutos fixos.

• itMonthly – Período mensal.

• itPointFigure – Período Ponto Figura, baseado em variação de preço.

• itQtd – Período baseado em quantidade de negócios.

• itRange – Período baseado em variação de preço fixa.

• itRenko – Período Renko, muda conforme variação de preço definida.

• itSecond – Período por segundos fixos.

• itTrade – Período por microquantidade de trades.

• itVarInv – Período por variação inversa.

• itVariation – Período baseado em variação de preço ou percentual.

• itWeekly – Período semanal.

• itYearly – Período anual.

Tipo de Média:

• kaADX - Média baseada no indicador ADX.

• kaArithmetic - Média aritmética simples.

• kaExponential - Média móvel exponencial.

• kaWeighted - Média móvel ponderada.

• kaWelles - Média de Welles Wilder.

Tipo de Valor:

• tvClose - Valor de fechamento.

• tvMax - Valor máximo.

• tvMin - Valor mínimo.

• tvOpen - Valor de abertura.

Tipo de Volume:
Definem qual medida de volume será analisada. São utilizadas no parâmetro Type das funções HighestVolume(),
HighestVolumePrice() e VolumeAtPrice().

• vtFinancial - Volume financeiro.

• vtQuantity - Quantidade de papéis (contratos).

• vtTrades - Número de negócios.

Comparação:
Representam o resultado da comparação entre dois valores, retornado pela função CompareFloat().

• LessThanValue - O primeiro valor é menor que o segundo (equivale ao valor -1).

• EqualsValue - Os dois valores são iguais (equivale ao valor 0).

• GreaterThanValue - O primeiro valor é maior que o segundo (equivale ao valor 1).

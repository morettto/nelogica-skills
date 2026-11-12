---
name: ntsl-indicadores
description: Catálogo completo dos 159 indicadores do Profit que existem como funções NTSL, com assinatura, parâmetros e o que cada um mede. Use quando alguém perguntar qual indicador usar para uma necessidade, qual é o nome exato da função do indicador no Editor de Estratégias, ou ao montar o cálculo de um indicador dentro de uma estratégia NTSL.
---

# Indicadores NTSL — os 159 do manual v4.7

Fonte única: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026 (https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf). Catálogo extraído verbatim do capítulo 20 do manual (páginas 248 a 458). Cada indicador é uma **função** que devolve `Float` e pode ser plotada com `Plot()`/`PlotN()`.

## Regras que não se negociam

1. **Não invente indicador.** Se o nome não está na lista do fim desta skill, ele não existe como função NTSL no manual v4.7. Diga o que existe de mais próximo em vez de inventar um nome plausível.
2. **Não existe função `ATR()`.** Para Average True Range use `AvgTrueRange()`, `StopATR()` ou `FrassonATR()` — ou monte com `TrueRange` e uma média. O mesmo vale para `Stochastic` puro: existem `FastStochastic` e as variantes do capítulo 20.
3. **RSI atende por dois nomes**: `RSI(Periodo, Tipo)` e `IFR(Periodo)`.
4. **Parâmetros são posicionais e não têm valor default** quando o manual não diz. Confira a ordem na assinatura antes de escrever a chamada.
5. **Indicador da tela não é indicador do código.** Nem todo indicador nativo do gráfico tem função NTSL correspondente; a ponte é a função homônima do capítulo 20.
6. Sempre cite a página do manual ao afirmar parâmetro ou fórmula.

## Mapa rápido: necessidade → função

- Força da tendência (não a direção): `ADX` (p. 250)
- Direção e reversão: `AroonLin`, `AroonOsc`, `ParabolicSAR`, `AdaptiveMovingAverage`
- Volatilidade: `AvgTrueRange`, `BollingerBandW`, `StopATR`, `FrassonATR`, `HistVolatility`, `ImpliedVolatility`, `TWOMVVOLATILITY`, `LSVolatilityIndex`
- Suporte/resistência e topos/fundos: `FuraTeto`, `FuraChao`, `AllTimeHigh`, `AllTimeLow`, `AutoFibonacci`, `AutoFibonacciCustom`
- Preço médio e referência: `SMA`, `EMA`, `VWAP`, `VWAPDate`, `VWAPWeekly`, `VWAPMonthly`, `VWMA`, `MIMA`
- Envelope em torno da média: `BollingerBands` (valor), `BollingerBPerc` (%B), `BollingerBandW` (largura)
- Fluxo, agressão e volume: `AccAgressSaldo`, `AgressionVolBuy`, `AgressionVolSell`, `AgressionVolBalance`, `AvgAgrBuySell`, `BalanceAgent`, `VolumeAgent`, `VolumeAtPrice`, `HighestVolume`, `BidAsk`
- Volume clássico: `OBV`, `OBVAvg`, `OnBalanceTR`, `AccuDistr`, `AccuDistrW`, `MoneyFlowIndex`, `ArmsEaseOfMov`
- Momentum e osciladores: `RSI`, `IFR`, `MACD`, `FastStochastic`, `Williams`, `BalanceOfPower`, `BearPower`

## Assinaturas conferidas no manual

```ntsl
Função ADX(Periodo : Integer; Media : Integer): Float;
Função AroonOsc(Periodo : Integer): Float;
Função BollingerBands(Desvio : Float; PeriodoMédia: Integer; Tipo: Integer): Float;
Função BollingerBandW(Desvio : Float; PeriodoMédia: Integer; Tipo: Integer): Float;
Função BollingerBPerc(Desvio : Float; PeriodoMédia: Integer; Tipo: Integer): Float;
Função AvgTrueRange(Periodo : Integer; Tipo: Integer): Float;
Função ParabolicSAR(Fator : Float; Limite : Float): Float;
Função SMA(Periodo : Integer; TipoValor : Integer; TipoMedia : Integer): Float;
Função EMA(Periodo : Integer; TipoValor : Integer): Float;
Função VWAP(Periodo : Integer): Float;
Função VWAPDate(Data : Integer; Time : Integer): Float;
Função MACD(MediaLonga : Integer; MediaCurta : Integer; Sinal : Integer): Float;
Função RSI(Periodo : Integer; Tipo : Integer): Float;
Função IFR(Periodo : Integer): Float;
Função FastStochastic(Periodo : Integer; PeriodoMedia : Integer;
Função MoneyFlowIndex(Periodo : Integer): Float;
Função OBV(): Float;
Função OBVAvg(Periodo : Integer; Tipo : Integer): Float;
Função OnBalanceTR(): Float;
Função AccAgressSaldo(Tipo : Integer): Float;
Função AgressionVolBuy(): Float;
Função AgressionVolSell(): Float;
Função VolumeAtPrice(Interval: Integer; Offset: Integer; Type: Integer; Standard:
```

## As 159 funções do capítulo de indicadores

TWOMVVOLATILITY, ADX, AccAgressSaldo, AccuDistr, AccuDistrW, AdaptiveMovingAverage, AgressionVolBalance, AgressionVolBuy, AgressionVolSell, AllTimeHigh, AllTimeLow, ArmsEaseOfMov, AroonLin, AroonOsc, AutoFibonacci, AutoFibonacciCustom, Averan, AvgAgent, AvgAgrBuySell, AvgAgrTotal, AvgSeparation, AvgTrueRange, BTCPrice, BTCSpread, BalanceAgent, BalanceOfPower, BearPower, BidAsk, BollingerBPerc, BollingerBandW, BollingerBands, BullPower, CCI, ChaikinMoneyFlow, ChaikinOsc, ChainSetup, COHENPRICEWAVE, COHENWEISWAVE, ContadorDeCandle, DTOscillator, DarvasBox, DecisionPoints, DiPDiM, DiDiIndex, DivergenceDetector, DonchianCH, EMA, Envelope, Euroinvest, FastStochastic, FastWMA, FgzRobot, FinancialVol, ForceIndex, FrassonATR, FrassonVH, FullStochastic, FuraChao, FuraTeto, HeikinAshi, HighestVolume, HighestVolumePrice, HiLoActivator, HistVolatility, HullMovingAverage, IchimokuCloud, ImpliedVolatility, KVO, KeltnerCH, LSVolatilityIndex, LinearRegressionChannel, MACD, MFI, MIMA, MIMAROC, MADRIDTRENDSQUEEZE, MAGOMACD, MAGOMEDIAS, Momentum, MomentumStochastic, MoneyFlow, MoneyFlowIndex, MADRIDMOVINGAVERAGE, NelogicaBottomFinder, NelogicaPullBackFinder, NelogicaWeisWave, OBV, OBVAvg, OnBalanceTR, OpenDaily, OpenInterest, PTAX, PTAXFuturo, ParabolicSAR, Phibo, Pivot, PowerMeter, PRICENERY, PriceOsc, PriceVolumeTrend, PriorCote, QuantityVol, RBG, ROC, RSI, Rafi, TENDENCYTRACKER, Ravi, RenkoVTwo, RsiStochastic, SMA, SafeZoneDownTrend, SafeZoneUpTrend, SampleAverage, SampleBollinger, SampleMACD, SampleRSI, SampleStochastic, SampleVWAP, Santo, SlowStochastic, SOMOSRENKOTRENDMPONTO, StdDevConstPeriod, StopATR, TOSCANABRUNELLO, TOSCANAPICCOLA, TOSCANAPICCOLO, TOSCANAPRODUTIVIDADE, TOSCANART, TRIX, TRIXM, TRPTAX, TRPTAXFuturo, Tilson, TimeAgrBuySell, TimeAgrSellBuy, TimeAgrTotal, TopBottomDetector, TRENDAVERAGE, TRENDCLOUD, TRENDDIFUSOR, TRENDFLOW, TRENDSNIPER, TRENDSOLDIER, TRADENCIATRENDVARIATION, TRENDVOLAG, Trades, TwoMVAggression, TwoMVPower, VSS, VWAP, VWAPDate, VWAPMonthly, VWAPWeekly, VWMA, Valerie, VolumeAgent, VolumeAtPrice, Williams

## Referências (conteúdo verbatim, com página)

- `refs/01-a-f.md` — indicadores A–F
- `refs/02-g-m.md` — indicadores G–M
- `refs/03-n-s.md` — indicadores N–S
- `refs/04-t-z.md` — indicadores T–Z

Cada entrada traz disponibilidade por versão, descrição, sintaxe, parâmetros, exemplo de uso e a página do manual.

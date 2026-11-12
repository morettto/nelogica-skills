---
name: ntsl-graficos-e-candlestick
description: Funções gráficas do NTSL (Plot até Plot99, PlotN, PaintBar, linhas horizontais, cores, ConsoleLog) e as funções de padrão de candlestick (engolfo, martelo, doji, harami, estrela). Use quando o pedido for desenhar algo no gráfico do Profit a partir de uma estratégia, colorir candles, plotar indicador próprio ou detectar padrão de vela em código.
---

# Desenhar no gráfico e ler candles no NTSL

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulos 19 (Funções Gráficas, p. 205) e 17 (Funções de Candlestick, p. 192). Conteúdo verbatim em `refs/`.

## Regras que não se negociam

1. **`Plot()` plota, não retorna.** É procedimento: chame solto (`Plot(OBV);`), não dentro de expressão.
2. **Até 99 linhas por gráfico**, pela versão numerada: `Plot()`, `Plot2()`, `Plot3()` … `Plot99()`. Cada número é uma linha independente e mantém sua própria cor/legenda.
3. **`PlotN(plot, valor)` escreve numa linha específica** já existente — é assim que se plota condicionalmente sem criar linha nova.
4. **Cor é inteiro** (constante de cor da plataforma). Não passe string de cor.
5. **Função gráfica não decide nada na estratégia**: ela desenha. Se a lógica depende do valor, calcule numa variável antes de plotar.
6. **Padrão de candlestick é função booleana** — devolve verdadeiro/falso na barra, e o parâmetro de tendência/corpo muda o resultado. Leia a assinatura antes de usar.

## Assinaturas conferidas

```ntsl
Função PlotN(Plot: Integer; Valor: Float): Void;
Função PaintBar(Cor: Integer): Void;
Função HorizontalLine(Y: Float; Color: Integer): Void;
Função ConsoleLog(Content: String; Color: Integer): Void;
Função Alert(Color: Integer): Void;
```

## Funções cobertas

- Gráficas (37): AvgPrice, BarCount, ConsoleLog, CurrentBar, GetPlotColor, GetPlotWidth, GraphicInterval, GraphicOffset, HorizontalLine, HorizontalLineCustom, LastBarOnChart, Leader, LineSegment, MaxBarsBack, MaxBarsForward, MedianPrice, NoPlot, PaintBar, Funções Plot, PlotCandle, PlotN, PlotText, Range, RangeLeader, RGB, SetPlotColor, SetPlotStyle, SetPlotType, SetPlotWidth, TrueHigh, TrueLow, TrueRange, TrueRangeCustom, TypicalPrice, VerticalLine, VerticalLineCustom, WeightedClose
- Candlestick (8): C_3WhSolds_3BlkCrows, C_BullEng_BearEng, C_Doji, C_Hammer_HangingMan, C_MornDoji_EveDoji, C_MornStar_EveStar, C_PierceLine_DkCloud, C_ShootingStar

## Referências

- `refs/01-funcoes-graficas.md` — todas as funções gráficas, com parâmetros e exemplo
- `refs/02-candlestick.md` — padrões de vela
- `refs/03-exemplos.md` — exemplos de funcionamento

# 01 Funcoes Graficas

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções Gráficas

### Funções Gráficas
*Manual NTSL v4.7 (14/10/2026) — p. 205*

Funções Gráficas

19.1 Função AvgPrice

_A função AvgPrice() retorna o valor da média entre Abertura, Fechamento, Máxima e Mínima, de determinado candle._

**Sintaxe**

```ntsl
Função AvgPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** valor no gráfico.

```ntsl
No exemplo, a variável AvgPricePlot recebe o preço médio da barra atual com a função AvgPrice() e plota esse
var
AvgPricePlot : Float;
begin
AvgPricePlot := AvgPrice();
Plot(AvgPricePlot);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função BarCount() retorna a quantidade total de barras._

**Sintaxe**

```ntsl
Função BarCount(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, será pintado de azul (clBlue) a barra que está 10 posições antes da última no gráfico.
begin
if CurrentBar() = BarCount() - 10 then
PaintBar(clBlue);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função ConsoleLog() imprime um texto no terminal de console para ajudar na depuração do código._

**Sintaxe**

```ntsl
Função ConsoleLog(Content: String; Color: Integer): Void;
```

**Parâmetros**

Content: String; Texto que irá ser impresso no console de depuração.

Color: Integer [Opcional]; Cor do texto impresso.

**Exemplo de uso:** maior de 4%.

```ntsl
No exemplo abaixo, a função ConsoleLog() irá imprimir os dias e as variações do WDOFUT em que teve variação
begin
if Close[1] > Close * 1.04 then
ConsoleLog("Day: " + Date() + " Variation: " +
(Close[1] / Close - 1) * 100 + "%", clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função CurrentBar() tem como finalidade retornar ao usuário o índice do candle atual._

**Sintaxe**

```ntsl
Função CurrentBar(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, será pintado de azul (clBlue) a barra que está 10 posições antes da última no gráfico.
begin
if CurrentBar() = BarCount() - 10 then
PaintBar(clBlue);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função GetPlotColor possui como funcionalidade retornar o valor numérico da cor de determinado plot._

**Sintaxe**

```ntsl
Função GetPlotColor(PlotNum: Integer): Integer;
```

**Parâmetros**

PlotNum: Integer; Número do Plot para obter a cor.

**Exemplo de uso:** No exemplo, será aplicada a coloração do Plot 1 ao Plot 2.

```ntsl
begin
SetPlotColor(1,RGB(100,100,255));
SetPlotColor(2,GetPlotColor(1));
PlotN(1,close);
PlotN(2,Open);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função GetPlotWidth possui como finalidade retornar o valor da espessura de determinado plot._

**Sintaxe**

```ntsl
Função GetPlotWidth(PlotNum: Integer): Integer;
```

**Parâmetros**

PlotNum: Integer; Número do Plot para obter a espessura

**Exemplo de uso:** No exemplo, será aplicada a espessura do Plot 1 ao Plot 2.

```ntsl
begin
SetPlotWidth(1, 5);
SetPlotWidth(2, GetPlotWidth(1));
PlotN(1,close);
PlotN(2,Open);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função "GraphicInterval()" possui como finalidade retornar o intervalo do gráfico._

**Sintaxe**

```ntsl
Função GraphicInterval(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável gInterval o retorno da função.

```ntsl
var
gInterval : Integer;
begin
gInterval := GraphicInterval();
Plot(gInterval);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função GraphicOffset() possui como finalidade retornar o offset do gráfico._

**Sintaxe**

```ntsl
Função GraphicOffset(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável gOffset o retorno da função.

```ntsl
var
gOffset : Integer;
begin
gOffset := GraphicOffset();
Plot(gOffset);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função HorizontalLine tem como finalidade adicionar um estudo horizontal em um indicador. É possível exibir no máximo 99 linhas horizontais criadas por meio da função HorizontalLine simultaneamente no gráfico._

**Sintaxe**

```ntsl
Função HorizontalLine(Y: Float; Color: Integer): Void;
```

**Parâmetros**

Y: Float; Valor do estudo.

Color: Integer [Opcional]; Cor da linha.

**Exemplo de uso:** No exemplo abaixo, será adicionada uma linha vermelha, no nível 5288.

```ntsl
begin
HorizontalLine(5288, RGB(200, 0, 0));
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função HorizontalLineCustom tem como finalidade adicionar um estudo horizontal customizável em um indi- cador. É possível exibir no máximo 99 linhas horizontais criadas por meio da função HorizontalLineCustom simultaneamente no gráfico._

**Sintaxe**

```ntsl
Função HorizontalLineCustom(Price: Float; Color: Integer; LineWidth: Integer;

Style: Integer; Text: String; FontSize: Integer; TextPosition: Integer; StartDate

: Integer;

EndDate: Integer; PriceVariation: Float; StartTime: Integer; EndTime: Integer):

Void;
```

**Parâmetros**

Price: Float; Valor do estudo.

Color: Integer; Cor da linha.

LineWidth: Integer; Espessura da linha.

Style: Integer; Estilo da linha. Ver SetPlotStyle() para mais detalhes.

Text: String; Texto da linha.

FontSize: Integer [Opcional]; Tamanho da fonte.

TextPosition: Integer [Opcional]; Posição do texto na linha.

– tpTopLeft;

– tpTopRight;

– tpBottomLeft;

– tpBottomRight.

StartDate: Integer [Opcional]; Data inicial da linha.

EndDate: Integer [Opcional]; Data final da linha.

PriceVariation: Float [Opcional]; Variação de preço para preencher acima e abaixo da linha principal.

StartTime: Integer [Opcional]; Hora inicial da linha.

EndTime: Integer [Opcional]; Hora final da linha.

**Exemplo de uso:** No exemplo abaixo, será adicionada uma linha amarela, com espessura 3, estilo linha, com fonte de tamanho
10, texto no topo direito, do início ao fim do gráfico e com uma variação de 1000 no preço.

```ntsl
begin
HorizontalLineCustom(Close + 1000, clYellow, 3, 0, "Teste",
10, tpTopRight, 0, 0, 1000);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função LastBarOnChart retorna um valor Booleano indicando se o candle atual é o último candle do gráfico._

**Sintaxe**

```ntsl
Função LastBarOnChart(): Boolean;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo a seguir, o candle atual será identificado com a coloração amarela.

```ntsl
begin
if (LastBarOnChart) then
PaintBar(clYellow);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função Leader() retorna o valor 0 quando o ponto médio não for maior que a máxima do candle anterior e não for menor que a mínima, ou seja, quando estiver dentro do intervalo definido entre a mínima e a máxima. Quando o ponto médio for maior que a máxima ou menor que a mínima do candle anterior, a função retorna 1._

**Sintaxe**

```ntsl
Função Leader(): Integer;
```

**Parâmetros**

Não possui parâmetros.

```ntsl
No exemplo abaixo, caso a função Leader() seja igual a 1, o candle analisado será identificado pela cor verde.
begin
if (Leader() = 1) then
PaintBar(clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função LineSegment() desenha um segmento de reta no gráfico com base nos parâmetros fornecidos. A linha começa no ponto definido por PriceStart e DateStart e termina em PriceEnd e DateEnd. Se o parâmetro
Extrapolate estiver definido como verdadeiro, a linha será estendida além dos limites especificados, mantendo sua angulação original._

**Sintaxe**

```ntsl
Função LineSegment (PriceStart: Float; PriceEnd: Float; StartDate: Integer; EndDate

: Integer; Extrapolate: Boolean; Text: String; Color: Integer; LineWidth:
Integer; Style: Integer; FontSize: Integer; TextPosition: Integer; StartTime:
Integer; EndTime: Integer): Void;
```

**Parâmetros**

PriceStart: Float; Valor inicial da linha no eixo de preço.

PriceEnd: Float; Valor final da linha no eixo de preço.

StartDate: Integer; Data inicial da linha.

EndDate: Integer; Data final da linha.

Extrapolate: Boolean; Define se a linha deve ser extrapolada além dos limites definidos.

Text: String; Texto a ser exibido próximo à linha.

Color: Integer [Opcional]; Cor da linha.

LineWidth: Integer [Opcional]; Espessura da linha.

Style: Integer [Opcional]; Estilo da linha.

FontSize: Integer [Opcional]; Tamanho da fonte do texto.

TextPosition: Integer [Opcional]; Posição do texto.

StartTime: Integer [Opcional]; Hora de início (caso aplicável).

EndTime: Integer [Opcional]; Hora de término (caso aplicável).

**Exemplo de uso:** No exemplo abaixo, será desenhado um segmento de reta do valor 137.000 para 138.000, entre as datas 01/05 e 09/05, com extrapolação ativada e texto "Segmento".

```ntsl
begin
LineSegment(137000, 138000, 1250501, 1250509, true, "Segmento");
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função MaxBarsBack() tem como finalidade percorrer a lista da série, iniciando do primeiro candle criado (índice
0)._

**Sintaxe**

```ntsl
Função MaxBarsBack(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será aplicada uma coloração no segundo candle criado.

```ntsl
begin
if (MaxBarsBack() = 1) then
PaintBar(clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função MaxBarsForward() tem como finalidade percorrer a lista da série, iniciando do último candle criado (índice
0, candle atual)._

**Sintaxe**

```ntsl
Função MaxBarsForward(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será aplicada uma coloração no candle anterior ao atual.

```ntsl
begin
if (MaxBarsForward() = 1) then
PaintBar(clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função MedianPrice() retorna a média entre a máxima e a mínima de cada candle._

**Sintaxe**

```ntsl
Função MedianPrice(): Float;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** os candles serão destacados com a cor clGreen.

```ntsl
No exemplo a seguir, caso o valor da função MedianPrice() do candle atual seja maior que o do candle anterior,
begin
if ((MedianPrice() > MedianPrice(1))) then
PaintBar(clGreen);
Plot(MedianPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função NoPlot() tem como finalidade efetuar a remoção de determinado Plot._

**Sintaxe**

```ntsl
Função NoPlot(PlotNum: Integer): Void;
```

**Parâmetros**

PlotNum: Integer; Número do Plot (1, 2, 3 ou 4) a ser removido.

**Exemplo de uso:** Conforme o exemplo a seguir, será removida a linha referente ao Plot 1, e será exibida apenas a linha vinculada ao Plot 2.

```ntsl
begin
Plot(Close);
Plot2(Open);
NoPlot(1);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função PaintBar() permite a aplicação de colorações em indicadores ou candles._

**Sintaxe**

```ntsl
Função PaintBar(Cor: Integer): Void;
```

**Parâmetros**

Cor: Integer; Determina a coloração.

```ntsl
No exemplo, será aplicada a coloração verde quando o histograma de MACD() for maior que zero.
begin
if (MACD(23, 12, 9)|1| > 0) then
PaintBar(clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função Plot() realiza a ligação dos valores passados por parâmetro e cria gráficos de linhas.
É possível inserir até 99 linhas, utilizando a versão numerada da função: Plot(), Plot2(), Plot3() . . . Plot99()._

**Sintaxe**

```ntsl
Função Plot(Valor: Float): Void;
Função Plot2(Valor: Float): Void;
Função Plot3(Valor: Float): Void;
...
Função Plot99(Valor: Float): Void;
```

**Parâmetros**

Valor: Float; Pode-se utilizar variáveis, funções ou constantes para realizar o desenho do indicador.

**Exemplo de uso:** Conforme o exemplo a seguir, são plotados os dados de fechamento do dia anterior e a abertura do dia atual.

```ntsl
begin
Plot(CloseD(1));
Plot99(OpenD(0));
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função PlotCandle() plota um candle personalizado no gráfico, permitindo definir manualmente os valores de abertura, máxima, mínima e fechamento, além das cores do corpo e da borda._

**Sintaxe**

```ntsl
Função PlotCandle(Open: Float; High: Float; Low: Float; Close: Float;

ColorPositive: Integer; ColorLow: Integer; ColorBorder: Integer): Void;
```

**Parâmetros**

Open: Float; Valor de abertura do candle.

High: Float; Valor da máxima do candle.

Low: Float; Valor da mínima do candle.

Close: Float; Valor de fechamento do candle.

ColorPositive: Integer [Opcional]; Cor do corpo do candle positivo (quando Close > Open).

ColorLow: Integer[Opcional]; Cor do corpo do candle negativo (quando Close < Open).

ColorBorder: Integer[Opcional]; Cor da borda do candle.

**Exemplo de uso:** No exemplo abaixo, são desenhados candles personalizados com cores específicas para candles de alta e baixa.
As variáveis de abertura, máxima, mínima e fechamento são obtidas da série principal, e as cores são definidas conforme o tipo do candle.
vOpen,vHigh,vLow,vClose vPositivo ,vNegativo ,vBorda

```ntsl
var
: Float;
: Integer;
begin
vOpen := Open;
vHigh := High;
vLow := low;
vClose := Close;
vPositivo := ClGreen;
vNegativo := ClRed;
vBorda := clWhite;
PlotCandle(vOpen,vHigh,vLow,vClose ,vPositivo ,vNegativo ,vBorda);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função PlotN() assim como a Plot(), desenha o indicador conforme a série de dados informada, porém o número do plot deve ser determinado por parâmetro (entre 0 e 99)._

**Sintaxe**

```ntsl
Função PlotN(Plot: Integer; Valor: Float): Void;
```

**Parâmetros**

Plot: Integer; Número do plot, entre 0 e 99.

Valor: Float; Pode-se utilizar variáveis, funções ou constantes para realizar o desenho do indicador.

**Exemplo de uso:** No exemplo, são plotados os dados de fechamento do dia anterior e a abertura do dia atual.

```ntsl
begin
PlotN(0, CloseD(1));
PlotN(99, OpenD(0));
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função PlotText() possui como finalidade adicionar um texto a um indicador._

**Sintaxe**

```ntsl
Função PlotText(Content: String Color: Integer Position: Integer FontSize: Integer

Price: Float): Void;
```

**Parâmetros**

Content: String; Conteúdo do texto.

Color: Integer; Cor da fonte.

Position: Integer [Opcional]; Posição do texto:

– 0: Abaixo do candle.

– 1: Centralizado.

– 2: Acima do candle.

– 3: Posiciona no preço definido em dPrice.

FontSize: Integer [Opcional]; Tamanho da fonte do texto.

Price: Float [Opcional]; Quando utilizada Position = 3, será utilizado o valor de dPrice para posicionar o texto.

**Exemplo de uso:** No exemplo, será adicionado o texto "Close > M20" quando o fechamento anterior estiver acima da média exponencial de 20 períodos. Caso contrário, será exibido o texto "Close < M20".

```ntsl
begin
if (Close[1] < mediaExp(20, Close)[1]) and
(Close > mediaExp(20, Close)) then
PlotText("Close > M20!", clLime, 2, 6)
else if (Close[1] > mediaExp(20, Close)) and
(Close < mediaExp(20, Close)) then
PlotText("Close < M20!", clRed, 0, 6);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função Range() retorna a diferença entre a máxima e a mínima do candle._

**Sintaxe**

```ntsl
Função Range(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo, a variável nRange irá receber o valor retornado pela função Range().
var
nRange : Float;
begin
nRange := Range();
Plot(nRange);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função RangeLeader() compara o candle atual e anterior, analisando duas condições: se o ponto médio do candle atual é maior que a máxima anterior ou menor que a mínima anterior; se o intervalo do candle atual é maior que o intervalo da barra anterior. A função retornará 1 caso ambas as condições forem atendidas, mas retornará 0 caso nenhuma ou apenas uma das condições for atendida._

**Sintaxe**

```ntsl
Função RangeLeader(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo, a variável nRL irá receber o valor retornado pela função RangeLeader().
var
nRL : Float;
begin
nRL := RangeLeader();
Plot(nRL);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função RGB() permite ao usuário customizar cores, a partir da aplicação de intensidade dos parâmetros vermelho, verde e azul._

**Sintaxe**

```ntsl
Função RGB(Red: Integer; Green: Integer; Blue: Integer): Integer;
```

**Parâmetros**

Red: Integer; Intensidade da cor vermelha, variando de 0 a 255.

Green: Integer; Intensidade da cor verde, variando de 0 a 255.

Blue: Integer; Intensidade da cor azul, variando de 0 a 255.

```ntsl
No exemplo a seguir, será aplicada a coloração azul, conforme os parâmetros passados à função RGB().
begin
PaintBar(RGB(0, 0, 230));
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função SetPlotColor() possui como finalidade alterar a coloração de determinado Plot de 1 a 99._

**Sintaxe**

```ntsl
Função SetPlotColor(NumeroPlot: Integer; Cor: Integer): Void;
```

**Parâmetros**

NumeroPlot: Integer; Número do plot que terá a cor alterada:

– 1: Plot;
– 2: Plot2;
– 3: Plot3;
– 4: Plot4.

Cor: Integer; Determina a coloração. Pode ser uma constante de cor ou uma chamada à função RGB().

```ntsl
No exemplo abaixo, será alterada a coloração para vermelha referente à linha do Plot().
begin
Plot(Close);
SetPlotColor(1, clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A partir da função SetPlotStyle(), é possível alterar o estilo da linha de um plot específico._

**Sintaxe**

```ntsl
Função SetPlotStyle(Number: Integer; Style: Integer): Void;
```

**Parâmetros**

Number: Integer; Número do plot a ser modificado.

Style: Integer; Estilo da linha:

– 0: Contínua;

– 1: Tracejada (Traço longo);

– 2: Tracejada (Traço curto);

– 3: Tracejada (Traço longo e curto);

– 4: Tracejada (Traço longo e dois curtos).

**Exemplo de uso:** e o segundo, com traços curtos.

```ntsl
No exemplo abaixo, serão customizados os estilos dos plots: o primeiro terá linha tracejada com traços longos,
begin
Plot(OpenD(0));
Plot2(PriorCote(4));
SetPlotStyle(1, 1);
SetPlotStyle(2, 2);
SetPlotWidth(2, 2);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função SetPlotType() possui como finalidade alterar o tipo de gráfico de determinado plot._

**Sintaxe**

```ntsl
Função SetPlotType(Number: Integer; Type: Integer): Void;
```

**Parâmetros**

Number: Integer; Número do plot específico.

Type: Integer; Tipo de visualização:

– 0: Linha;

– 1: Histograma.

**Exemplo de uso:** No exemplo abaixo, será alterado o tipo do Plot 1 para histograma.

```ntsl
begin
PlotN(1, closeD(1));
SetPlotType(1, 1);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função SetPlotWidth() possui como finalidade alterar a espessura de determinado Plot (1 a 4)._

**Sintaxe**

```ntsl
Função SetPlotWidth(NumeroPlot: Integer; Espessura: Integer): Void;
```

**Parâmetros**

NumeroPlot: Integer; Número do plot a ser modificado:

– 1: Plot;
– 2: Plot2;
– 3: Plot3;
– 4: Plot4.

Espessura: Integer; Valor da nova espessura da linha.

**Exemplo de uso:** No exemplo abaixo, será alterada a espessura da linha do Plot 1 para 3.

```ntsl
begin
Plot(Close);
SetPlotWidth(1, 3);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função TrueHigh() retorna o maior valor entre o máximo da barra atual e o fechamento da barra anterior._

**Sintaxe**

```ntsl
Função TrueHigh(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TH receberá o valor retornado pela TrueHigh().
var
TH : Float;
begin
TH := TrueHigh();
Plot(TH);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função TrueLow() retorna o menor valor entre a mínima da barra atual e o fechamento da barra anterior._

**Sintaxe**

```ntsl
Função TrueLow(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TL receberá o valor retornado pela função TrueLow().
var
TL : Float;
begin
TL := TrueLow();
Plot(TL);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função TrueRange() retorna a diferença entre os valores de TrueHigh() e TrueLow()._

**Sintaxe**

```ntsl
Função TrueRange(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TR receberá o valor retornado pela função TrueRange().
var
TR : Float;
begin
TR := TrueRange();
Plot(TR);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função TrueRangeCustom() retorna o valor de TrueRange com base nos dados fornecidos pelo usuário._

**Sintaxe**

```ntsl
Função TrueRangeCustom(Maxima: Float; Minima: Float; Fechamento: Float): Float;
```

**Parâmetros**

Maxima: Float; Valor de máxima para o cálculo do indicador.

Minima: Float; Valor de mínima para o cálculo do indicador.

Fechamento: Float; Valor de fechamento de referência.

```ntsl
No exemplo abaixo, a variável TRC receberá o valor retornado pela função TrueRangeCustom().
var
TRC : Float;
begin
TRC := TrueRangeCustom(3763.5, 3761, 3761);
Plot(TRC);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função TypicalPrice() retorna a média aritmética entre os valores de máxima, mínima e fechamento do candle._

**Sintaxe**

```ntsl
Função TypicalPrice(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável aux receberá o valor retornado pela função TypicalPrice().
var
aux : Float;
begin
aux := TypicalPrice();
Plot(aux);
end
```

**Gráfico:** ver exemplo no manual, p. 205

_A função VerticalLine() adiciona uma linha vertical no gráfico, destacando um ponto específico no eixo do tempo._

**Sintaxe**

```ntsl
Função VerticalLine(Date: Integer; Color: Integer): Void;
```

**Parâmetros**

Date: Integer; Data no formato 1AAMMDD.

Color: Integer; Cor da linha.

**Exemplo de uso:** No exemplo abaixo, será inserida uma linha vertical amarela na data do dia anterior.

```ntsl
begin
VerticalLine(CurrentDate - 1, clYellow);
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função VerticalLineCustom() permite desenhar múltiplas linhas verticais com configurações personalizadas, como texto, estilo, espessura e região pintada._

**Sintaxe**

```ntsl
Função VerticalLineCustom (Color: Color; LineWidth: Integer; Style: Integer; Text:
String; FontSize: Integer; TextPosition: Integer; PriceTop: Float; PriceBottom:
Float; PaintRegion: Boolean):

Void;
```

**Parâmetros**

Color: Color; Cor da linha.

LineWidth: Integer; Espessura da linha.

Style: Integer; Estilo da linha. Ver SetPlotStyle() para mais detalhes.

Text: String; Texto exibido na linha.

FontSize: [Opcional] Integer; Tamanho da fonte do texto.

TextPosition: [Opcional] Integer; Posição do texto.

PriceTop: [Opcional] Float; Preço inicial da linha (se 0, começa do topo do gráfico).

PriceBottom: [Opcional] Float; Preço final da linha (se 0, vai até o fundo do gráfico).

PaintRegion: [Opcional] Boolean; Define se será pintada uma região até a próxima linha ou até o fim.

```ntsl
No exemplo abaixo, a função VerticalLineCustom(), será plotado uma linha vertical personalizada no gráfico.
begin
VerticalLineCustom(CLRED,1,1 ,"1234");
end;
```

**Gráfico:** ver exemplo no manual, p. 205

_A função WeightedClose() retorna a média entre o ponto médio da barra e dois fechamentos._

**Sintaxe**

```ntsl
Função WeightedClose(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável aux irá receber o valor retornado pela função WeightedClose().
var
aux : Float;
begin
aux := WeightedClose();
Plot(aux);
end;
```

### Função AvgPrice
*Manual NTSL v4.7 (14/10/2026) — p. 205*

19 Funções Gráficas

19.1 Função AvgPrice

_A função AvgPrice() retorna o valor da média entre Abertura, Fechamento, Máxima e Mínima, de determinado candle._

**Sintaxe**

```ntsl
Função AvgPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** valor no gráfico.

```ntsl
No exemplo, a variável AvgPricePlot recebe o preço médio da barra atual com a função AvgPrice() e plota esse
var
AvgPricePlot : Float;
begin
AvgPricePlot := AvgPrice();
Plot(AvgPricePlot);
end;
```

### Função BarCount
*Manual NTSL v4.7 (14/10/2026) — p. 206*

_A função BarCount() retorna a quantidade total de barras._

**Sintaxe**

```ntsl
Função BarCount(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, será pintado de azul (clBlue) a barra que está 10 posições antes da última no gráfico.
begin
if CurrentBar() = BarCount() - 10 then
PaintBar(clBlue);
end;
```

### Função ConsoleLog
*Manual NTSL v4.7 (14/10/2026) — p. 207*

_A função ConsoleLog() imprime um texto no terminal de console para ajudar na depuração do código._

**Sintaxe**

```ntsl
Função ConsoleLog(Content: String; Color: Integer): Void;
```

**Parâmetros**

Content: String; Texto que irá ser impresso no console de depuração.

Color: Integer [Opcional]; Cor do texto impresso.

**Exemplo de uso:** maior de 4%.

```ntsl
No exemplo abaixo, a função ConsoleLog() irá imprimir os dias e as variações do WDOFUT em que teve variação
begin
if Close[1] > Close * 1.04 then
ConsoleLog("Day: " + Date() + " Variation: " +
(Close[1] / Close - 1) * 100 + "%", clRed);
end;
```

### Função CurrentBar
*Manual NTSL v4.7 (14/10/2026) — p. 208*

_A função CurrentBar() tem como finalidade retornar ao usuário o índice do candle atual._

**Sintaxe**

```ntsl
Função CurrentBar(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, será pintado de azul (clBlue) a barra que está 10 posições antes da última no gráfico.
begin
if CurrentBar() = BarCount() - 10 then
PaintBar(clBlue);
end;
```

### Função GetPlotColor
*Manual NTSL v4.7 (14/10/2026) — p. 209*

_A função GetPlotColor possui como funcionalidade retornar o valor numérico da cor de determinado plot._

**Sintaxe**

```ntsl
Função GetPlotColor(PlotNum: Integer): Integer;
```

**Parâmetros**

PlotNum: Integer; Número do Plot para obter a cor.

**Exemplo de uso:** No exemplo, será aplicada a coloração do Plot 1 ao Plot 2.

```ntsl
begin
SetPlotColor(1,RGB(100,100,255));
SetPlotColor(2,GetPlotColor(1));
PlotN(1,close);
PlotN(2,Open);
end;
```

### Função GetPlotWidth
*Manual NTSL v4.7 (14/10/2026) — p. 210*

_A função GetPlotWidth possui como finalidade retornar o valor da espessura de determinado plot._

**Sintaxe**

```ntsl
Função GetPlotWidth(PlotNum: Integer): Integer;
```

**Parâmetros**

PlotNum: Integer; Número do Plot para obter a espessura

**Exemplo de uso:** No exemplo, será aplicada a espessura do Plot 1 ao Plot 2.

```ntsl
begin
SetPlotWidth(1, 5);
SetPlotWidth(2, GetPlotWidth(1));
PlotN(1,close);
PlotN(2,Open);
end;
```

### Função GraphicInterval
*Manual NTSL v4.7 (14/10/2026) — p. 211*

_A função "GraphicInterval()" possui como finalidade retornar o intervalo do gráfico._

**Sintaxe**

```ntsl
Função GraphicInterval(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável gInterval o retorno da função.

```ntsl
var
gInterval : Integer;
begin
gInterval := GraphicInterval();
Plot(gInterval);
end;
```

### Função GraphicOffset
*Manual NTSL v4.7 (14/10/2026) — p. 212*

_A função GraphicOffset() possui como finalidade retornar o offset do gráfico._

**Sintaxe**

```ntsl
Função GraphicOffset(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável gOffset o retorno da função.

```ntsl
var
gOffset : Integer;
begin
gOffset := GraphicOffset();
Plot(gOffset);
end;
```

### Função HorizontalLine
*Manual NTSL v4.7 (14/10/2026) — p. 213*

_A função HorizontalLine tem como finalidade adicionar um estudo horizontal em um indicador. É possível exibir no máximo 99 linhas horizontais criadas por meio da função HorizontalLine simultaneamente no gráfico._

**Sintaxe**

```ntsl
Função HorizontalLine(Y: Float; Color: Integer): Void;
```

**Parâmetros**

Y: Float; Valor do estudo.

Color: Integer [Opcional]; Cor da linha.

**Exemplo de uso:** No exemplo abaixo, será adicionada uma linha vermelha, no nível 5288.

```ntsl
begin
HorizontalLine(5288, RGB(200, 0, 0));
end;
```

### Função HorizontalLineCustom
*Manual NTSL v4.7 (14/10/2026) — p. 214*

_A função HorizontalLineCustom tem como finalidade adicionar um estudo horizontal customizável em um indi- cador. É possível exibir no máximo 99 linhas horizontais criadas por meio da função HorizontalLineCustom simultaneamente no gráfico._

**Sintaxe**

```ntsl
Função HorizontalLineCustom(Price: Float; Color: Integer; LineWidth: Integer;

Style: Integer; Text: String; FontSize: Integer; TextPosition: Integer; StartDate

: Integer;

EndDate: Integer; PriceVariation: Float; StartTime: Integer; EndTime: Integer):

Void;
```

**Parâmetros**

Price: Float; Valor do estudo.

Color: Integer; Cor da linha.

LineWidth: Integer; Espessura da linha.

Style: Integer; Estilo da linha. Ver SetPlotStyle() para mais detalhes.

Text: String; Texto da linha.

FontSize: Integer [Opcional]; Tamanho da fonte.

TextPosition: Integer [Opcional]; Posição do texto na linha.

– tpTopLeft;

– tpTopRight;

– tpBottomLeft;

– tpBottomRight.

StartDate: Integer [Opcional]; Data inicial da linha.

EndDate: Integer [Opcional]; Data final da linha.

PriceVariation: Float [Opcional]; Variação de preço para preencher acima e abaixo da linha principal.

StartTime: Integer [Opcional]; Hora inicial da linha.

EndTime: Integer [Opcional]; Hora final da linha.

**Exemplo de uso:** No exemplo abaixo, será adicionada uma linha amarela, com espessura 3, estilo linha, com fonte de tamanho
10, texto no topo direito, do início ao fim do gráfico e com uma variação de 1000 no preço.

```ntsl
begin
HorizontalLineCustom(Close + 1000, clYellow, 3, 0, "Teste",
10, tpTopRight, 0, 0, 1000);
end;
```

### Função LastBarOnChart
*Manual NTSL v4.7 (14/10/2026) — p. 216*

_A função LastBarOnChart retorna um valor Booleano indicando se o candle atual é o último candle do gráfico._

**Sintaxe**

```ntsl
Função LastBarOnChart(): Boolean;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo a seguir, o candle atual será identificado com a coloração amarela.

```ntsl
begin
if (LastBarOnChart) then
PaintBar(clYellow);
end;
```

### Função Leader
*Manual NTSL v4.7 (14/10/2026) — p. 217*

_A função Leader() retorna o valor 0 quando o ponto médio não for maior que a máxima do candle anterior e não for menor que a mínima, ou seja, quando estiver dentro do intervalo definido entre a mínima e a máxima. Quando o ponto médio for maior que a máxima ou menor que a mínima do candle anterior, a função retorna 1._

**Sintaxe**

```ntsl
Função Leader(): Integer;
```

**Parâmetros**

Não possui parâmetros.

```ntsl
No exemplo abaixo, caso a função Leader() seja igual a 1, o candle analisado será identificado pela cor verde.
begin
if (Leader() = 1) then
PaintBar(clGreen);
end;
```

### Função LineSegment
*Manual NTSL v4.7 (14/10/2026) — p. 218*

_A função LineSegment() desenha um segmento de reta no gráfico com base nos parâmetros fornecidos. A linha começa no ponto definido por PriceStart e DateStart e termina em PriceEnd e DateEnd. Se o parâmetro
Extrapolate estiver definido como verdadeiro, a linha será estendida além dos limites especificados, mantendo sua angulação original._

**Sintaxe**

```ntsl
Função LineSegment (PriceStart: Float; PriceEnd: Float; StartDate: Integer; EndDate

: Integer; Extrapolate: Boolean; Text: String; Color: Integer; LineWidth:
Integer; Style: Integer; FontSize: Integer; TextPosition: Integer; StartTime:
Integer; EndTime: Integer): Void;
```

**Parâmetros**

PriceStart: Float; Valor inicial da linha no eixo de preço.

PriceEnd: Float; Valor final da linha no eixo de preço.

StartDate: Integer; Data inicial da linha.

EndDate: Integer; Data final da linha.

Extrapolate: Boolean; Define se a linha deve ser extrapolada além dos limites definidos.

Text: String; Texto a ser exibido próximo à linha.

Color: Integer [Opcional]; Cor da linha.

LineWidth: Integer [Opcional]; Espessura da linha.

Style: Integer [Opcional]; Estilo da linha.

FontSize: Integer [Opcional]; Tamanho da fonte do texto.

TextPosition: Integer [Opcional]; Posição do texto.

StartTime: Integer [Opcional]; Hora de início (caso aplicável).

EndTime: Integer [Opcional]; Hora de término (caso aplicável).

**Exemplo de uso:** No exemplo abaixo, será desenhado um segmento de reta do valor 137.000 para 138.000, entre as datas 01/05 e 09/05, com extrapolação ativada e texto "Segmento".

```ntsl
begin
LineSegment(137000, 138000, 1250501, 1250509, true, "Segmento");
end;
```

### Função MaxBarsBack
*Manual NTSL v4.7 (14/10/2026) — p. 220*

_A função MaxBarsBack() tem como finalidade percorrer a lista da série, iniciando do primeiro candle criado (índice
0)._

**Sintaxe**

```ntsl
Função MaxBarsBack(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será aplicada uma coloração no segundo candle criado.

```ntsl
begin
if (MaxBarsBack() = 1) then
PaintBar(clGreen);
end;
```

### Função MaxBarsForward
*Manual NTSL v4.7 (14/10/2026) — p. 221*

_A função MaxBarsForward() tem como finalidade percorrer a lista da série, iniciando do último candle criado (índice
0, candle atual)._

**Sintaxe**

```ntsl
Função MaxBarsForward(): Integer;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** No exemplo, será aplicada uma coloração no candle anterior ao atual.

```ntsl
begin
if (MaxBarsForward() = 1) then
PaintBar(clGreen);
end;
```

### Função MedianPrice
*Manual NTSL v4.7 (14/10/2026) — p. 222*

_A função MedianPrice() retorna a média entre a máxima e a mínima de cada candle._

**Sintaxe**

```ntsl
Função MedianPrice(): Float;
```

**Parâmetros**

Não possui parâmetros.

**Exemplo de uso:** os candles serão destacados com a cor clGreen.

```ntsl
No exemplo a seguir, caso o valor da função MedianPrice() do candle atual seja maior que o do candle anterior,
begin
if ((MedianPrice() > MedianPrice(1))) then
PaintBar(clGreen);
Plot(MedianPrice);
end;
```

### Função NoPlot
*Manual NTSL v4.7 (14/10/2026) — p. 223*

_A função NoPlot() tem como finalidade efetuar a remoção de determinado Plot._

**Sintaxe**

```ntsl
Função NoPlot(PlotNum: Integer): Void;
```

**Parâmetros**

PlotNum: Integer; Número do Plot (1, 2, 3 ou 4) a ser removido.

**Exemplo de uso:** Conforme o exemplo a seguir, será removida a linha referente ao Plot 1, e será exibida apenas a linha vinculada ao Plot 2.

```ntsl
begin
Plot(Close);
Plot2(Open);
NoPlot(1);
end;
```

### Função PaintBar
*Manual NTSL v4.7 (14/10/2026) — p. 224*

_A função PaintBar() permite a aplicação de colorações em indicadores ou candles._

**Sintaxe**

```ntsl
Função PaintBar(Cor: Integer): Void;
```

**Parâmetros**

Cor: Integer; Determina a coloração.

```ntsl
No exemplo, será aplicada a coloração verde quando o histograma de MACD() for maior que zero.
begin
if (MACD(23, 12, 9)|1| > 0) then
PaintBar(clGreen);
end;
```

### Funções Plot
*Manual NTSL v4.7 (14/10/2026) — p. 225*

_A função Plot() realiza a ligação dos valores passados por parâmetro e cria gráficos de linhas.
É possível inserir até 99 linhas, utilizando a versão numerada da função: Plot(), Plot2(), Plot3() . . . Plot99()._

**Sintaxe**

```ntsl
Função Plot(Valor: Float): Void;
Função Plot2(Valor: Float): Void;
Função Plot3(Valor: Float): Void;
...
Função Plot99(Valor: Float): Void;
```

**Parâmetros**

Valor: Float; Pode-se utilizar variáveis, funções ou constantes para realizar o desenho do indicador.

**Exemplo de uso:** Conforme o exemplo a seguir, são plotados os dados de fechamento do dia anterior e a abertura do dia atual.

```ntsl
begin
Plot(CloseD(1));
Plot99(OpenD(0));
end;
```

### Função PlotCandle
*Manual NTSL v4.7 (14/10/2026) — p. 226*

_A função PlotCandle() plota um candle personalizado no gráfico, permitindo definir manualmente os valores de abertura, máxima, mínima e fechamento, além das cores do corpo e da borda._

**Sintaxe**

```ntsl
Função PlotCandle(Open: Float; High: Float; Low: Float; Close: Float;

ColorPositive: Integer; ColorLow: Integer; ColorBorder: Integer): Void;
```

**Parâmetros**

Open: Float; Valor de abertura do candle.

High: Float; Valor da máxima do candle.

Low: Float; Valor da mínima do candle.

Close: Float; Valor de fechamento do candle.

ColorPositive: Integer [Opcional]; Cor do corpo do candle positivo (quando Close > Open).

ColorLow: Integer[Opcional]; Cor do corpo do candle negativo (quando Close < Open).

ColorBorder: Integer[Opcional]; Cor da borda do candle.

**Exemplo de uso:** No exemplo abaixo, são desenhados candles personalizados com cores específicas para candles de alta e baixa.
As variáveis de abertura, máxima, mínima e fechamento são obtidas da série principal, e as cores são definidas conforme o tipo do candle.
vOpen,vHigh,vLow,vClose vPositivo ,vNegativo ,vBorda

```ntsl
var
: Float;
: Integer;
begin
vOpen := Open;
vHigh := High;
vLow := low;
vClose := Close;
vPositivo := ClGreen;
vNegativo := ClRed;
vBorda := clWhite;
PlotCandle(vOpen,vHigh,vLow,vClose ,vPositivo ,vNegativo ,vBorda);
end;
```

### Função PlotN
*Manual NTSL v4.7 (14/10/2026) — p. 228*

_A função PlotN() assim como a Plot(), desenha o indicador conforme a série de dados informada, porém o número do plot deve ser determinado por parâmetro (entre 0 e 99)._

**Sintaxe**

```ntsl
Função PlotN(Plot: Integer; Valor: Float): Void;
```

**Parâmetros**

Plot: Integer; Número do plot, entre 0 e 99.

Valor: Float; Pode-se utilizar variáveis, funções ou constantes para realizar o desenho do indicador.

**Exemplo de uso:** No exemplo, são plotados os dados de fechamento do dia anterior e a abertura do dia atual.

```ntsl
begin
PlotN(0, CloseD(1));
PlotN(99, OpenD(0));
end;
```

### Função PlotText
*Manual NTSL v4.7 (14/10/2026) — p. 229*

_A função PlotText() possui como finalidade adicionar um texto a um indicador._

**Sintaxe**

```ntsl
Função PlotText(Content: String Color: Integer Position: Integer FontSize: Integer

Price: Float): Void;
```

**Parâmetros**

Content: String; Conteúdo do texto.

Color: Integer; Cor da fonte.

Position: Integer [Opcional]; Posição do texto:

– 0: Abaixo do candle.

– 1: Centralizado.

– 2: Acima do candle.

– 3: Posiciona no preço definido em dPrice.

FontSize: Integer [Opcional]; Tamanho da fonte do texto.

Price: Float [Opcional]; Quando utilizada Position = 3, será utilizado o valor de dPrice para posicionar o texto.

**Exemplo de uso:** No exemplo, será adicionado o texto "Close > M20" quando o fechamento anterior estiver acima da média exponencial de 20 períodos. Caso contrário, será exibido o texto "Close < M20".

```ntsl
begin
if (Close[1] < mediaExp(20, Close)[1]) and
(Close > mediaExp(20, Close)) then
PlotText("Close > M20!", clLime, 2, 6)
else if (Close[1] > mediaExp(20, Close)) and
(Close < mediaExp(20, Close)) then
PlotText("Close < M20!", clRed, 0, 6);
end;
```

### Função Range
*Manual NTSL v4.7 (14/10/2026) — p. 231*

_A função Range() retorna a diferença entre a máxima e a mínima do candle._

**Sintaxe**

```ntsl
Função Range(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo, a variável nRange irá receber o valor retornado pela função Range().
var
nRange : Float;
begin
nRange := Range();
Plot(nRange);
end;
```

### Função RangeLeader
*Manual NTSL v4.7 (14/10/2026) — p. 232*

_A função RangeLeader() compara o candle atual e anterior, analisando duas condições: se o ponto médio do candle atual é maior que a máxima anterior ou menor que a mínima anterior; se o intervalo do candle atual é maior que o intervalo da barra anterior. A função retornará 1 caso ambas as condições forem atendidas, mas retornará 0 caso nenhuma ou apenas uma das condições for atendida._

**Sintaxe**

```ntsl
Função RangeLeader(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo, a variável nRL irá receber o valor retornado pela função RangeLeader().
var
nRL : Float;
begin
nRL := RangeLeader();
Plot(nRL);
end;
```

### Função RGB
*Manual NTSL v4.7 (14/10/2026) — p. 233*

_A função RGB() permite ao usuário customizar cores, a partir da aplicação de intensidade dos parâmetros vermelho, verde e azul._

**Sintaxe**

```ntsl
Função RGB(Red: Integer; Green: Integer; Blue: Integer): Integer;
```

**Parâmetros**

Red: Integer; Intensidade da cor vermelha, variando de 0 a 255.

Green: Integer; Intensidade da cor verde, variando de 0 a 255.

Blue: Integer; Intensidade da cor azul, variando de 0 a 255.

```ntsl
No exemplo a seguir, será aplicada a coloração azul, conforme os parâmetros passados à função RGB().
begin
PaintBar(RGB(0, 0, 230));
end;
```

### Função SetPlotColor
*Manual NTSL v4.7 (14/10/2026) — p. 234*

_A função SetPlotColor() possui como finalidade alterar a coloração de determinado Plot de 1 a 99._

**Sintaxe**

```ntsl
Função SetPlotColor(NumeroPlot: Integer; Cor: Integer): Void;
```

**Parâmetros**

NumeroPlot: Integer; Número do plot que terá a cor alterada:

– 1: Plot;
– 2: Plot2;
– 3: Plot3;
– 4: Plot4.

Cor: Integer; Determina a coloração. Pode ser uma constante de cor ou uma chamada à função RGB().

```ntsl
No exemplo abaixo, será alterada a coloração para vermelha referente à linha do Plot().
begin
Plot(Close);
SetPlotColor(1, clRed);
end;
```

### Função SetPlotStyle
*Manual NTSL v4.7 (14/10/2026) — p. 235*

_A partir da função SetPlotStyle(), é possível alterar o estilo da linha de um plot específico._

**Sintaxe**

```ntsl
Função SetPlotStyle(Number: Integer; Style: Integer): Void;
```

**Parâmetros**

Number: Integer; Número do plot a ser modificado.

Style: Integer; Estilo da linha:

– 0: Contínua;

– 1: Tracejada (Traço longo);

– 2: Tracejada (Traço curto);

– 3: Tracejada (Traço longo e curto);

– 4: Tracejada (Traço longo e dois curtos).

**Exemplo de uso:** e o segundo, com traços curtos.

```ntsl
No exemplo abaixo, serão customizados os estilos dos plots: o primeiro terá linha tracejada com traços longos,
begin
Plot(OpenD(0));
Plot2(PriorCote(4));
SetPlotStyle(1, 1);
SetPlotStyle(2, 2);
SetPlotWidth(2, 2);
end;
```

### Função SetPlotType
*Manual NTSL v4.7 (14/10/2026) — p. 237*

_A função SetPlotType() possui como finalidade alterar o tipo de gráfico de determinado plot._

**Sintaxe**

```ntsl
Função SetPlotType(Number: Integer; Type: Integer): Void;
```

**Parâmetros**

Number: Integer; Número do plot específico.

Type: Integer; Tipo de visualização:

– 0: Linha;

– 1: Histograma.

**Exemplo de uso:** No exemplo abaixo, será alterado o tipo do Plot 1 para histograma.

```ntsl
begin
PlotN(1, closeD(1));
SetPlotType(1, 1);
end;
```

### Função SetPlotWidth
*Manual NTSL v4.7 (14/10/2026) — p. 238*

_A função SetPlotWidth() possui como finalidade alterar a espessura de determinado Plot (1 a 4)._

**Sintaxe**

```ntsl
Função SetPlotWidth(NumeroPlot: Integer; Espessura: Integer): Void;
```

**Parâmetros**

NumeroPlot: Integer; Número do plot a ser modificado:

– 1: Plot;
– 2: Plot2;
– 3: Plot3;
– 4: Plot4.

Espessura: Integer; Valor da nova espessura da linha.

**Exemplo de uso:** No exemplo abaixo, será alterada a espessura da linha do Plot 1 para 3.

```ntsl
begin
Plot(Close);
SetPlotWidth(1, 3);
end;
```

### Função TrueHigh
*Manual NTSL v4.7 (14/10/2026) — p. 239*

_A função TrueHigh() retorna o maior valor entre o máximo da barra atual e o fechamento da barra anterior._

**Sintaxe**

```ntsl
Função TrueHigh(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TH receberá o valor retornado pela TrueHigh().
var
TH : Float;
begin
TH := TrueHigh();
Plot(TH);
end;
```

### Função TrueLow
*Manual NTSL v4.7 (14/10/2026) — p. 240*

_A função TrueLow() retorna o menor valor entre a mínima da barra atual e o fechamento da barra anterior._

**Sintaxe**

```ntsl
Função TrueLow(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TL receberá o valor retornado pela função TrueLow().
var
TL : Float;
begin
TL := TrueLow();
Plot(TL);
end;
```

### Função TrueRange
*Manual NTSL v4.7 (14/10/2026) — p. 241*

_A função TrueRange() retorna a diferença entre os valores de TrueHigh() e TrueLow()._

**Sintaxe**

```ntsl
Função TrueRange(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável TR receberá o valor retornado pela função TrueRange().
var
TR : Float;
begin
TR := TrueRange();
Plot(TR);
end;
```

### Função TrueRangeCustom
*Manual NTSL v4.7 (14/10/2026) — p. 242*

_A função TrueRangeCustom() retorna o valor de TrueRange com base nos dados fornecidos pelo usuário._

**Sintaxe**

```ntsl
Função TrueRangeCustom(Maxima: Float; Minima: Float; Fechamento: Float): Float;
```

**Parâmetros**

Maxima: Float; Valor de máxima para o cálculo do indicador.

Minima: Float; Valor de mínima para o cálculo do indicador.

Fechamento: Float; Valor de fechamento de referência.

```ntsl
No exemplo abaixo, a variável TRC receberá o valor retornado pela função TrueRangeCustom().
var
TRC : Float;
begin
TRC := TrueRangeCustom(3763.5, 3761, 3761);
Plot(TRC);
end;
```

### Função TypicalPrice
*Manual NTSL v4.7 (14/10/2026) — p. 243*

_A função TypicalPrice() retorna a média aritmética entre os valores de máxima, mínima e fechamento do candle._

**Sintaxe**

```ntsl
Função TypicalPrice(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável aux receberá o valor retornado pela função TypicalPrice().
var
aux : Float;
begin
aux := TypicalPrice();
Plot(aux);
end
```

### Função VerticalLine
*Manual NTSL v4.7 (14/10/2026) — p. 244*

_A função VerticalLine() adiciona uma linha vertical no gráfico, destacando um ponto específico no eixo do tempo._

**Sintaxe**

```ntsl
Função VerticalLine(Date: Integer; Color: Integer): Void;
```

**Parâmetros**

Date: Integer; Data no formato 1AAMMDD.

Color: Integer; Cor da linha.

**Exemplo de uso:** No exemplo abaixo, será inserida uma linha vertical amarela na data do dia anterior.

```ntsl
begin
VerticalLine(CurrentDate - 1, clYellow);
end;
```

### Função VerticalLineCustom
*Manual NTSL v4.7 (14/10/2026) — p. 245*

_A função VerticalLineCustom() permite desenhar múltiplas linhas verticais com configurações personalizadas, como texto, estilo, espessura e região pintada._

**Sintaxe**

```ntsl
Função VerticalLineCustom (Color: Color; LineWidth: Integer; Style: Integer; Text:
String; FontSize: Integer; TextPosition: Integer; PriceTop: Float; PriceBottom:
Float; PaintRegion: Boolean):

Void;
```

**Parâmetros**

Color: Color; Cor da linha.

LineWidth: Integer; Espessura da linha.

Style: Integer; Estilo da linha. Ver SetPlotStyle() para mais detalhes.

Text: String; Texto exibido na linha.

FontSize: [Opcional] Integer; Tamanho da fonte do texto.

TextPosition: [Opcional] Integer; Posição do texto.

PriceTop: [Opcional] Float; Preço inicial da linha (se 0, começa do topo do gráfico).

PriceBottom: [Opcional] Float; Preço final da linha (se 0, vai até o fundo do gráfico).

PaintRegion: [Opcional] Boolean; Define se será pintada uma região até a próxima linha ou até o fim.

```ntsl
No exemplo abaixo, a função VerticalLineCustom(), será plotado uma linha vertical personalizada no gráfico.
begin
VerticalLineCustom(CLRED,1,1 ,"1234");
end;
```

### Função WeightedClose
*Manual NTSL v4.7 (14/10/2026) — p. 247*

_A função WeightedClose() retorna a média entre o ponto médio da barra e dois fechamentos._

**Sintaxe**

```ntsl
Função WeightedClose(): Float;
```

**Parâmetros**

Nenhum parâmetro.

```ntsl
No exemplo abaixo, a variável aux irá receber o valor retornado pela função WeightedClose().
var
aux : Float;
begin
aux := WeightedClose();
Plot(aux);
end;
```

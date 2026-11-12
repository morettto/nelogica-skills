# 02 Funcoes De Usuario

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Usuário

### Funções de Usuário
*Manual NTSL v4.7 (14/10/2026) — p. 542*

Funções de Usuário

25.1 Função Cum

_A função Cum() acumula o valor de uma série de dados, desde a primeira barra até a atual._

**Sintaxe**

```ntsl
Função Cum(SerieDeDados: Serie): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série para efetuar o somatório.

**Exemplo de uso:** No exemplo, será atribuído à variável aux o somatório da diferença entre as séries Close e Open.

```ntsl
var
aux : Float;
begin
aux := Cum(Close - Open);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função FastKCustom() retorna o valor de FastK do Oscilador Estocástico, de acordo com os preços determinados por parâmetro, e período desejado._

**Sintaxe**

```ntsl
Função FastKCustom(PriceH: Serie; PriceL: Serie; PriceC: Serie; Período: Serie):

Float;
```

**Parâmetros**

PriceH: Serie; Série de referência para a máxima.

PriceL: Serie; Série de referência para a mínima.

PriceC: Serie; Série de referência para o fechamento.

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo, será atribuído à variável kCustom o retorno da função FastKCustom, considerando as séries de

```ntsl
máxima(PriceH), mínima(PriceL), fechamento(PriceC), e 14 períodos para o cálculo.
var
kCustom : Float;
begin
kCustom := FastKCustom(High, Low, Close, 14);
Plot(kCustom);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função HarmonicMean() calcula a média harmônica de uma série de dados, baseada em um determinado período._

**Sintaxe**

```ntsl
Função HarmonicMean(SerieDeDados: Serie Período: Integer;): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Período: Float; Período utilizado no momento do cálculo.

```ntsl
No exemplo a seguir, será atribuído à variável aux o retorno da função HarmonicMean(), considerando a máxima
(Close) e 20 (Períodos) para o cálculo.
var
aux : Float;
begin
aux := HarmonicMean(High, 20);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função Highest() tem como funcionalidade retornar ao usuário o maior valor da série estipulada por ele, dentro de um período determinado._

**Sintaxe**

```ntsl
Função Highest(SerieDeDados: Serie; Período: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser a abertura, máxima, mínima, fechamento, ou até mesmo indicadores.

Período: Float; Determina o período que será considerado para a pesquisa.

```ntsl
No exemplo abaixo, usamos a função Highest() para retornar a maior abertura dentro de 9 períodos.
begin
if not HasPosition then
Plot(Highest(Open, 9));
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função HighestBar() tem como funcionalidade retornar o índice do maior valor da série especificada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função HighestBar(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, como abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

**Exemplo de uso:** utilizando a série de abertura.

```ntsl
No exemplo abaixo, usamos a função HighestBar() para retornar o índice da maior mínima dentro de 9 períodos,
var
mMinima : Float;
begin
mMinima := HighestBar(Open, 9);
Plot(mMinima);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função Lowest() tem como funcionalidade retornar o menor valor da série estipulada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função Lowest(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

```ntsl
No exemplo abaixo, usamos a função Lowest() para retornar o menor fechamento dentro de 50 períodos.
var
low : Float;
begin
low := Lowest(Close, 50);
Plot(low);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função LowestBar() tem como funcionalidade retornar o índice do menor valor da série estipulada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função LowestBar(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

**Exemplo de uso:** períodos, utilizando a série Low.

```ntsl
No exemplo abaixo, usamos a função LowestBar() para retornar o índice da menor mínima dentro de 26
var
lowB : Float;
begin
lowB := LowestBar(Close, 26);
Plot(lowB);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função Media() retorna o valor do indicador Média Móvel, tipo aritmética. o exemplo com o código fonte está_

**Sintaxe**

```ntsl
Função Media(Periodo: Integer; TipoSerie: Serie): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

Dados: TipoSerie; Série que será considerada para o cálculo.

```ntsl
No exemplo, será atribuído à variável vMed o valor do indicador Média Móvel (Aritmética), considerando 100
períodos, e a série de fechamento (Close) para o cálculo.
var
vMed : Float;
begin
vMed := Media;
Plot(Media(100, Close));
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função MediaExp() retorna o valor do indicador Média Móvel, tipo exponencial.
O indicador Média Móvel calcula a média dos dados entre a cotação atual e um período anterior.
O código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função MediaExp(Periodo: Integer; Dados: Serie): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

Dados: Serie; Série que será considerada para o cálculo.

**Exemplo de uso:** de fechamento "Close". O cálculo considera um período de "100" unidades. O valor retornado pela função é então plotado no gráfico.

```ntsl
No exemplo abaixo, a função MediaExp() é utilizada para calcular a média móvel exponencial da série de preços
var
AvgPeriod : Integer;
begin
AvgPeriod := 100;
Plot(MediaExp(AvgPeriod ,Close));
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função MidPoint() retorna a média entre o maior e o menor valor encontrados no período._

**Sintaxe**

```ntsl
Função MidPoint(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série de referência.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** Close e 15 períodos como base.

```ntsl
No exemplo abaixo, a variável midP irá receber o valor retornado pela função MidPoint(), utilizando a série
var
midP : Float;
begin
midP := MidPoint(Close, 15);
Plot(midP);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função PercentChange() calcula a alteração percentual no preço do candle atual em relação a um determinado deslocamento anterior._

**Sintaxe**

```ntsl
Função PercentChange(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série base de referência.

Periodo: Integer; Período anterior para a comparação com o dado da série atual.

**Exemplo de uso:** e 2 períodos para a comparação.

```ntsl
No exemplo abaixo, será atribuído à variável pc o retorno da função PercentChange(), utilizando a série Close
var
pc : Float;
begin
pc := PercentChange(Close, 2);
Plot(pc);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função PriceOscillator() retorna o valor do indicador PriceOscillator, de acordo com os parâmetros deseja- dos._

**Sintaxe**

```ntsl
Função PriceOscillator(SerieDados: Serie; ComprimentoRapido: Integer;

ComprimentoLento: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo do indicador.

ComprimentoRapido: Integer; Referente ao parâmetro FastLength.

ComprimentoLento: Integer; Referente ao parâmetro SlowLength.

**Exemplo de uso:** High, com comprimento rápido igual a 9 e comprimento lento igual a 18.

```ntsl
No exemplo abaixo, a variável pOsc irá receber o valor do indicador PriceOscillator(), considerando a série
var
pOsc : Float;
begin
pOsc := PriceOscillator(High, 9, 18);
Plot(pOsc);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função RateOfChange() retorna a variação percentual de uma série de dados em relação a um valor anterior definido._

**Sintaxe**

```ntsl
Função RateOfChange(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série base de referência.

Periodo: Integer; Índice do dado utilizado na comparação com o valor atual da série.

```ntsl
No exemplo abaixo, será atribuído à variável rc o valor retornado pela função RateOfChange(), utilizando a
série High e o candle anterior (1) como base de comparação.
var
rc : Float;
begin
rc := RateOfChange(High, 1);
Plot(rc);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função SlowD() retorna o valor da linha %D do Estocástico Lento, calculada a partir da média móvel dos valores de SlowK, para o período especificado._

**Sintaxe**

```ntsl
Função SlowD(Periodo: Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** cálculo.

```ntsl
No exemplo abaixo, a variável sd irá receber o valor do indicador SlowD(), considerando 14 períodos para o
var
sd : Float;
begin
sd := SlowD(14);
Plot(sd);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função StdDevs() retorna o desvio padrão de uma série de dados, em um determinado período._

**Sintaxe**

```ntsl
Função StdDevs(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo abaixo, a variável sd irá receber o retorno da função StdDevs(), considerando a série Close e 20
var
sd : Float;
begin
sd := StdDevs(Close, 20);
Plot(sd);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função Summation() efetua o somatório dos valores de uma série de dados em um determinado número de barras._

**Sintaxe**

```ntsl
Função Summation(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos.

```ntsl
No exemplo abaixo, a variável s irá receber o retorno da função Summation(), considerando a série Close e 10
var
s : Float;
begin
s := Summation(Close, 10);
Plot(s);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função TriAverage() efetua a média triangular de uma série de dados, dentro de um determinado período._

**Sintaxe**

```ntsl
Função TriAverage(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** 20 períodos para o cálculo.

```ntsl
No exemplo abaixo, a variável aux irá receber o retorno da função TriAverage(), considerando a série High e
var
aux : Float;
begin
aux := TriAverage(High, 20);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função UlcerIndex() mede o nível de estresse do mercado com base na variação negativa dos preços em relação a um topo anterior, ao longo de um período determinado._

**Sintaxe**

```ntsl
Função UlcerIndex(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** 3 períodos.

```ntsl
No exemplo abaixo, a variável aux irá receber o retorno da função UlcerIndex(), considerando a série High e
var
aux : Float;
begin
aux := UlcerIndex(High, 3);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 542

_A função WAverage() calcula a média ponderada de um determinado período._

**Sintaxe**

```ntsl
Função WAverage(SerieDeDados: Serie, Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo abaixo, será plotado no gráfico o retorno da função WAverage(), considerando a série High e 20
begin
Plot(WAverage(High, 20));
end
```

**Gráfico:** ver exemplo no manual, p. 542

_A função WellesSum() retorna o valor do indicador "WellesSum", de acordo com os parâmetros desejados. É o método que cria a soma móvel de uma série de dados, onde cada valor é a soma dos últimos n períodos. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função WellesSum(Periodo: Integer, Dados: Serie, Offset : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

SerieDeDados: Serie; Série utilizada para o cálculo.

Offset: Integer; Referente ao parâmetro "Offset" do indicador.

```ntsl
No exemplo abaixo, será plotado no gráfico o dado do indicador "WellesSum", considerando 20 (Período), série
de fechamento (SerieReferencia) e 0 (Offset) para o cálculo.
begin
Plot(WellesSum(20, Close, 0));
end
```

**Gráfico:** ver exemplo no manual, p. 542

_A função xAverage() retorna a média exponêncial de um determinado período._

**Sintaxe**

```ntsl
Função xAverage(SerieDeDados: Serie, Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** e 10 períodos para o cálculo.

```ntsl
No exemplo abaixo, será plotado no gráfico o retorno da função xAverage(), considerando a série de fechamento
begin
Plot(xAverage(Close, 10));
end
```

### Função Cum
*Manual NTSL v4.7 (14/10/2026) — p. 542*

25 Funções de Usuário

25.1 Função Cum

_A função Cum() acumula o valor de uma série de dados, desde a primeira barra até a atual._

**Sintaxe**

```ntsl
Função Cum(SerieDeDados: Serie): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série para efetuar o somatório.

**Exemplo de uso:** No exemplo, será atribuído à variável aux o somatório da diferença entre as séries Close e Open.

```ntsl
var
aux : Float;
begin
aux := Cum(Close - Open);
Plot(aux);
end;
```

### Função FastKCustom
*Manual NTSL v4.7 (14/10/2026) — p. 543*

_A função FastKCustom() retorna o valor de FastK do Oscilador Estocástico, de acordo com os preços determinados por parâmetro, e período desejado._

**Sintaxe**

```ntsl
Função FastKCustom(PriceH: Serie; PriceL: Serie; PriceC: Serie; Período: Serie):

Float;
```

**Parâmetros**

PriceH: Serie; Série de referência para a máxima.

PriceL: Serie; Série de referência para a mínima.

PriceC: Serie; Série de referência para o fechamento.

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo, será atribuído à variável kCustom o retorno da função FastKCustom, considerando as séries de

```ntsl
máxima(PriceH), mínima(PriceL), fechamento(PriceC), e 14 períodos para o cálculo.
var
kCustom : Float;
begin
kCustom := FastKCustom(High, Low, Close, 14);
Plot(kCustom);
end;
```

### Função HarmonicMean
*Manual NTSL v4.7 (14/10/2026) — p. 545*

_A função HarmonicMean() calcula a média harmônica de uma série de dados, baseada em um determinado período._

**Sintaxe**

```ntsl
Função HarmonicMean(SerieDeDados: Serie Período: Integer;): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Período: Float; Período utilizado no momento do cálculo.

```ntsl
No exemplo a seguir, será atribuído à variável aux o retorno da função HarmonicMean(), considerando a máxima
(Close) e 20 (Períodos) para o cálculo.
var
aux : Float;
begin
aux := HarmonicMean(High, 20);
Plot(aux);
end;
```

### Funcão Highest
*Manual NTSL v4.7 (14/10/2026) — p. 546*

_A função Highest() tem como funcionalidade retornar ao usuário o maior valor da série estipulada por ele, dentro de um período determinado._

**Sintaxe**

```ntsl
Função Highest(SerieDeDados: Serie; Período: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser a abertura, máxima, mínima, fechamento, ou até mesmo indicadores.

Período: Float; Determina o período que será considerado para a pesquisa.

```ntsl
No exemplo abaixo, usamos a função Highest() para retornar a maior abertura dentro de 9 períodos.
begin
if not HasPosition then
Plot(Highest(Open, 9));
end;
```

### Função HighestBar
*Manual NTSL v4.7 (14/10/2026) — p. 547*

_A função HighestBar() tem como funcionalidade retornar o índice do maior valor da série especificada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função HighestBar(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, como abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

**Exemplo de uso:** utilizando a série de abertura.

```ntsl
No exemplo abaixo, usamos a função HighestBar() para retornar o índice da maior mínima dentro de 9 períodos,
var
mMinima : Float;
begin
mMinima := HighestBar(Open, 9);
Plot(mMinima);
end;
```

### Função Lowest
*Manual NTSL v4.7 (14/10/2026) — p. 548*

_A função Lowest() tem como funcionalidade retornar o menor valor da série estipulada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função Lowest(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

```ntsl
No exemplo abaixo, usamos a função Lowest() para retornar o menor fechamento dentro de 50 períodos.
var
low : Float;
begin
low := Lowest(Close, 50);
Plot(low);
end;
```

### Função LowestBar
*Manual NTSL v4.7 (14/10/2026) — p. 549*

_A função LowestBar() tem como funcionalidade retornar o índice do menor valor da série estipulada, dentro de um período determinado._

**Sintaxe**

```ntsl
Função LowestBar(SerieDeDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série de dados desejada, podendo ser abertura, máxima, mínima, fechamento ou indicadores.

Periodo: Integer; Determina o período que será considerado para a pesquisa.

**Exemplo de uso:** períodos, utilizando a série Low.

```ntsl
No exemplo abaixo, usamos a função LowestBar() para retornar o índice da menor mínima dentro de 26
var
lowB : Float;
begin
lowB := LowestBar(Close, 26);
Plot(lowB);
end;
```

### Função Media
*Manual NTSL v4.7 (14/10/2026) — p. 550*

_A função Media() retorna o valor do indicador Média Móvel, tipo aritmética. o exemplo com o código fonte está_

**Sintaxe**

```ntsl
Função Media(Periodo: Integer; TipoSerie: Serie): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

Dados: TipoSerie; Série que será considerada para o cálculo.

```ntsl
No exemplo, será atribuído à variável vMed o valor do indicador Média Móvel (Aritmética), considerando 100
períodos, e a série de fechamento (Close) para o cálculo.
var
vMed : Float;
begin
vMed := Media;
Plot(Media(100, Close));
end;
```

### Função MediaExp
*Manual NTSL v4.7 (14/10/2026) — p. 551*

_A função MediaExp() retorna o valor do indicador Média Móvel, tipo exponencial.
O indicador Média Móvel calcula a média dos dados entre a cotação atual e um período anterior.
O código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função MediaExp(Periodo: Integer; Dados: Serie): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

Dados: Serie; Série que será considerada para o cálculo.

**Exemplo de uso:** de fechamento "Close". O cálculo considera um período de "100" unidades. O valor retornado pela função é então plotado no gráfico.

```ntsl
No exemplo abaixo, a função MediaExp() é utilizada para calcular a média móvel exponencial da série de preços
var
AvgPeriod : Integer;
begin
AvgPeriod := 100;
Plot(MediaExp(AvgPeriod ,Close));
end;
```

### Função MidPoint
*Manual NTSL v4.7 (14/10/2026) — p. 552*

_A função MidPoint() retorna a média entre o maior e o menor valor encontrados no período._

**Sintaxe**

```ntsl
Função MidPoint(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série de referência.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** Close e 15 períodos como base.

```ntsl
No exemplo abaixo, a variável midP irá receber o valor retornado pela função MidPoint(), utilizando a série
var
midP : Float;
begin
midP := MidPoint(Close, 15);
Plot(midP);
end;
```

### Função PercentChange
*Manual NTSL v4.7 (14/10/2026) — p. 553*

_A função PercentChange() calcula a alteração percentual no preço do candle atual em relação a um determinado deslocamento anterior._

**Sintaxe**

```ntsl
Função PercentChange(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série base de referência.

Periodo: Integer; Período anterior para a comparação com o dado da série atual.

**Exemplo de uso:** e 2 períodos para a comparação.

```ntsl
No exemplo abaixo, será atribuído à variável pc o retorno da função PercentChange(), utilizando a série Close
var
pc : Float;
begin
pc := PercentChange(Close, 2);
Plot(pc);
end;
```

### Função PriceOscillator
*Manual NTSL v4.7 (14/10/2026) — p. 554*

_A função PriceOscillator() retorna o valor do indicador PriceOscillator, de acordo com os parâmetros deseja- dos._

**Sintaxe**

```ntsl
Função PriceOscillator(SerieDados: Serie; ComprimentoRapido: Integer;

ComprimentoLento: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo do indicador.

ComprimentoRapido: Integer; Referente ao parâmetro FastLength.

ComprimentoLento: Integer; Referente ao parâmetro SlowLength.

**Exemplo de uso:** High, com comprimento rápido igual a 9 e comprimento lento igual a 18.

```ntsl
No exemplo abaixo, a variável pOsc irá receber o valor do indicador PriceOscillator(), considerando a série
var
pOsc : Float;
begin
pOsc := PriceOscillator(High, 9, 18);
Plot(pOsc);
end;
```

### Função RateOfChange
*Manual NTSL v4.7 (14/10/2026) — p. 555*

_A função RateOfChange() retorna a variação percentual de uma série de dados em relação a um valor anterior definido._

**Sintaxe**

```ntsl
Função RateOfChange(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série base de referência.

Periodo: Integer; Índice do dado utilizado na comparação com o valor atual da série.

```ntsl
No exemplo abaixo, será atribuído à variável rc o valor retornado pela função RateOfChange(), utilizando a
série High e o candle anterior (1) como base de comparação.
var
rc : Float;
begin
rc := RateOfChange(High, 1);
Plot(rc);
end;
```

### Função SlowD
*Manual NTSL v4.7 (14/10/2026) — p. 556*

_A função SlowD() retorna o valor da linha %D do Estocástico Lento, calculada a partir da média móvel dos valores de SlowK, para o período especificado._

**Sintaxe**

```ntsl
Função SlowD(Periodo: Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** cálculo.

```ntsl
No exemplo abaixo, a variável sd irá receber o valor do indicador SlowD(), considerando 14 períodos para o
var
sd : Float;
begin
sd := SlowD(14);
Plot(sd);
end;
```

### Função StdDevs
*Manual NTSL v4.7 (14/10/2026) — p. 557*

_A função StdDevs() retorna o desvio padrão de uma série de dados, em um determinado período._

**Sintaxe**

```ntsl
Função StdDevs(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo abaixo, a variável sd irá receber o retorno da função StdDevs(), considerando a série Close e 20
var
sd : Float;
begin
sd := StdDevs(Close, 20);
Plot(sd);
end;
```

### Função Summation
*Manual NTSL v4.7 (14/10/2026) — p. 558*

_A função Summation() efetua o somatório dos valores de uma série de dados em um determinado número de barras._

**Sintaxe**

```ntsl
Função Summation(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos.

```ntsl
No exemplo abaixo, a variável s irá receber o retorno da função Summation(), considerando a série Close e 10
var
s : Float;
begin
s := Summation(Close, 10);
Plot(s);
end;
```

### Função TriAverage
*Manual NTSL v4.7 (14/10/2026) — p. 559*

_A função TriAverage() efetua a média triangular de uma série de dados, dentro de um determinado período._

**Sintaxe**

```ntsl
Função TriAverage(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** 20 períodos para o cálculo.

```ntsl
No exemplo abaixo, a variável aux irá receber o retorno da função TriAverage(), considerando a série High e
var
aux : Float;
begin
aux := TriAverage(High, 20);
Plot(aux);
end;
```

### Função UlcerIndex
*Manual NTSL v4.7 (14/10/2026) — p. 560*

_A função UlcerIndex() mede o nível de estresse do mercado com base na variação negativa dos preços em relação a um topo anterior, ao longo de um período determinado._

**Sintaxe**

```ntsl
Função UlcerIndex(SerieDados: Serie; Periodo: Integer): Float;
```

**Parâmetros**

SerieDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** 3 períodos.

```ntsl
No exemplo abaixo, a variável aux irá receber o retorno da função UlcerIndex(), considerando a série High e
var
aux : Float;
begin
aux := UlcerIndex(High, 3);
Plot(aux);
end;
```

### Função WAverage
*Manual NTSL v4.7 (14/10/2026) — p. 561*

_A função WAverage() calcula a média ponderada de um determinado período._

**Sintaxe**

```ntsl
Função WAverage(SerieDeDados: Serie, Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo abaixo, será plotado no gráfico o retorno da função WAverage(), considerando a série High e 20
begin
Plot(WAverage(High, 20));
end
```

### Função WellesSum
*Manual NTSL v4.7 (14/10/2026) — p. 562*

_A função WellesSum() retorna o valor do indicador "WellesSum", de acordo com os parâmetros desejados. É o método que cria a soma móvel de uma série de dados, onde cada valor é a soma dos últimos n períodos. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função WellesSum(Periodo: Integer, Dados: Serie, Offset : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

SerieDeDados: Serie; Série utilizada para o cálculo.

Offset: Integer; Referente ao parâmetro "Offset" do indicador.

```ntsl
No exemplo abaixo, será plotado no gráfico o dado do indicador "WellesSum", considerando 20 (Período), série
de fechamento (SerieReferencia) e 0 (Offset) para o cálculo.
begin
Plot(WellesSum(20, Close, 0));
end
```

### Função xAverage
*Manual NTSL v4.7 (14/10/2026) — p. 563*

_A função xAverage() retorna a média exponêncial de um determinado período._

**Sintaxe**

```ntsl
Função xAverage(SerieDeDados: Serie, Periodo: Integer): Float;
```

**Parâmetros**

SerieDeDados: Serie; Série utilizada para o cálculo.

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** e 10 períodos para o cálculo.

```ntsl
No exemplo abaixo, será plotado no gráfico o retorno da função xAverage(), considerando a série de fechamento
begin
Plot(xAverage(Close, 10));
end
```

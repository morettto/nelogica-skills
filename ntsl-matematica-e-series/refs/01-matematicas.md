# 01 Matematicas

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções Matemáticas

### Funções Matemáticas
*Manual NTSL v4.7 (14/10/2026) — p. 486*

Funções Matemáticas

22.1 Função ABS

_A função ABS() retorna o valor absoluto de um número ponto flutuante._

**Sintaxe**

```ntsl
Função ABS(Valor: Float): Float;
```

**Parâmetros**

Valor: Float ; Valor ou variável para obter o módulo.

```ntsl
No exemplo, a variável n irá receber o módulo (4) do valor (-4).
var
n : Float;
begin
n := ABS(-4);
Plot(n);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Arctangent() retorna o arcotangente (em graus) de determinado número_

**Sintaxe**

```ntsl
Função Arctangent(Num: Float): Float;
```

**Parâmetros**

Num: Float ; Número que será convertido.

**Exemplo de uso:** No exemplo, a variável arc irá receber o arcotangente, em graus, do número 12.

```ntsl
var
arc : Float;
begin
arc := Arctangent(12);
Plot(arc);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Ceiling() efetua um arredondamento, retornando o menor inteiro maior que um número específico._

**Sintaxe**

```ntsl
Função Ceiling(Num: Float): Float;
```

**Parâmetros**

Num: Float ; Número que será arredondado.

**Exemplo de uso:** 3).

```ntsl
No exemplo abaixo, usamos a função Ceiling() para retornar o menor inteiro maior que o valor 2.3 (Retorno:
var
number : Float;
begin
number := Ceiling(2.3);
Plot(number);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Combination() calcula o número de grupos com combinação única, considerando um conjunto específico de números._

**Sintaxe**

```ntsl
Função Combination(Num: Integer; NumChosen: Integer): Integer;
```

**Parâmetros**

Num: Integer; Total de números ou itens a serem considerados.

NumChosen: Integer; Número de itens únicos em cada grupo.

```ntsl
No exemplo, será atribuído à variável nComb o número de grupos da combinação (4,2), onde o resultado será 6,
conforme o cálculo: (1,2), (1,3), (1,4), (2,3), (2,4) e (3,4).
var
nComb : Integer;
begin
nComb := Combination(4,2);
Plot(nComb);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Cos() tem como objetivo retornar ao usuário o Cosseno de um valor em radianos._

**Sintaxe**

```ntsl
Função Cos(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCos o Cosseno do valor 180 em radianos(-0,60).
var
nCos : Float;
begin
nCos := Cos(180);
Plot(nCos);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Cosine() tem como objetivo retornar ao usuário o Cosseno de um valor em graus._

**Sintaxe**

```ntsl
Função Cosine(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCos o Cosseno do valor 45 em graus (0,71).
var
nCos : Float;
begin
nCos := Cosine(45);
Plot(nCos);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Cotangent() tem como objetivo retornar ao usuário a Cotangente de um valor em graus._

**Sintaxe**

```ntsl
Função Cotangent(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCo a Cotangente do valor 30 em graus (1,73).
var
nCo : Float;
begin
nCo := Cotangent(30);
Plot(nCo);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Exp() tem como objetivo retornar ao usuário a enésima potência do número de Euler._

**Sintaxe**

```ntsl
Função Exp(Value: Float): Float;
```

**Parâmetros**

Value: Float; Valor ou uma variável para obter a enésima potência (Euler).

```ntsl
No exemplo, será atribuído à variável n o valor de (2) e irá retornar o valor 7,39
var
n : Float;
begin
n := Exp(2);
Plot(n);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função ExpValue() possui como finalidade retornar o valor exponencial de um determinado número._

**Sintaxe**

```ntsl
Função ExpValue(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou uma variável para obter o valor exponencial.

```ntsl
No exemplo, será atribuído à variável n o valor de (2) e irá retornar o valor 7,39
var
n : Float;
begin
n := ExpValue(2);
Plot(n);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função ExtremePriceRatio() retorna o ratio das extremidades(divide o maior valor no periodo pelo menor valor)
de um número determinado de barras._

**Sintaxe**

```ntsl
Função ExtremePriceRatio(Length: Integer; UseLog: Boolean): Float;
```

**Parâmetros**

Length: Integer; O número de barras que serão considerados no cálculo.

UseLog: Boolean; Deterna se o logaritmo de 10 do resultado da divisão será aplicado.

```ntsl
No exemplo, será atribuído à variável pRatio() o retorno da função, considerando 300 períodos para a divisão.
var
pRatio : Float;
begin
pRatio := ExtremePriceRatio(300, True);
Plot(pRatio);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Factorial() tem como finalidade efetuar o cálculo fatorial(n!) de um número natural n._

**Sintaxe**

```ntsl
Função Factorial(Value: Float): Float;
```

**Parâmetros**

Value: Float; Número natural para o cálculo do factorial.

**Exemplo de uso:** No exemplo, será atribuído à variável nFatorial irá receber o fatorial do número 4.

```ntsl
var
nFatorial : Float;
begin
nFatorial := Factorial(4);
Plot(nFatorial);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função FastD() retorna o valor da linha %D do Estocástico Rápido, calculada a partir da média móvel dos valores de FastK, para o período especificado_

**Sintaxe**

```ntsl
Função FastD(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Float; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo, será atribuído à variável interval_d irá receber o retorno da função FastD(), considerando 4
var
interval_d : Float;
begin
interval_d := FastD(4);
Plot(interval_d);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função FastK() retorna o valor da linha %K do Estocástico Rápido, calculada com base na relação entre o preço de fechamento atual e a faixa de preços (máximo e mínimo) do período especificado._

**Sintaxe**

```ntsl
Função FastK(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Float; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo, será atribuído à variável interval_k irá receber o retorno da função FastK(), considerando 14
var
interval_k : Float;
begin
interval_k := FastK(14);
Plot(interval_k);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Floor() possui como finalidade retornar o maior valor inteiro menor que um número determinado._

**Sintaxe**

```ntsl
Função Floor(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor de referência para obter o dado específico.

**Exemplo de uso:** No exemplo, será atribuído à variável m o valor -7.

```ntsl
var
m : Float;
begin
m := Floor(- 6.1);
Plot(m);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função FracPortion() possui como finalidade retornar a parte fracionária de um número._

**Sintaxe**

```ntsl
Função FracPortion(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor de referência para obter o dado específico.

**Exemplo de uso:** No exemplo, será atribuído à variável numFrac o valor 7.14 e será retornado a parte fracionária de 0,14.

```ntsl
var
numFrac : Float;
begin
numFrac := FracPortion(7.14);
Plot(numFrac);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função GCD() retorna o maior denominador comum entre dois números._

**Sintaxe**

```ntsl
Função GCD(Value1: Float; Value2: Float): Float;
```

**Parâmetros**

Value1: Float; Primeiro valor a ser analisado.

Value2: Float; Segundo valor a ser analisado.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável nDem o maior denominador comum entre 12 e 9.

```ntsl
var
nDem : Float;
begin
nDem := GCD(12, 9);
Plot(nDem);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função IntPortion() tem como finalidade retornar a parte inteira de determinado número._

**Sintaxe**

```ntsl
Função IntPortion(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para obter a parte inteira.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável aux o valor 7, que representa a parte inteira de 7.52.

```ntsl
var
aux : Float;
begin
aux := IntPortion(7.52);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Log() retorna o logaritmo natural (ln) de um número._

**Sintaxe**

```ntsl
Função Log(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para o logaritmo natural (ln).

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável vLn o valor do logaritmo natural de 5, aproximadamente 1,61.

```ntsl
var
vLn : Float;
begin
vLn := Log(5);
Plot(vLn);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função LogN() retorna o logaritmo na base N de um número._

**Sintaxe**

```ntsl
Função LogN(Base: Float; Número: Float): Float;
```

**Parâmetros**

Base: Float; Número que deve ser elevado a uma certa potência.

Número: Float; Número para o logaritmo natural (ln).

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável vLn o valor do logaritmo natural de 2 com base 5, aproximadamente
0,43.

```ntsl
var
vLn : Float;
begin
vLn := LogN(5, 2);
Plot(vLn);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Max() retorna o maior valor entre dois números._

**Sintaxe**

```ntsl
Função Max(Valor1: Float; Valor2: Float): Float;
```

**Parâmetros**

Valor1: Float; Primeiro número da comparação.

Valor2: Float; Segundo número da comparação.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável dMax o valor 20.0, que é o maior entre 10.0 e 20.

```ntsl
var
dMax : Float;
begin
dMax := Max(10.0 , 20);
Plot(dMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Min() retorna o menor valor entre dois números._

**Sintaxe**

```ntsl
Função Min(Valor1: Float; Valor2: Float): Float;
```

**Parâmetros**

Valor1: Float; Primeiro número da comparação.

Valor2: Float; Segundo número da comparação.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável dMin o valor 10.0, que é o menor entre 10.0 e 20.

```ntsl
var
dMin : Float;
begin
dMin := Min(10.0 , 20);
Plot(dMin);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função MinutesToTime() retorna a conversão de minutos em hora militar (contagem iniciada à meia-noite)._

**Sintaxe**

```ntsl
Função MinutesToTime(Minutes: Integer): Integer;
```

**Parâmetros**

Minutes: Integer; Minutos para a conversão em horas.

**Exemplo de uso:** No exemplo a seguir, a variável nHora irá receber a conversão de 600 minutos em horas, retornando o valor
1000, que representa 10h.

```ntsl
var
nHora : Integer;
begin
nHora := MinutesToTime(600);
Plot(nHora);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Mod() possui como finalidade retornar o resto da divisão entre dois números inteiros._

**Sintaxe**

```ntsl
Função Mod(Num: Integer; Divisor: Integer): Integer;
```

**Parâmetros**

Num: Integer; Número referente ao dividendo.

Divisor: Integer; Número que será o divisor.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável res o valor 1, referente ao resto da divisão de 10 por 3.

```ntsl
var
res : Integer;
begin
res := Mod(10, 3);
Plot(res);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Neg() retorna o valor negativo de um determinado número._

**Sintaxe**

```ntsl
Função Neg(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor para obter seu número negativo.

**Exemplo de uso:** No exemplo abaixo, a variável nNeg irá receber o valor -5, que é o retorno da função aplicada sobre 5.

```ntsl
var
nNeg : Float;
begin
nNeg := Neg(5);
Plot(nNeg);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função NumUnits() retorna o número de contratos/ações de um certo investimento._

**Sintaxe**

```ntsl
Função NumUnits(Amnt: Integer; MinLot: Integer): Integer;
```

**Parâmetros**

Amnt: Integer; Valor total de investimento, em reais, por operação.

MinLot: Integer; Tamanho mínimo desejado de lote por transação.

**Exemplo de uso:** No exemplo abaixo, assumindo que a ação selecionada custa 29.74 BRL, ao investir 15500 com lote mínimo de

```ntsl
100, a função NumUnits() retornará 500.
var
numU : Integer;
begin
numU := NumUnits(15500, 100);
Plot(numU);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função PercentR() retorna uma porcentagem indicando onde o preço atual está em relação à faixa de negociação avaliada._

**Sintaxe**

```ntsl
Função PercentR(Length: Integer): Float;
```

**Parâmetros**

Length: Integer; Comprimento considerado para o cálculo.

**Exemplo de uso:** comprimento.

```ntsl
No exemplo abaixo, será atribuído à variável vPercentR o retorno da função PercentR(), considerando 2 como
var
vPercentR : Float;
begin
vPercentR := PercentR(2);
Plot(vPercentR);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Permutation() calcula o número de permutações para um determinado número de objetos._

**Sintaxe**

```ntsl
Função Permutation(Num: Integer; NumChosen: Integer): Integer;
```

**Parâmetros**

Num: Integer; Determina o número de candles a serem analisados.

NumChosen: Integer; Define o número de objetos dentro do intervalo de candles que podem ser selecionados.

**Exemplo de uso:** A variável n irá receber a permutação, considerando 4 candles e 2 objetos.

```ntsl
var
n : Integer;
begin
n := Permutation(4, 2);
Plot(n);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Pos() retorna o valor absoluto (módulo) de um número ponto flutuante._

**Sintaxe**

```ntsl
Função Pos(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor ou variável para obter o módulo.

**Exemplo de uso:** No exemplo abaixo, a variável n irá receber o valor 4, que é o módulo do valor -4.

```ntsl
var
n : Float;
begin
n := Pos(-4);
Plot(n);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Power() tem como finalidade retornar a enésima potência de um valor._

**Sintaxe**

```ntsl
Função Power(Valor: Float; Potência: Integer): Float;
```

**Parâmetros**

Valor: Float; Valor base da potenciação.

Potência: Integer; Valor ao qual a base será elevada.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável x o resultado da operação 2³, ou seja, 8.

```ntsl
var
x : Float;
begin
x := Power(2, 3);
Plot(x);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Power() tem como finalidade retornar a enésima potência de um valor._

**Sintaxe**

```ntsl
Função PowerF(Valor: Float; Potência: Float): Float;
```

**Parâmetros**

Valor: Float; Valor base da potenciação.

Potência: Float; Valor ao qual a base será elevada.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável x o resultado da operação 23.5, ou seja, 11,31.

```ntsl
var
x : Float;
begin
x := PowerF(2, 3.5);
Plot(x);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_Com a função Random(), o usuário poderá gerar um número aleatório inteiro dentro de um intervalo iniciado em zero, tendo como limite superior o valor definido por parâmetro._

**Sintaxe**

```ntsl
Função Random(Limite: Integer): Integer;
```

**Parâmetros**

Limite: Integer; Valor ou variável que determina o limite superior do intervalo.

**Exemplo de uso:** aux.

```ntsl
No exemplo a seguir, a função Random() irá gerar números aleatórios entre 0 e 5, que serão atribuídos à variável
var
aux : Integer;
begin
aux := Random(5);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Round() possui como finalidade efetuar o arredondamento de um número ponto flutuante._

**Sintaxe**

```ntsl
Função Round(Valor: Float): Integer;
```

**Parâmetros**

Valor: Float; Número (variável ou constante) com casas decimais que será arredondado.

**Exemplo de uso:** Conforme o exemplo abaixo, será atribuído à variável aux o valor arredondado de 2.6, ao utilizar a função

```ntsl
Round().
var
aux : Integer;
begin
aux := Round(2.6);
Plot(aux);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Round2Fraction() efetua o arredondamento de um número para o valor mais próximo de um múltiplo do incremento mínimo de um ativo._

**Sintaxe**

```ntsl
Função Round2Fraction(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor desejado para o arredondamento de acordo com o incremento mínimo do ativo.

**Exemplo de uso:** variável nRound2.

```ntsl
No exemplo abaixo (ativos Bovespa), ao aplicar a função para o valor 31.626, será atribuído o valor 31.63 à
var
nRound2 : Float;
begin
nRound2 := Round2Fraction(31.626);
Plot(nRound2);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Sign() possui como definição retornar um número inteiro baseado no sinal de um valor numérico._

**Sintaxe**

```ntsl
Função Sign(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para obter seu sinal.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável nSinal o valor -1, tendo em vista o valor -205 passado por parâmetro.

```ntsl
var
nSinal : Float;
begin
nSinal := Sign(-205);
Plot(nSinal);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Sin() tem como objetivo retornar o seno de um valor em radianos._

**Sintaxe**

```ntsl
Função Sin(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor para obter o seno.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável nSeno o valor do seno de 180, aproximadamente -0,80.

```ntsl
var
nSeno : Float;
begin
nSeno := Sin(180);
Plot(nSeno);
end;
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Sine() retorna o seno de um número em graus._

**Sintaxe**

```ntsl
Função Sine(Num: Float): Float;
```

**Parâmetros**

Sine: Float; Determina número escolhido para o cálculo.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o seno de 75.

```ntsl
begin
Plot(Sine(75));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função SlowK() retorna o valor da linha %K do Estocástico Lento (Slow Stochastic). Essa linha corresponde a uma versão suavizada da linha FastK, sendo calculada a partir da média dos valores do Estocástico Rápido._

**Sintaxe**

```ntsl
Função SlowK(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Integer; Determina o tamanho escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função SlowK().
begin
Plot(SlowK(10));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Sqrt() retorna a raiz quadrada de um valor._

**Sintaxe**

```ntsl
Função Sqrt(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Determina o valor escolhido para o cálculo.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a raiz quadrada de 144.

```ntsl
begin
Plot(Sqrt(144));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Square() retorna o valor de um determinado número ao quadrado._

**Sintaxe**

```ntsl
Função Square(Num: Float): Float;
```

**Parâmetros**

Num: Float; Determina o valor escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Square(), considerando 12 para o cálculo.
begin
Plot(Square(12));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Tangent() retorna a tangente de um número específico._

**Sintaxe**

```ntsl
Função Tangent(Num: Float): Float;
```

**Parâmetros**

Num: Float; Determina o valor escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Tangent(), considerando 45 para o cálculo.
begin
Plot(Tangent(45));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função UltimateOscillator() retorna o valor do "Ultimate Oscillator" desenvolvido por Larry Williams._

**Sintaxe**

```ntsl
Função UltimateOscillator(ShortLength: Integer, MiddLength: Integer, LongLength:

Integer): Float;
```

**Parâmetros**

ShortLength: Integer; Número de períodos para a média mais curta utilizada no cálculo do indicador.

MiddLength: Integer; Número de períodos para a média intermediária utilizada no cálculo do indicador.

LongLength: Integer; Número de períodos para a média mais longa utilizada no cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o retorno do indicador "Ultimate Oscillator" com períodos de 10 candles para as 3 médias.

```ntsl
begin
Plot(UltimateOscillator(10,10,10));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função Volatility() retorna a volatilidade de um determinado período._

**Sintaxe**

```ntsl
Função Volatility(Period: Integer): Float;
```

**Parâmetros**

Period: Integer; Determina o periodo para cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Volatility() com período 30.
begin
Plot(Volatility(30));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função VolumeOsc() retorna a diferença entre a média rápida e a média móvel lenta do volume._

**Sintaxe**

```ntsl
Função VolumeOsc(FastLength: Integer, SlowLength: Integer): Float;
```

**Parâmetros**

FastLength: Integer; Valor de média rápida.

SlowLength: Integer; Valor de média móvel.

**Exemplo de uso:** média móvel igual a 9.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função VolumeOsc() com média rápida igual a 1 e
begin
Plot(VolumeOsc(1,9));
end
```

**Gráfico:** ver exemplo no manual, p. 486

_A função VolumeROC() retorna o "VolumeROC" baseado em um número de barras._

**Sintaxe**

```ntsl
Função VolumeROC(Length: Integer): Float;
```

**Parâmetros**

Length: Integer; Período definido pela quantidade de barras, usado no cálculo do Volume Rate of Change.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função VolumeROC().
begin
Plot(VolumeROC(1));
end
```

### Função ABS
*Manual NTSL v4.7 (14/10/2026) — p. 486*

22 Funções Matemáticas

22.1 Função ABS

_A função ABS() retorna o valor absoluto de um número ponto flutuante._

**Sintaxe**

```ntsl
Função ABS(Valor: Float): Float;
```

**Parâmetros**

Valor: Float ; Valor ou variável para obter o módulo.

```ntsl
No exemplo, a variável n irá receber o módulo (4) do valor (-4).
var
n : Float;
begin
n := ABS(-4);
Plot(n);
end;
```

### Função Arctangent
*Manual NTSL v4.7 (14/10/2026) — p. 487*

_A função Arctangent() retorna o arcotangente (em graus) de determinado número_

**Sintaxe**

```ntsl
Função Arctangent(Num: Float): Float;
```

**Parâmetros**

Num: Float ; Número que será convertido.

**Exemplo de uso:** No exemplo, a variável arc irá receber o arcotangente, em graus, do número 12.

```ntsl
var
arc : Float;
begin
arc := Arctangent(12);
Plot(arc);
end;
```

### Função Ceiling
*Manual NTSL v4.7 (14/10/2026) — p. 488*

_A função Ceiling() efetua um arredondamento, retornando o menor inteiro maior que um número específico._

**Sintaxe**

```ntsl
Função Ceiling(Num: Float): Float;
```

**Parâmetros**

Num: Float ; Número que será arredondado.

**Exemplo de uso:** 3).

```ntsl
No exemplo abaixo, usamos a função Ceiling() para retornar o menor inteiro maior que o valor 2.3 (Retorno:
var
number : Float;
begin
number := Ceiling(2.3);
Plot(number);
end;
```

### Função Combination
*Manual NTSL v4.7 (14/10/2026) — p. 489*

_A função Combination() calcula o número de grupos com combinação única, considerando um conjunto específico de números._

**Sintaxe**

```ntsl
Função Combination(Num: Integer; NumChosen: Integer): Integer;
```

**Parâmetros**

Num: Integer; Total de números ou itens a serem considerados.

NumChosen: Integer; Número de itens únicos em cada grupo.

```ntsl
No exemplo, será atribuído à variável nComb o número de grupos da combinação (4,2), onde o resultado será 6,
conforme o cálculo: (1,2), (1,3), (1,4), (2,3), (2,4) e (3,4).
var
nComb : Integer;
begin
nComb := Combination(4,2);
Plot(nComb);
end;
```

### Função Cos
*Manual NTSL v4.7 (14/10/2026) — p. 490*

_A função Cos() tem como objetivo retornar ao usuário o Cosseno de um valor em radianos._

**Sintaxe**

```ntsl
Função Cos(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCos o Cosseno do valor 180 em radianos(-0,60).
var
nCos : Float;
begin
nCos := Cos(180);
Plot(nCos);
end;
```

### Função Cosine
*Manual NTSL v4.7 (14/10/2026) — p. 491*

_A função Cosine() tem como objetivo retornar ao usuário o Cosseno de um valor em graus._

**Sintaxe**

```ntsl
Função Cosine(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCos o Cosseno do valor 45 em graus (0,71).
var
nCos : Float;
begin
nCos := Cosine(45);
Plot(nCos);
end;
```

### Função Cotangent
*Manual NTSL v4.7 (14/10/2026) — p. 492*

_A função Cotangent() tem como objetivo retornar ao usuário a Cotangente de um valor em graus._

**Sintaxe**

```ntsl
Função Cotangent(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou variável para obter o Cosseno.

```ntsl
No exemplo, será atribuído à variável nCo a Cotangente do valor 30 em graus (1,73).
var
nCo : Float;
begin
nCo := Cotangent(30);
Plot(nCo);
end;
```

### Função Exp
*Manual NTSL v4.7 (14/10/2026) — p. 493*

_A função Exp() tem como objetivo retornar ao usuário a enésima potência do número de Euler._

**Sintaxe**

```ntsl
Função Exp(Value: Float): Float;
```

**Parâmetros**

Value: Float; Valor ou uma variável para obter a enésima potência (Euler).

```ntsl
No exemplo, será atribuído à variável n o valor de (2) e irá retornar o valor 7,39
var
n : Float;
begin
n := Exp(2);
Plot(n);
end;
```

### Função ExpValue
*Manual NTSL v4.7 (14/10/2026) — p. 494*

_A função ExpValue() possui como finalidade retornar o valor exponencial de um determinado número._

**Sintaxe**

```ntsl
Função ExpValue(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor ou uma variável para obter o valor exponencial.

```ntsl
No exemplo, será atribuído à variável n o valor de (2) e irá retornar o valor 7,39
var
n : Float;
begin
n := ExpValue(2);
Plot(n);
end;
```

### Função ExtremePriceRatio
*Manual NTSL v4.7 (14/10/2026) — p. 495*

_A função ExtremePriceRatio() retorna o ratio das extremidades(divide o maior valor no periodo pelo menor valor)
de um número determinado de barras._

**Sintaxe**

```ntsl
Função ExtremePriceRatio(Length: Integer; UseLog: Boolean): Float;
```

**Parâmetros**

Length: Integer; O número de barras que serão considerados no cálculo.

UseLog: Boolean; Deterna se o logaritmo de 10 do resultado da divisão será aplicado.

```ntsl
No exemplo, será atribuído à variável pRatio() o retorno da função, considerando 300 períodos para a divisão.
var
pRatio : Float;
begin
pRatio := ExtremePriceRatio(300, True);
Plot(pRatio);
end;
```

### Função Factorial
*Manual NTSL v4.7 (14/10/2026) — p. 496*

_A função Factorial() tem como finalidade efetuar o cálculo fatorial(n!) de um número natural n._

**Sintaxe**

```ntsl
Função Factorial(Value: Float): Float;
```

**Parâmetros**

Value: Float; Número natural para o cálculo do factorial.

**Exemplo de uso:** No exemplo, será atribuído à variável nFatorial irá receber o fatorial do número 4.

```ntsl
var
nFatorial : Float;
begin
nFatorial := Factorial(4);
Plot(nFatorial);
end;
```

### Função FastD
*Manual NTSL v4.7 (14/10/2026) — p. 497*

_A função FastD() retorna o valor da linha %D do Estocástico Rápido, calculada a partir da média móvel dos valores de FastK, para o período especificado_

**Sintaxe**

```ntsl
Função FastD(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Float; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo, será atribuído à variável interval_d irá receber o retorno da função FastD(), considerando 4
var
interval_d : Float;
begin
interval_d := FastD(4);
Plot(interval_d);
end;
```

### Função FastK
*Manual NTSL v4.7 (14/10/2026) — p. 498*

_A função FastK() retorna o valor da linha %K do Estocástico Rápido, calculada com base na relação entre o preço de fechamento atual e a faixa de preços (máximo e mínimo) do período especificado._

**Sintaxe**

```ntsl
Função FastK(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Float; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** períodos para o cálculo.

```ntsl
No exemplo, será atribuído à variável interval_k irá receber o retorno da função FastK(), considerando 14
var
interval_k : Float;
begin
interval_k := FastK(14);
Plot(interval_k);
end;
```

### Função Floor
*Manual NTSL v4.7 (14/10/2026) — p. 499*

_A função Floor() possui como finalidade retornar o maior valor inteiro menor que um número determinado._

**Sintaxe**

```ntsl
Função Floor(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor de referência para obter o dado específico.

**Exemplo de uso:** No exemplo, será atribuído à variável m o valor -7.

```ntsl
var
m : Float;
begin
m := Floor(- 6.1);
Plot(m);
end;
```

### Função FracPortion
*Manual NTSL v4.7 (14/10/2026) — p. 500*

_A função FracPortion() possui como finalidade retornar a parte fracionária de um número._

**Sintaxe**

```ntsl
Função FracPortion(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor de referência para obter o dado específico.

**Exemplo de uso:** No exemplo, será atribuído à variável numFrac o valor 7.14 e será retornado a parte fracionária de 0,14.

```ntsl
var
numFrac : Float;
begin
numFrac := FracPortion(7.14);
Plot(numFrac);
end;
```

### Função GCD
*Manual NTSL v4.7 (14/10/2026) — p. 501*

_A função GCD() retorna o maior denominador comum entre dois números._

**Sintaxe**

```ntsl
Função GCD(Value1: Float; Value2: Float): Float;
```

**Parâmetros**

Value1: Float; Primeiro valor a ser analisado.

Value2: Float; Segundo valor a ser analisado.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável nDem o maior denominador comum entre 12 e 9.

```ntsl
var
nDem : Float;
begin
nDem := GCD(12, 9);
Plot(nDem);
end;
```

### Função IntPortion
*Manual NTSL v4.7 (14/10/2026) — p. 502*

_A função IntPortion() tem como finalidade retornar a parte inteira de determinado número._

**Sintaxe**

```ntsl
Função IntPortion(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para obter a parte inteira.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável aux o valor 7, que representa a parte inteira de 7.52.

```ntsl
var
aux : Float;
begin
aux := IntPortion(7.52);
Plot(aux);
end;
```

### Função Log
*Manual NTSL v4.7 (14/10/2026) — p. 503*

_A função Log() retorna o logaritmo natural (ln) de um número._

**Sintaxe**

```ntsl
Função Log(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para o logaritmo natural (ln).

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável vLn o valor do logaritmo natural de 5, aproximadamente 1,61.

```ntsl
var
vLn : Float;
begin
vLn := Log(5);
Plot(vLn);
end;
```

### Função LogN
*Manual NTSL v4.7 (14/10/2026) — p. 504*

_A função LogN() retorna o logaritmo na base N de um número._

**Sintaxe**

```ntsl
Função LogN(Base: Float; Número: Float): Float;
```

**Parâmetros**

Base: Float; Número que deve ser elevado a uma certa potência.

Número: Float; Número para o logaritmo natural (ln).

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável vLn o valor do logaritmo natural de 2 com base 5, aproximadamente
0,43.

```ntsl
var
vLn : Float;
begin
vLn := LogN(5, 2);
Plot(vLn);
end;
```

### Função Max
*Manual NTSL v4.7 (14/10/2026) — p. 505*

_A função Max() retorna o maior valor entre dois números._

**Sintaxe**

```ntsl
Função Max(Valor1: Float; Valor2: Float): Float;
```

**Parâmetros**

Valor1: Float; Primeiro número da comparação.

Valor2: Float; Segundo número da comparação.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável dMax o valor 20.0, que é o maior entre 10.0 e 20.

```ntsl
var
dMax : Float;
begin
dMax := Max(10.0 , 20);
Plot(dMax);
end;
```

### Função Min
*Manual NTSL v4.7 (14/10/2026) — p. 506*

_A função Min() retorna o menor valor entre dois números._

**Sintaxe**

```ntsl
Função Min(Valor1: Float; Valor2: Float): Float;
```

**Parâmetros**

Valor1: Float; Primeiro número da comparação.

Valor2: Float; Segundo número da comparação.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável dMin o valor 10.0, que é o menor entre 10.0 e 20.

```ntsl
var
dMin : Float;
begin
dMin := Min(10.0 , 20);
Plot(dMin);
end;
```

### Função MinutesToTime
*Manual NTSL v4.7 (14/10/2026) — p. 507*

_A função MinutesToTime() retorna a conversão de minutos em hora militar (contagem iniciada à meia-noite)._

**Sintaxe**

```ntsl
Função MinutesToTime(Minutes: Integer): Integer;
```

**Parâmetros**

Minutes: Integer; Minutos para a conversão em horas.

**Exemplo de uso:** No exemplo a seguir, a variável nHora irá receber a conversão de 600 minutos em horas, retornando o valor
1000, que representa 10h.

```ntsl
var
nHora : Integer;
begin
nHora := MinutesToTime(600);
Plot(nHora);
end;
```

### Função Mod
*Manual NTSL v4.7 (14/10/2026) — p. 508*

_A função Mod() possui como finalidade retornar o resto da divisão entre dois números inteiros._

**Sintaxe**

```ntsl
Função Mod(Num: Integer; Divisor: Integer): Integer;
```

**Parâmetros**

Num: Integer; Número referente ao dividendo.

Divisor: Integer; Número que será o divisor.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável res o valor 1, referente ao resto da divisão de 10 por 3.

```ntsl
var
res : Integer;
begin
res := Mod(10, 3);
Plot(res);
end;
```

### Função Neg
*Manual NTSL v4.7 (14/10/2026) — p. 509*

_A função Neg() retorna o valor negativo de um determinado número._

**Sintaxe**

```ntsl
Função Neg(Num: Float): Float;
```

**Parâmetros**

Num: Float; Valor para obter seu número negativo.

**Exemplo de uso:** No exemplo abaixo, a variável nNeg irá receber o valor -5, que é o retorno da função aplicada sobre 5.

```ntsl
var
nNeg : Float;
begin
nNeg := Neg(5);
Plot(nNeg);
end;
```

### Função NumUnits
*Manual NTSL v4.7 (14/10/2026) — p. 510*

_A função NumUnits() retorna o número de contratos/ações de um certo investimento._

**Sintaxe**

```ntsl
Função NumUnits(Amnt: Integer; MinLot: Integer): Integer;
```

**Parâmetros**

Amnt: Integer; Valor total de investimento, em reais, por operação.

MinLot: Integer; Tamanho mínimo desejado de lote por transação.

**Exemplo de uso:** No exemplo abaixo, assumindo que a ação selecionada custa 29.74 BRL, ao investir 15500 com lote mínimo de

```ntsl
100, a função NumUnits() retornará 500.
var
numU : Integer;
begin
numU := NumUnits(15500, 100);
Plot(numU);
end;
```

### Função PercentR
*Manual NTSL v4.7 (14/10/2026) — p. 511*

_A função PercentR() retorna uma porcentagem indicando onde o preço atual está em relação à faixa de negociação avaliada._

**Sintaxe**

```ntsl
Função PercentR(Length: Integer): Float;
```

**Parâmetros**

Length: Integer; Comprimento considerado para o cálculo.

**Exemplo de uso:** comprimento.

```ntsl
No exemplo abaixo, será atribuído à variável vPercentR o retorno da função PercentR(), considerando 2 como
var
vPercentR : Float;
begin
vPercentR := PercentR(2);
Plot(vPercentR);
end;
```

### Função Permutation
*Manual NTSL v4.7 (14/10/2026) — p. 512*

_A função Permutation() calcula o número de permutações para um determinado número de objetos._

**Sintaxe**

```ntsl
Função Permutation(Num: Integer; NumChosen: Integer): Integer;
```

**Parâmetros**

Num: Integer; Determina o número de candles a serem analisados.

NumChosen: Integer; Define o número de objetos dentro do intervalo de candles que podem ser selecionados.

**Exemplo de uso:** A variável n irá receber a permutação, considerando 4 candles e 2 objetos.

```ntsl
var
n : Integer;
begin
n := Permutation(4, 2);
Plot(n);
end;
```

### Função Pos
*Manual NTSL v4.7 (14/10/2026) — p. 513*

_A função Pos() retorna o valor absoluto (módulo) de um número ponto flutuante._

**Sintaxe**

```ntsl
Função Pos(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor ou variável para obter o módulo.

**Exemplo de uso:** No exemplo abaixo, a variável n irá receber o valor 4, que é o módulo do valor -4.

```ntsl
var
n : Float;
begin
n := Pos(-4);
Plot(n);
end;
```

### Função Power
*Manual NTSL v4.7 (14/10/2026) — p. 514*

_A função Power() tem como finalidade retornar a enésima potência de um valor._

**Sintaxe**

```ntsl
Função Power(Valor: Float; Potência: Integer): Float;
```

**Parâmetros**

Valor: Float; Valor base da potenciação.

Potência: Integer; Valor ao qual a base será elevada.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável x o resultado da operação 2³, ou seja, 8.

```ntsl
var
x : Float;
begin
x := Power(2, 3);
Plot(x);
end;
```

### Função PowerF
*Manual NTSL v4.7 (14/10/2026) — p. 515*

_A função Power() tem como finalidade retornar a enésima potência de um valor._

**Sintaxe**

```ntsl
Função PowerF(Valor: Float; Potência: Float): Float;
```

**Parâmetros**

Valor: Float; Valor base da potenciação.

Potência: Float; Valor ao qual a base será elevada.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável x o resultado da operação 23.5, ou seja, 11,31.

```ntsl
var
x : Float;
begin
x := PowerF(2, 3.5);
Plot(x);
end;
```

### Função Random
*Manual NTSL v4.7 (14/10/2026) — p. 516*

_Com a função Random(), o usuário poderá gerar um número aleatório inteiro dentro de um intervalo iniciado em zero, tendo como limite superior o valor definido por parâmetro._

**Sintaxe**

```ntsl
Função Random(Limite: Integer): Integer;
```

**Parâmetros**

Limite: Integer; Valor ou variável que determina o limite superior do intervalo.

**Exemplo de uso:** aux.

```ntsl
No exemplo a seguir, a função Random() irá gerar números aleatórios entre 0 e 5, que serão atribuídos à variável
var
aux : Integer;
begin
aux := Random(5);
Plot(aux);
end;
```

### Função Round
*Manual NTSL v4.7 (14/10/2026) — p. 517*

_A função Round() possui como finalidade efetuar o arredondamento de um número ponto flutuante._

**Sintaxe**

```ntsl
Função Round(Valor: Float): Integer;
```

**Parâmetros**

Valor: Float; Número (variável ou constante) com casas decimais que será arredondado.

**Exemplo de uso:** Conforme o exemplo abaixo, será atribuído à variável aux o valor arredondado de 2.6, ao utilizar a função

```ntsl
Round().
var
aux : Integer;
begin
aux := Round(2.6);
Plot(aux);
end;
```

### Função Round2Fraction
*Manual NTSL v4.7 (14/10/2026) — p. 518*

_A função Round2Fraction() efetua o arredondamento de um número para o valor mais próximo de um múltiplo do incremento mínimo de um ativo._

**Sintaxe**

```ntsl
Função Round2Fraction(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor desejado para o arredondamento de acordo com o incremento mínimo do ativo.

**Exemplo de uso:** variável nRound2.

```ntsl
No exemplo abaixo (ativos Bovespa), ao aplicar a função para o valor 31.626, será atribuído o valor 31.63 à
var
nRound2 : Float;
begin
nRound2 := Round2Fraction(31.626);
Plot(nRound2);
end;
```

### Função Sign
*Manual NTSL v4.7 (14/10/2026) — p. 519*

_A função Sign() possui como definição retornar um número inteiro baseado no sinal de um valor numérico._

**Sintaxe**

```ntsl
Função Sign(Num: Float): Float;
```

**Parâmetros**

Num: Float; Número para obter seu sinal.

**Exemplo de uso:** No exemplo abaixo, será atribuído à variável nSinal o valor -1, tendo em vista o valor -205 passado por parâmetro.

```ntsl
var
nSinal : Float;
begin
nSinal := Sign(-205);
Plot(nSinal);
end;
```

### Função Sin
*Manual NTSL v4.7 (14/10/2026) — p. 520*

_A função Sin() tem como objetivo retornar o seno de um valor em radianos._

**Sintaxe**

```ntsl
Função Sin(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Valor para obter o seno.

**Exemplo de uso:** No exemplo a seguir, será atribuído à variável nSeno o valor do seno de 180, aproximadamente -0,80.

```ntsl
var
nSeno : Float;
begin
nSeno := Sin(180);
Plot(nSeno);
end;
```

### Função Sine
*Manual NTSL v4.7 (14/10/2026) — p. 521*

_A função Sine() retorna o seno de um número em graus._

**Sintaxe**

```ntsl
Função Sine(Num: Float): Float;
```

**Parâmetros**

Sine: Float; Determina número escolhido para o cálculo.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o seno de 75.

```ntsl
begin
Plot(Sine(75));
end
```

### Função SlowK
*Manual NTSL v4.7 (14/10/2026) — p. 522*

_A função SlowK() retorna o valor da linha %K do Estocástico Lento (Slow Stochastic). Essa linha corresponde a uma versão suavizada da linha FastK, sendo calculada a partir da média dos valores do Estocástico Rápido._

**Sintaxe**

```ntsl
Função SlowK(StochLength: Integer): Float;
```

**Parâmetros**

StochLength: Integer; Determina o tamanho escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função SlowK().
begin
Plot(SlowK(10));
end
```

### Função Sqrt
*Manual NTSL v4.7 (14/10/2026) — p. 523*

_A função Sqrt() retorna a raiz quadrada de um valor._

**Sintaxe**

```ntsl
Função Sqrt(Valor: Float): Float;
```

**Parâmetros**

Valor: Float; Determina o valor escolhido para o cálculo.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a raiz quadrada de 144.

```ntsl
begin
Plot(Sqrt(144));
end
```

### Função Square
*Manual NTSL v4.7 (14/10/2026) — p. 524*

_A função Square() retorna o valor de um determinado número ao quadrado._

**Sintaxe**

```ntsl
Função Square(Num: Float): Float;
```

**Parâmetros**

Num: Float; Determina o valor escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Square(), considerando 12 para o cálculo.
begin
Plot(Square(12));
end
```

### Função Tangent
*Manual NTSL v4.7 (14/10/2026) — p. 525*

_A função Tangent() retorna a tangente de um número específico._

**Sintaxe**

```ntsl
Função Tangent(Num: Float): Float;
```

**Parâmetros**

Num: Float; Determina o valor escolhido para o cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Tangent(), considerando 45 para o cálculo.
begin
Plot(Tangent(45));
end
```

### Função UltimateOscillator
*Manual NTSL v4.7 (14/10/2026) — p. 526*

_A função UltimateOscillator() retorna o valor do "Ultimate Oscillator" desenvolvido por Larry Williams._

**Sintaxe**

```ntsl
Função UltimateOscillator(ShortLength: Integer, MiddLength: Integer, LongLength:

Integer): Float;
```

**Parâmetros**

ShortLength: Integer; Número de períodos para a média mais curta utilizada no cálculo do indicador.

MiddLength: Integer; Número de períodos para a média intermediária utilizada no cálculo do indicador.

LongLength: Integer; Número de períodos para a média mais longa utilizada no cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o retorno do indicador "Ultimate Oscillator" com períodos de 10 candles para as 3 médias.

```ntsl
begin
Plot(UltimateOscillator(10,10,10));
end
```

### Função Volatility
*Manual NTSL v4.7 (14/10/2026) — p. 527*

_A função Volatility() retorna a volatilidade de um determinado período._

**Sintaxe**

```ntsl
Função Volatility(Period: Integer): Float;
```

**Parâmetros**

Period: Integer; Determina o periodo para cálculo.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função Volatility() com período 30.
begin
Plot(Volatility(30));
end
```

### Função VolumeOsc
*Manual NTSL v4.7 (14/10/2026) — p. 528*

_A função VolumeOsc() retorna a diferença entre a média rápida e a média móvel lenta do volume._

**Sintaxe**

```ntsl
Função VolumeOsc(FastLength: Integer, SlowLength: Integer): Float;
```

**Parâmetros**

FastLength: Integer; Valor de média rápida.

SlowLength: Integer; Valor de média móvel.

**Exemplo de uso:** média móvel igual a 9.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função VolumeOsc() com média rápida igual a 1 e
begin
Plot(VolumeOsc(1,9));
end
```

### Função VolumeROC
*Manual NTSL v4.7 (14/10/2026) — p. 529*

_A função VolumeROC() retorna o "VolumeROC" baseado em um número de barras._

**Sintaxe**

```ntsl
Função VolumeROC(Length: Integer): Float;
```

**Parâmetros**

Length: Integer; Período definido pela quantidade de barras, usado no cálculo do Volume Rate of Change.

```ntsl
No exemplo a seguir, será plotado no gráfico o retorno da função VolumeROC().
begin
Plot(VolumeROC(1));
end
```

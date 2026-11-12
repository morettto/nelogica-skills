# 03 Controle De Fluxo E Operadores

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Controle de Fluxo

### Controle de Fluxo
*Manual NTSL v4.7 (14/10/2026) — p. 28*

Controle de Fluxo

As instruções de fluxo são utilizadas para administrar a sequência de execução das instruções dentro de um programa.
A NTSL apresenta três tipos desse tipo:

5.1 If then else (Se então senão)

Se (condição) for verdadeiro executa-se a listagem (comandos 1), caso (condição) seja falso executa-se (comandos
2). Tanto (comandos 1) quanto (comandos 2) podem ser sequências de instruções.
A expressão (condição) pode ser qualquer tipo de teste que resulte em verdadeiro ou falso, alguns exemplos:

if (Close > Close[1])
if (nIndex = 10)
if (bCond = false) and (Volume > 1000)

A seguir um exemplo de coloração de candles de acordo com a condição presente no If then else (Se então senão).

begin

if (close = close[1]) then

PaintBar(clYellow)

else if (close > close[1]) then

PaintBar(clGreen)

else

PaintBar(clRed);

end;

Se o valor de fechamento da barra atual (Close equivale a Close[0]) for igual ao fechamento da barra anterior
(Representado por Close[1]) executa-se o código que segue a palavra reservada THEN (ENTÃO) . Caso contrário, o sistema executa o código subsequente até chegar na palavra reservada ELSE (SENÃO) .

Exemplo com múltiplas instruções begin e end (inicio e fim)
Quando a listagem (comandos 1 ou comandos 2) contiver mais de uma instrução, é necessário delimitar o bloco com begin (inicio) e end (fim). Veja o exemplo:

begin

if (close = close[1]) then

begin

PaintBar(clYellow);
PlotText("Fechamento igual ao anterior", clYellow);

end

else if (close > close[1]) then

begin

PaintBar(clGreen);
PlotText("Fechamento superior ao anterior", clGreen);

end

else

begin

PaintBar(clRed);
PlotText("Fechamento inferior ao anterior", clRed);

end;

end;

5.2 For (To / DownTo) Do (Para (Até / DownTo) Faça)

O comando FOR (PARA) é utilizado para definir um loop controlado, ou seja, o bloco é executado repetidamente até que a variável de contagem saia do valor inicial e atinja o valor final.

Para a variável controladora, pode-se incrementá-la, a partir do comando To (Até), ou decrementá-la, ao utilizar na estrutura o DownTo.

Importante: O laço FOR (PARA) em NTSL aceita apenas valores inteiros para a variável de controle e para os limites de iteração (To / DownTo). O uso de variáveis ou expressões do tipo Float não é suportado e resultará em comportamento inválido.

Exemplo (For To Do (Para Até Faça)):
Observe o código da média móvel, a variável de contagem nIndex começa com o valor 0 e deve chegar ao valor de
Periodo – 1. No exemplo, Periodo foi definido como parâmetro de entrada, para definir o tamanho da média.
Assim, caso seja parametrizado o valor 0 (Periodo), o comando FOR criará um loop de 9 iterações (de 0 até 8) para cada barra, calculando assim o valor médio para a posição atual.

input

Preco(close);
Periodo(9);

var

sResult : Float;
nIndex

: Integer;

begin

sResult := 0;
for nIndex := 0 to Periodo - 1 do

begin

sResult := sResult + Preco[nIndex];

end;

Plot(sResult / Periodo);

end;

Exemplo (For To Do x For DownTo Do (Para Até Faça x Para DownTo Faça)):
A fim didático, segue um exemplo de cálculo de fatorial, utilizando as duas estruturas.
For To Do (Para Até Faça):

input

n(6);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
For i := 1 To n Do

fatorial := fatorial * i;

Plot(fatorial);

end;

For DownTo Do (Para DownTo Faça):

input

n(6);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
For i := n DownTo 1 Do

fatorial := fatorial * i;

Plot(fatorial);

end;

5.3 While (Enquanto)

A execução da estratégia ao chegar no comando WHILE testa o resultado de (condição). Caso (condição) seja verdadeiro (true) a listagem (comandos) é executada. Após a execução a (condição) volta a ser testada, assim, o loop apenas irá se encerrar quando (condição) deixar de ser verdadeira.
Exemplo:
No código a seguir, reescrevemos o indicador média móvel utilizando a instrução WHILE (ENQUANTO) ao invés de
FOR (PARA) .

input

Preco(close);
Periodo(9);

var

sResult : Float;
nIndex

: Integer;

begin

sResult := 0;
nIndex := 0;
while (nIndex <= Periodo - 1) do

begin

sResult := sResult + Preco[nIndex];
nIndex := nIndex + 1;

end;

Plot(sResult / Periodo);

end;

5.4 Repeat (Repita)

Este comando difere-se do For e While, no sentido de que a condição será testada no final da estrutura, e não no início, portanto, as instruções do bloco serão executadas pelo menos uma vez.
Exemplo:
A fim de comparação com as outras estruturas já abordadas, segue o exemplo de cálculo de fatorial:

input

n(5);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
i := 1;
repeat

begin

fatorial := fatorial * i;
i := i + 1;

end

until (i > n);
Plot(fatorial);

end;

### If then else (Se então senão)
*Manual NTSL v4.7 (14/10/2026) — p. 28*

5 Controle de Fluxo

As instruções de fluxo são utilizadas para administrar a sequência de execução das instruções dentro de um programa.
A NTSL apresenta três tipos desse tipo:

5.1 If then else (Se então senão)

Se (condição) for verdadeiro executa-se a listagem (comandos 1), caso (condição) seja falso executa-se (comandos
2). Tanto (comandos 1) quanto (comandos 2) podem ser sequências de instruções.
A expressão (condição) pode ser qualquer tipo de teste que resulte em verdadeiro ou falso, alguns exemplos:

if (Close > Close[1])
if (nIndex = 10)
if (bCond = false) and (Volume > 1000)

A seguir um exemplo de coloração de candles de acordo com a condição presente no If then else (Se então senão).

begin

if (close = close[1]) then

PaintBar(clYellow)

else if (close > close[1]) then

PaintBar(clGreen)

else

PaintBar(clRed);

end;

Se o valor de fechamento da barra atual (Close equivale a Close[0]) for igual ao fechamento da barra anterior
(Representado por Close[1]) executa-se o código que segue a palavra reservada THEN (ENTÃO) . Caso contrário, o sistema executa o código subsequente até chegar na palavra reservada ELSE (SENÃO) .

Exemplo com múltiplas instruções begin e end (inicio e fim)
Quando a listagem (comandos 1 ou comandos 2) contiver mais de uma instrução, é necessário delimitar o bloco com begin (inicio) e end (fim). Veja o exemplo:

begin

if (close = close[1]) then

begin

PaintBar(clYellow);
PlotText("Fechamento igual ao anterior", clYellow);

end

else if (close > close[1]) then

begin

PaintBar(clGreen);
PlotText("Fechamento superior ao anterior", clGreen);

end

else

begin

PaintBar(clRed);
PlotText("Fechamento inferior ao anterior", clRed);

end;

end;

5.2 For (To / DownTo) Do (Para (Até / DownTo) Faça)

O comando FOR (PARA) é utilizado para definir um loop controlado, ou seja, o bloco é executado repetidamente até que a variável de contagem saia do valor inicial e atinja o valor final.

### For (To / DownTo) Do (Para (Até / DownTo) Faça)
*Manual NTSL v4.7 (14/10/2026) — p. 28*

5 Controle de Fluxo

As instruções de fluxo são utilizadas para administrar a sequência de execução das instruções dentro de um programa.
A NTSL apresenta três tipos desse tipo:

5.1 If then else (Se então senão)

Se (condição) for verdadeiro executa-se a listagem (comandos 1), caso (condição) seja falso executa-se (comandos
2). Tanto (comandos 1) quanto (comandos 2) podem ser sequências de instruções.
A expressão (condição) pode ser qualquer tipo de teste que resulte em verdadeiro ou falso, alguns exemplos:

if (Close > Close[1])
if (nIndex = 10)
if (bCond = false) and (Volume > 1000)

A seguir um exemplo de coloração de candles de acordo com a condição presente no If then else (Se então senão).

begin

if (close = close[1]) then

PaintBar(clYellow)

else if (close > close[1]) then

PaintBar(clGreen)

else

PaintBar(clRed);

end;

Se o valor de fechamento da barra atual (Close equivale a Close[0]) for igual ao fechamento da barra anterior
(Representado por Close[1]) executa-se o código que segue a palavra reservada THEN (ENTÃO) . Caso contrário, o sistema executa o código subsequente até chegar na palavra reservada ELSE (SENÃO) .

Exemplo com múltiplas instruções begin e end (inicio e fim)
Quando a listagem (comandos 1 ou comandos 2) contiver mais de uma instrução, é necessário delimitar o bloco com begin (inicio) e end (fim). Veja o exemplo:

begin

if (close = close[1]) then

begin

PaintBar(clYellow);
PlotText("Fechamento igual ao anterior", clYellow);

end

else if (close > close[1]) then

begin

PaintBar(clGreen);
PlotText("Fechamento superior ao anterior", clGreen);

end

else

begin

PaintBar(clRed);
PlotText("Fechamento inferior ao anterior", clRed);

end;

end;

5.2 For (To / DownTo) Do (Para (Até / DownTo) Faça)

O comando FOR (PARA) é utilizado para definir um loop controlado, ou seja, o bloco é executado repetidamente até que a variável de contagem saia do valor inicial e atinja o valor final.

Para a variável controladora, pode-se incrementá-la, a partir do comando To (Até), ou decrementá-la, ao utilizar na estrutura o DownTo.

Importante: O laço FOR (PARA) em NTSL aceita apenas valores inteiros para a variável de controle e para os limites de iteração (To / DownTo). O uso de variáveis ou expressões do tipo Float não é suportado e resultará em comportamento inválido.

Exemplo (For To Do (Para Até Faça)):
Observe o código da média móvel, a variável de contagem nIndex começa com o valor 0 e deve chegar ao valor de
Periodo – 1. No exemplo, Periodo foi definido como parâmetro de entrada, para definir o tamanho da média.
Assim, caso seja parametrizado o valor 0 (Periodo), o comando FOR criará um loop de 9 iterações (de 0 até 8) para cada barra, calculando assim o valor médio para a posição atual.

input

Preco(close);
Periodo(9);

var

sResult : Float;
nIndex

: Integer;

begin

sResult := 0;
for nIndex := 0 to Periodo - 1 do

begin

sResult := sResult + Preco[nIndex];

end;

Plot(sResult / Periodo);

end;

Exemplo (For To Do x For DownTo Do (Para Até Faça x Para DownTo Faça)):
A fim didático, segue um exemplo de cálculo de fatorial, utilizando as duas estruturas.
For To Do (Para Até Faça):

input

n(6);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
For i := 1 To n Do

fatorial := fatorial * i;

Plot(fatorial);

end;

For DownTo Do (Para DownTo Faça):

input

n(6);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
For i := n DownTo 1 Do

fatorial := fatorial * i;

Plot(fatorial);

end;

### While (Enquanto)
*Manual NTSL v4.7 (14/10/2026) — p. 30*

A execução da estratégia ao chegar no comando WHILE testa o resultado de (condição). Caso (condição) seja verdadeiro (true) a listagem (comandos) é executada. Após a execução a (condição) volta a ser testada, assim, o loop apenas irá se encerrar quando (condição) deixar de ser verdadeira.
Exemplo:
No código a seguir, reescrevemos o indicador média móvel utilizando a instrução WHILE (ENQUANTO) ao invés de
FOR (PARA) .

input

Preco(close);
Periodo(9);

var

sResult : Float;
nIndex

: Integer;

begin

sResult := 0;
nIndex := 0;
while (nIndex <= Periodo - 1) do

begin

sResult := sResult + Preco[nIndex];
nIndex := nIndex + 1;

end;

Plot(sResult / Periodo);

end;

5.4 Repeat (Repita)

Este comando difere-se do For e While, no sentido de que a condição será testada no final da estrutura, e não no início, portanto, as instruções do bloco serão executadas pelo menos uma vez.
Exemplo:
A fim de comparação com as outras estruturas já abordadas, segue o exemplo de cálculo de fatorial:

input

n(5);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
i := 1;
repeat

begin

fatorial := fatorial * i;
i := i + 1;

end

until (i > n);
Plot(fatorial);

end;

### Repeat (Repita)
*Manual NTSL v4.7 (14/10/2026) — p. 30*

5.3 While (Enquanto)

A execução da estratégia ao chegar no comando WHILE testa o resultado de (condição). Caso (condição) seja verdadeiro (true) a listagem (comandos) é executada. Após a execução a (condição) volta a ser testada, assim, o loop apenas irá se encerrar quando (condição) deixar de ser verdadeira.
Exemplo:
No código a seguir, reescrevemos o indicador média móvel utilizando a instrução WHILE (ENQUANTO) ao invés de
FOR (PARA) .

input

Preco(close);
Periodo(9);

var

sResult : Float;
nIndex

: Integer;

begin

sResult := 0;
nIndex := 0;
while (nIndex <= Periodo - 1) do

begin

sResult := sResult + Preco[nIndex];
nIndex := nIndex + 1;

end;

Plot(sResult / Periodo);

end;

5.4 Repeat (Repita)

Este comando difere-se do For e While, no sentido de que a condição será testada no final da estrutura, e não no início, portanto, as instruções do bloco serão executadas pelo menos uma vez.
Exemplo:
A fim de comparação com as outras estruturas já abordadas, segue o exemplo de cálculo de fatorial:

input

n(5);

var

fatorial : Integer;
i
: Integer;
begin

fatorial := 1;
i := 1;
repeat

begin

fatorial := fatorial * i;
i := i + 1;

end

until (i > n);
Plot(fatorial);

end;

## Operadores

### Operadores
*Manual NTSL v4.7 (14/10/2026) — p. 31*

Operadores

Os operadores constituem os símbolos matemáticos e lógicos usados em cálculos e comparações.

6.1 Operadores matemáticos

Os operadores matemáticos são:

Operador

+

-

*

/

Descrição

Adição

Subtração

Multiplicação

Divisão

Exemplo

Resultado

5+4

5-4

5*4

5/4

1,25

O operador de divisão possui a maior força de precedência, seguido por multiplicação. Assim, como consta na imagem abaixo:

Expressão

10*10/5+2

10*10+2

50+100*10/2-2

Resultado

6.2 Operadores lógicos

Os operadores lógicos são usados principalmente para comparações e para combinar várias condições em uma expressão lógica. Aqui está uma explicação de seu uso:

"E" lógico
Representado pela palavra reservada and (e), retornará TRUE somente quando as duas condições de teste forem verdadeiras conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

AND

AND

AND

AND

AND

Condição 2

Resultado

FALSE

TRUE

FALSE

TRUE

FALSE

FALSE

FALSE

TRUE

"OU" lógico
Representado pela palavra reservada or (ou), retornará TRUE (verdadeiro) sempre que pelo menos uma das condições de teste for verdadeira, conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

OR

OR

OR

OR

OR

Condição 2

Resultado

FALSE

TRUE

TRUE

TRUE

FALSE

TRUE

FALSE

TRUE

"NOT" lógico
Representado pela palavra reservada not (não), retornará TRUE (verdadeiro) quando uma condição de teste for falsa, conforme tabela verdade abaixo:

Condição

FALSE

TRUE

NOT

NOT

NOT

Resultado

TRUE

FALSE

6.3 Operadores de Comparação

Os operadores de comparação disponíveis na linguagem NTSL são utilizados para comparar valores e avaliar condições lógicas.

Operador

>

<

>=

<=

=

<>

Descrição

Maior que

Menor que

Maior ou igual

Menor ou igual

Igual

Diferente

Exemplo (condição verdadeira)

5 > 4;

4 < 5;

5 >= 5;

6 >= 5

5 <= 5;

4 <= 5

4 = 4;

5 = 5

5 <> 4;

4 <> 5

### Operadores matemáticos
*Manual NTSL v4.7 (14/10/2026) — p. 31*

6 Operadores

Os operadores constituem os símbolos matemáticos e lógicos usados em cálculos e comparações.

6.1 Operadores matemáticos

Os operadores matemáticos são:

Operador

+

-

*

/

Descrição

Adição

Subtração

Multiplicação

Divisão

Exemplo

Resultado

5+4

5-4

5*4

5/4

1,25

O operador de divisão possui a maior força de precedência, seguido por multiplicação. Assim, como consta na imagem abaixo:

Expressão

10*10/5+2

10*10+2

50+100*10/2-2

Resultado

6.2 Operadores lógicos

Os operadores lógicos são usados principalmente para comparações e para combinar várias condições em uma expressão lógica. Aqui está uma explicação de seu uso:

"E" lógico
Representado pela palavra reservada and (e), retornará TRUE somente quando as duas condições de teste forem verdadeiras conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

AND

AND

AND

AND

AND

Condição 2

Resultado

FALSE

TRUE

FALSE

TRUE

FALSE

FALSE

FALSE

TRUE

"OU" lógico
Representado pela palavra reservada or (ou), retornará TRUE (verdadeiro) sempre que pelo menos uma das condições de teste for verdadeira, conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

OR

OR

OR

OR

OR

Condição 2

Resultado

FALSE

TRUE

TRUE

TRUE

FALSE

TRUE

FALSE

TRUE

### Operadores lógicos
*Manual NTSL v4.7 (14/10/2026) — p. 31*

6 Operadores

Os operadores constituem os símbolos matemáticos e lógicos usados em cálculos e comparações.

6.1 Operadores matemáticos

Os operadores matemáticos são:

Operador

+

-

*

/

Descrição

Adição

Subtração

Multiplicação

Divisão

Exemplo

Resultado

5+4

5-4

5*4

5/4

1,25

O operador de divisão possui a maior força de precedência, seguido por multiplicação. Assim, como consta na imagem abaixo:

Expressão

10*10/5+2

10*10+2

50+100*10/2-2

Resultado

6.2 Operadores lógicos

Os operadores lógicos são usados principalmente para comparações e para combinar várias condições em uma expressão lógica. Aqui está uma explicação de seu uso:

"E" lógico
Representado pela palavra reservada and (e), retornará TRUE somente quando as duas condições de teste forem verdadeiras conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

AND

AND

AND

AND

AND

Condição 2

Resultado

FALSE

TRUE

FALSE

TRUE

FALSE

FALSE

FALSE

TRUE

"OU" lógico
Representado pela palavra reservada or (ou), retornará TRUE (verdadeiro) sempre que pelo menos uma das condições de teste for verdadeira, conforme tabela verdade abaixo:

Condição 1

FALSE

FALSE

TRUE

TRUE

OR

OR

OR

OR

OR

Condição 2

Resultado

FALSE

TRUE

TRUE

TRUE

FALSE

TRUE

FALSE

TRUE

### Operadores de Comparação
*Manual NTSL v4.7 (14/10/2026) — p. 32*

"NOT" lógico
Representado pela palavra reservada not (não), retornará TRUE (verdadeiro) quando uma condição de teste for falsa, conforme tabela verdade abaixo:

Condição

FALSE

TRUE

NOT

NOT

NOT

Resultado

TRUE

FALSE

6.3 Operadores de Comparação

Os operadores de comparação disponíveis na linguagem NTSL são utilizados para comparar valores e avaliar condições lógicas.

Operador

>

<

>=

<=

=

<>

Descrição

Maior que

Menor que

Maior ou igual

Menor ou igual

Igual

Diferente

Exemplo (condição verdadeira)

5 > 4;

4 < 5;

5 >= 5;

6 >= 5

5 <= 5;

4 <= 5

4 = 4;

5 = 5

5 <> 4;

4 <> 5

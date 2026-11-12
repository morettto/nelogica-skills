# 04 Funcoes E Procedimentos

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Function (Função)

### Function (Função)
*Manual NTSL v4.7 (14/10/2026) — p. 33*

Function (Função)

Conforme visto, funções são declaradas e descritas na área de declaração de variáveis e funções, abaixo um exemplo de funções:

Observe que primeiro é declarada a variável usada na área principal. É sempre interessante manter o código o mais claro e organizado possível e as funções desempenham um papel fundamental nessa tarefa.

Importante: variáveis declaradas no início do código (variáveis globais) não podem ser utilizadas diretamente dentro de funções. Cada função possui seu próprio escopo, sendo permitido o uso apenas de:

• Variáveis locais declaradas dentro da própria função;

• Parâmetros recebidos pela função.

Caso seja necessário utilizar valores externos, estes devem ser passados explicitamente como parâmetros da função.

7.1 Criando Funções (Sintaxe)

Função NomedaFunção (parâmetro1 : Tipo;
parâmetro2 : Tipo; parâmetroN : Tipo): Tipo de Retorno;
begin

Comandos

end;

Exemplo Correto: Uso de Parâmetros

No exemplo abaixo, os valores externos são declarados na área principal do código e passados explicitamente como parâmetros para a função.

var

nPeriodo : Integer;
nValor nMedia

: Float;
: Float;

Function CalcMediaSimples(Valor : Float; Periodo : Integer) : Float;
begin

CalcMediaSimples := Valor / Periodo;

end;
begin

nPeriodo := 10;
nValor nMedia := CalcMediaSimples(nValor, nPeriodo);
Plot(nMedia);

:= 100;

end;

Neste caso, a função é independente do contexto externo, tornando-se reutilizável, segura e previsível.

Exemplo Incorreto: Uso de Variáveis Globais

O exemplo abaixo ilustra um uso incorreto de funções, onde variáveis globais são acessadas diretamente dentro da função.

var

nPeriodo : Integer;
nValor

: Float;

Function CalcMediaSimples() : Float;
begin

CalcMediaSimples := nValor / nPeriodo;

end;

Atenção: o acesso direto a variáveis globais dentro de funções não é permitido em NTSL e resultará em compor- tamento inválido ou erro de compilação.

7.2 Funções de biblioteca

Além do usuário poder criar seus próprios indicadores, é possível utilizar a biblioteca do sistema, ou seja, o usuário pode utilizar estratégias já criadas em novas.
Dentro das funcionalidades de bibliotecas, o usuário poderá colorir os gráficos de acordo com as condições determi- nadas pelo seu indicador.

### Criando Funções (Sintaxe)
*Manual NTSL v4.7 (14/10/2026) — p. 33*

7 Function (Função)

Conforme visto, funções são declaradas e descritas na área de declaração de variáveis e funções, abaixo um exemplo de funções:

Observe que primeiro é declarada a variável usada na área principal. É sempre interessante manter o código o mais claro e organizado possível e as funções desempenham um papel fundamental nessa tarefa.

Importante: variáveis declaradas no início do código (variáveis globais) não podem ser utilizadas diretamente dentro de funções. Cada função possui seu próprio escopo, sendo permitido o uso apenas de:

• Variáveis locais declaradas dentro da própria função;

• Parâmetros recebidos pela função.

Caso seja necessário utilizar valores externos, estes devem ser passados explicitamente como parâmetros da função.

7.1 Criando Funções (Sintaxe)

Função NomedaFunção (parâmetro1 : Tipo;
parâmetro2 : Tipo; parâmetroN : Tipo): Tipo de Retorno;
begin

Comandos

end;

Exemplo Correto: Uso de Parâmetros

No exemplo abaixo, os valores externos são declarados na área principal do código e passados explicitamente como parâmetros para a função.

### Funções de biblioteca
*Manual NTSL v4.7 (14/10/2026) — p. 34*

var

nPeriodo : Integer;
nValor nMedia

: Float;
: Float;

Function CalcMediaSimples(Valor : Float; Periodo : Integer) : Float;
begin

CalcMediaSimples := Valor / Periodo;

end;
begin

nPeriodo := 10;
nValor nMedia := CalcMediaSimples(nValor, nPeriodo);
Plot(nMedia);

:= 100;

end;

Neste caso, a função é independente do contexto externo, tornando-se reutilizável, segura e previsível.

Exemplo Incorreto: Uso de Variáveis Globais

O exemplo abaixo ilustra um uso incorreto de funções, onde variáveis globais são acessadas diretamente dentro da função.

var

nPeriodo : Integer;
nValor

: Float;

Function CalcMediaSimples() : Float;
begin

CalcMediaSimples := nValor / nPeriodo;

end;

Atenção: o acesso direto a variáveis globais dentro de funções não é permitido em NTSL e resultará em compor- tamento inválido ou erro de compilação.

7.2 Funções de biblioteca

Além do usuário poder criar seus próprios indicadores, é possível utilizar a biblioteca do sistema, ou seja, o usuário pode utilizar estratégias já criadas em novas.
Dentro das funcionalidades de bibliotecas, o usuário poderá colorir os gráficos de acordo com as condições determi- nadas pelo seu indicador.

## Procedure (Procedimento)

### Procedure (Procedimento)
*Manual NTSL v4.7 (14/10/2026) — p. 35*

Procedure (Procedimento)

Procedures são semelhantes às funções, mas não retornam um valor. Elas são usadas para agrupar comandos que podem ser chamados em diferentes partes do código, ajudando a manter a organização e legibilidade. A seguir, temos um exemplo prático de uma procedure para abrir posições no mercado com base em parâmetros.

8.1 Criando Procedimentos (Sintaxe)

procedimento NomeDaProcedure(parâmetro1 : Tipo;
parâmetro2 : Tipo; parâmetroN : Tipo);
begin

Comandos

end;

### Criando Procedimentos (Sintaxe)
*Manual NTSL v4.7 (14/10/2026) — p. 35*

8 Procedure (Procedimento)

Procedures são semelhantes às funções, mas não retornam um valor. Elas são usadas para agrupar comandos que podem ser chamados em diferentes partes do código, ajudando a manter a organização e legibilidade. A seguir, temos um exemplo prático de uma procedure para abrir posições no mercado com base em parâmetros.

8.1 Criando Procedimentos (Sintaxe)

procedimento NomeDaProcedure(parâmetro1 : Tipo;
parâmetro2 : Tipo; parâmetroN : Tipo);
begin

Comandos

end;

## Initialization

### Initialization
*Manual NTSL v4.7 (14/10/2026) — p. 36*

Initialization

O bloco Initialization permite a execução de um conjunto de instruções apenas uma única vez durante todo o ciclo de vida da estratégia, de forma semelhante ao bloco initialization da linguagem Delphi. O uso desse bloco é opcional.

Descrição

As instruções contidas no bloco Initialization são executadas somente na inicialização da estratégia, não se repetindo durante a execução normal e não dependendo do fluxo de candles ou ticks do gráfico. Esse bloco é indicado para inicialização de variáveis, estados internos e configurações que não devem ser reavaliadas a cada ciclo de execução.

**Sintaxe**

```ntsl
O bloco Initialization deve conter obrigatoriamente um par begin / end e pode ser declarado antes ou depois
do código principal da estratégia.
Initialization antes do código principal:

Initialization
begin

nValue := 5;

end;

begin

Plot(nValue);

end;

Initialization após o código principal:

begin

Plot(nValue);

end;

Initialization
begin

nValue := 5;

end;

Regras de Uso

• Pode existir apenas um bloco Initialization por estratégia.

• Não pode haver nenhum código entre o bloco principal e o bloco Initialization, independentemente de sua

posição.

• O bloco Initialization não pode ser declarado dentro de funções ou procedures definidas na própria es-

tratégia.

• É permitido o uso de Initialization em arquivos externos chamados por outra estratégia. Nesse caso, o

código será executado sempre que o arquivo externo for carregado.

Comportamento de Execução

Durante a compilação, o código do bloco Initialization é integrado ao fluxo normal da estratégia. Em tempo de
execução:

• A execução inicia pelo bloco Initialization.

• Após sua execução completa, o fluxo é automaticamente direcionado para o início da execução normal da

estratégia.

• O bloco Initialization não será executado novamente até que a estratégia seja reiniciada.

Importante: O bloco Initialization não substitui a execução normal da estratégia, sendo utilizado apenas para
lógica de inicialização.
```

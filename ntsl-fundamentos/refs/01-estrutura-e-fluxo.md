# 01 Estrutura E Fluxo

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Introdução

### Introdução
*Manual NTSL v4.7 (14/10/2026) — p. 11*

Introdução

A NTSL (Nelogica Trading System Language) é uma linguagem avançada desenvolvida para a criação de sistemas algorítmicos de operação com alto desempenho e eficiência. Projetada para atender às necessidades de traders e investidores, a NTSL permite a implementação de estratégias automatizadas de forma intuitiva e flexível. Seu grande diferencial é a facilidade de uso, possibilitando a escrita de códigos em português, tornando o desenvolvimento e a compreensão das estratégias mais acessíveis para todos os usuários.

2 Estrutura de uma Estratégia

Observe o trecho de código abaixo que representa o indicador média móvel. Esse código apresenta as três áreas que definem a estrutura de uma estratégia. São elas: área de declaração de parâmetros de entrada, área de declaração de variáveis e funções e área de código.

A área de parâmetros de entrada compreende toda a região entre a palavra reservada input (parâmetro) e a palavra reservada var. A área de variáveis e funções começa com a palavra var e estende-se até a palavra begin (inicio).
Finalmente, a região de código inicia-se com a palavra reservada begin (inicio) e finaliza na palavra end (fim), conforme imagem abaixo:

Entrada

input (parametro)

Variáveis e Funções

var

Código

begin (inicio)
end (fim)

## Estrutura de uma Estratégia

### Estrutura de uma Estratégia
*Manual NTSL v4.7 (14/10/2026) — p. 11*

Introdução

A NTSL (Nelogica Trading System Language) é uma linguagem avançada desenvolvida para a criação de sistemas algorítmicos de operação com alto desempenho e eficiência. Projetada para atender às necessidades de traders e investidores, a NTSL permite a implementação de estratégias automatizadas de forma intuitiva e flexível. Seu grande diferencial é a facilidade de uso, possibilitando a escrita de códigos em português, tornando o desenvolvimento e a compreensão das estratégias mais acessíveis para todos os usuários.

2 Estrutura de uma Estratégia

Observe o trecho de código abaixo que representa o indicador média móvel. Esse código apresenta as três áreas que definem a estrutura de uma estratégia. São elas: área de declaração de parâmetros de entrada, área de declaração de variáveis e funções e área de código.

A área de parâmetros de entrada compreende toda a região entre a palavra reservada input (parâmetro) e a palavra reservada var. A área de variáveis e funções começa com a palavra var e estende-se até a palavra begin (inicio).
Finalmente, a região de código inicia-se com a palavra reservada begin (inicio) e finaliza na palavra end (fim), conforme imagem abaixo:

Entrada

input (parametro)

Variáveis e Funções

var

Código

begin (inicio)
end (fim)

2.1 Área de declaração de parâmetros de entrada

Na área de declaração de parâmetros de entrada informamos todos os parâmetros externos que a estratégia usará.
Esses parâmetros são fundamentais, pois:

• Definem a interface com o mundo externo, ou seja, é onde usuário poderá alterar e o que servirá como parâmetro

de chamada caso a estratégia seja utilizada em outra interface/estratégia.

• Define os itens que serão analisados no processo de otimização.

Para definir um parâmetro: NOME_DO_PARÂMETRO (VALOR_DE_INICIALIZAÇÃO)

Exemplo:

Input

Preço (Close);

Período (2);

Definição

Define um parâmetro inicializado com o valor de fechamento de preços da série de dados.

Define um parâmetro chamado Período com o valor 2.

2.2 Área de declaração de variáveis e funções

Na área de declaração de variáveis informamos todas as variáveis que serão utilizadas na estratégia. Nesta região também descrevemos funções que desejamos usar no código. As funções devem ser sempre codificadas após a declaração das variáveis.
Para declarar uma variável: NOME_DA_VARIAVEL: TIPO

Exemplo:

Variável

sResult : Float;

nIndex : Integer;

Definição

Cria uma variável chamada sResult do tipo ponto flutuante.

Cria uma variável chamada nIndex para armazenar número inteiros.

2.3 Área de código

Nesta parte descreve-se o código propriamente dito, ou seja, as regras que utilizam parâmetros, variáveis e outros dados para calcular sinais e indicadores.

### Área de declaração de parâmetros de entrada
*Manual NTSL v4.7 (14/10/2026) — p. 12*

Na área de declaração de parâmetros de entrada informamos todos os parâmetros externos que a estratégia usará.
Esses parâmetros são fundamentais, pois:

• Definem a interface com o mundo externo, ou seja, é onde usuário poderá alterar e o que servirá como parâmetro

de chamada caso a estratégia seja utilizada em outra interface/estratégia.

• Define os itens que serão analisados no processo de otimização.

Para definir um parâmetro: NOME_DO_PARÂMETRO (VALOR_DE_INICIALIZAÇÃO)

Exemplo:

Input

Preço (Close);

Período (2);

Definição

Define um parâmetro inicializado com o valor de fechamento de preços da série de dados.

Define um parâmetro chamado Período com o valor 2.

2.2 Área de declaração de variáveis e funções

Na área de declaração de variáveis informamos todas as variáveis que serão utilizadas na estratégia. Nesta região também descrevemos funções que desejamos usar no código. As funções devem ser sempre codificadas após a declaração das variáveis.
Para declarar uma variável: NOME_DA_VARIAVEL: TIPO

Exemplo:

Variável

sResult : Float;

nIndex : Integer;

Definição

Cria uma variável chamada sResult do tipo ponto flutuante.

Cria uma variável chamada nIndex para armazenar número inteiros.

2.3 Área de código

Nesta parte descreve-se o código propriamente dito, ou seja, as regras que utilizam parâmetros, variáveis e outros dados para calcular sinais e indicadores.

### Área de declaração de variáveis e funções
*Manual NTSL v4.7 (14/10/2026) — p. 12*

2.1 Área de declaração de parâmetros de entrada

Na área de declaração de parâmetros de entrada informamos todos os parâmetros externos que a estratégia usará.
Esses parâmetros são fundamentais, pois:

• Definem a interface com o mundo externo, ou seja, é onde usuário poderá alterar e o que servirá como parâmetro

de chamada caso a estratégia seja utilizada em outra interface/estratégia.

• Define os itens que serão analisados no processo de otimização.

Para definir um parâmetro: NOME_DO_PARÂMETRO (VALOR_DE_INICIALIZAÇÃO)

Exemplo:

Input

Preço (Close);

Período (2);

Definição

Define um parâmetro inicializado com o valor de fechamento de preços da série de dados.

Define um parâmetro chamado Período com o valor 2.

2.2 Área de declaração de variáveis e funções

Na área de declaração de variáveis informamos todas as variáveis que serão utilizadas na estratégia. Nesta região também descrevemos funções que desejamos usar no código. As funções devem ser sempre codificadas após a declaração das variáveis.
Para declarar uma variável: NOME_DA_VARIAVEL: TIPO

Exemplo:

Variável

sResult : Float;

nIndex : Integer;

Definição

Cria uma variável chamada sResult do tipo ponto flutuante.

Cria uma variável chamada nIndex para armazenar número inteiros.

2.3 Área de código

Nesta parte descreve-se o código propriamente dito, ou seja, as regras que utilizam parâmetros, variáveis e outros dados para calcular sinais e indicadores.

### Área de código
*Manual NTSL v4.7 (14/10/2026) — p. 12*

2.1 Área de declaração de parâmetros de entrada

Na área de declaração de parâmetros de entrada informamos todos os parâmetros externos que a estratégia usará.
Esses parâmetros são fundamentais, pois:

• Definem a interface com o mundo externo, ou seja, é onde usuário poderá alterar e o que servirá como parâmetro

de chamada caso a estratégia seja utilizada em outra interface/estratégia.

• Define os itens que serão analisados no processo de otimização.

Para definir um parâmetro: NOME_DO_PARÂMETRO (VALOR_DE_INICIALIZAÇÃO)

Exemplo:

Input

Preço (Close);

Período (2);

Definição

Define um parâmetro inicializado com o valor de fechamento de preços da série de dados.

Define um parâmetro chamado Período com o valor 2.

2.2 Área de declaração de variáveis e funções

Na área de declaração de variáveis informamos todas as variáveis que serão utilizadas na estratégia. Nesta região também descrevemos funções que desejamos usar no código. As funções devem ser sempre codificadas após a declaração das variáveis.
Para declarar uma variável: NOME_DA_VARIAVEL: TIPO

Exemplo:

Variável

sResult : Float;

nIndex : Integer;

Definição

Cria uma variável chamada sResult do tipo ponto flutuante.

Cria uma variável chamada nIndex para armazenar número inteiros.

2.3 Área de código

Nesta parte descreve-se o código propriamente dito, ou seja, as regras que utilizam parâmetros, variáveis e outros dados para calcular sinais e indicadores.

## Fluxo de Execução de uma Estratégia

### Fluxo de Execução de uma Estratégia
*Manual NTSL v4.7 (14/10/2026) — p. 13*

Fluxo de Execução de uma Estratégia

O código de uma estratégia é executado de maneira sequencial. Porém, ele é executado sequencialmente candle por candle, como se houvesse um laço que percorre toda série de dados de um ativo.
Sendo assim, a sequência de comandos existente na área de código será executada uma vez para cada candle existente. Para cada candle, será executado o código da estratégia em um loop implícito. A regra em pseudocódigo é, portanto:

• Tendo uma série de dados X de tamanho N;

• Para cada item X[i], com i variando de 0 até N-1, executa-se a área de código da estratégia;

• A cada novo dado do ativo, o código da estratégia continua sendo executado, avaliando o último e o penúltimo

candle;

Importante:

• O mesmo candle pode ser processado diversas vezes. Isso ocorre muito em tempo real, onde cada trade pode

gerar uma notificação de reprocessamento do fluxo de execução.

• Quando uma ordem é executada, o fluxo de execução reprocessa o mesmo candle para ativar as ordens Covers.

• Dependendo da notificação dos candles, podem ser reprocessados candles passados. Isso deve ser levado em

consideração pelo programador.

• Sempre que um candle passado é reprocessado, serão reprocessados todos candles até o atual.

• Em tempo real, quando o código está executando ao mesmo tempo que recebe novos dados do mercado, o código da estratégia é executado diversas vezes para o último e o penúltimo candle durante a execução, podendo também executar em candles passados.

Esses processamentos podem alterar valores de variáveis globais ou de série, e podem causar mudanças na coloração para candles passados ou mudança de comportamento quando o código é pausado e executado novamente.
Quando estiver utilizando séries em sua estratégia, é importante lembrar que o primeiro tick do candle terá o valor
[0] zerado. Como comentamos anteriormente, sua estratégia será executada não apenas no último candle e sim também ao passado, devido aos cálculos que precisam ser feitos para garantir que a NTSL funcione corretamente.
É importante ressaltar que não se pode assumir que um candle no passado não será avaliado, porém, se desejar, é possível inibir o recálculo de algum valor utilizando a função LastBarOnChart() em uma condição no início do código para evitar isso. É fundamental compreender que o [0] sempre está se referindo ao candle que está sendo avaliado, e não necessariamente será do último candle.

Abaixo, um exemplo de como uma variável arbitrária "nValor" funcionaria caso o último candle estivesse sendo avaliado. Caso eu quisesse acessar o valor dela há 2 candles passados, utilizaria "nValor[2]".

Porém, caso o código esteja sendo executado em um candle no passado, o nValor[0] seria referente ao candle atual do processamento, e não ao último candle como no exemplo passado. Os outros candles também seriam acessados com base no candle que está sendo processado no momento, como no exemplo abaixo.

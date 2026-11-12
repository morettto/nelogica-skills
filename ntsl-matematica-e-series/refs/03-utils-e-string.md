# 03 Utils E String

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções Utils

### Funções Utils
*Manual NTSL v4.7 (14/10/2026) — p. 564*

Funções Utils

26.1 Função AssetHasValue

_A função AssetHasValue() retorna se o ativo escolhido tem valor de mercado ou não._

**Sintaxe**

```ntsl
Função AssetHasValue(Asset: Ativo): Boolean;
```

**Parâmetros**

Asset: Ativo; Ativo escolhido para a função.

**Exemplo de uso:** caso o ativo PETR4 tenha valor de mercado.
const

```ntsl
No exemplo abaixo, será plotado no gráfico o melhor preço de venda do ativo, usando a função AskPrice(),
PETR = Asset("PETR4", feedBovespa);
begin
if AssetHasValue(PETR) then
Plot(AskPrice);
end
```

**Gráfico:** ver exemplo no manual, p. 564

_A função BoolToString() transforma um valor booleano em um string._

**Sintaxe**

```ntsl
Função BoolToString(Content: Boolean): String;
```

**Parâmetros**

Content: Boolean; Valor booleano escolhido para ser transformado em string.

**Exemplo de uso:** No exemplo abaixo, será plotado no gráfico o texto da variavel compare caso o ativo PETR4 tenha valor de mercado.
const

```ntsl
PETR4 = Asset("PETR4", feedBovespa);
var
compare : Boolean;
begin
compare := AssetHasValue(PETR4);
if compare then
PlotText(BoolToString(compare), clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 564

**Sintaxe**

```ntsl
Função CompareFloat(Valor_1: Float; Valor_2: Float; DígitosPrecisao: Integer = 9):

Integer;
```

**Parâmetros**

Valor_1: Float; Primeiro valor a ser comparado.

Valor_2: Float; Segundo valor a ser comparado.

DígitosPrecisao: Integer [Opcional]; Número de casas decimais a considerar (padrão = 9).

**Exemplo de uso:** No exemplo abaixo, com precisão de 3 dígitos decimais, o resultado da comparação entre 3.141592 e 3.14 será

```ntsl
atribuído à variável resultado, e então exibido com a função Plot().
var
resultado : Integer;
begin
resultado := CompareFloat(3.141592, 3.14, 3);
Plot(resultado);
end;
```

**Gráfico:** ver exemplo no manual, p. 564

**Sintaxe**

```ntsl
Função FloatToString(Valor: Float; Dígitos: Integer): String;
```

**Parâmetros**

Valor: Float; Valor numérico a ser convertido em texto.

Dígitos: Integer [Opcional]; Número de casas decimais exibidas (padrão = 2).

**Exemplo de uso:** No exemplo abaixo, o valor de fechamento do candle atual é convertido para texto com duas casas decimais e

```ntsl
exibido no gráfico em vermelho, utilizando a função PlotText().
begin
PlotText(FloatToString(Close, 2), clRed);
end;
```

### Função AssetHasValue
*Manual NTSL v4.7 (14/10/2026) — p. 564*

26 Funções Utils

26.1 Função AssetHasValue

_A função AssetHasValue() retorna se o ativo escolhido tem valor de mercado ou não._

**Sintaxe**

```ntsl
Função AssetHasValue(Asset: Ativo): Boolean;
```

**Parâmetros**

Asset: Ativo; Ativo escolhido para a função.

**Exemplo de uso:** caso o ativo PETR4 tenha valor de mercado.
const

```ntsl
No exemplo abaixo, será plotado no gráfico o melhor preço de venda do ativo, usando a função AskPrice(),
PETR = Asset("PETR4", feedBovespa);
begin
if AssetHasValue(PETR) then
Plot(AskPrice);
end
```

### Função BoolToString
*Manual NTSL v4.7 (14/10/2026) — p. 565*

_A função BoolToString() transforma um valor booleano em um string._

**Sintaxe**

```ntsl
Função BoolToString(Content: Boolean): String;
```

**Parâmetros**

Content: Boolean; Valor booleano escolhido para ser transformado em string.

**Exemplo de uso:** No exemplo abaixo, será plotado no gráfico o texto da variavel compare caso o ativo PETR4 tenha valor de mercado.
const

```ntsl
PETR4 = Asset("PETR4", feedBovespa);
var
compare : Boolean;
begin
compare := AssetHasValue(PETR4);
if compare then
PlotText(BoolToString(compare), clRed);
end
```

### Função CompareFloat
*Manual NTSL v4.7 (14/10/2026) — p. 565*

26.2 Função BoolToString

_A função BoolToString() transforma um valor booleano em um string._

**Sintaxe**

```ntsl
Função BoolToString(Content: Boolean): String;
```

**Parâmetros**

Content: Boolean; Valor booleano escolhido para ser transformado em string.

**Exemplo de uso:** No exemplo abaixo, será plotado no gráfico o texto da variavel compare caso o ativo PETR4 tenha valor de mercado.
const

```ntsl
PETR4 = Asset("PETR4", feedBovespa);
var
compare : Boolean;
begin
compare := AssetHasValue(PETR4);
if compare then
PlotText(BoolToString(compare), clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 565

**Sintaxe**

```ntsl
Função CompareFloat(Valor_1: Float; Valor_2: Float; DígitosPrecisao: Integer = 9):

Integer;
```

**Parâmetros**

Valor_1: Float; Primeiro valor a ser comparado.

Valor_2: Float; Segundo valor a ser comparado.

DígitosPrecisao: Integer [Opcional]; Número de casas decimais a considerar (padrão = 9).

**Exemplo de uso:** No exemplo abaixo, com precisão de 3 dígitos decimais, o resultado da comparação entre 3.141592 e 3.14 será

```ntsl
atribuído à variável resultado, e então exibido com a função Plot().
var
resultado : Integer;
begin
resultado := CompareFloat(3.141592, 3.14, 3);
Plot(resultado);
end;
```

### Função FloatToString
*Manual NTSL v4.7 (14/10/2026) — p. 567*

A função FloatToString() converte um valor numérico de ponto flutuante em uma String, exibindo o número de casas decimais especificado. Essa função é útil para formatar valores numéricos antes de exibi-los em textos, legendas ou mensagens na tela.

**Sintaxe**

```ntsl
Função FloatToString(Valor: Float; Dígitos: Integer): String;
```

**Parâmetros**

Valor: Float; Valor numérico a ser convertido em texto.

Dígitos: Integer [Opcional]; Número de casas decimais exibidas (padrão = 2).

**Exemplo de uso:** No exemplo abaixo, o valor de fechamento do candle atual é convertido para texto com duas casas decimais e

```ntsl
exibido no gráfico em vermelho, utilizando a função PlotText().
begin
PlotText(FloatToString(Close, 2), clRed);
end;
```

## Funções de String

### Funções de String
*Manual NTSL v4.7 (14/10/2026) — p. 568*

Funções de String

27.1 Função SubString

_A função SubString() retorna o trecho do texto entre os dois índices informados. O caractere da posição EndIndex não entra no resultado. Caso EndIndex seja omitido, o trecho retornado vai de BeginIndex até o fim do texto._

**Sintaxe**

```ntsl
Função SubString(Text: String; BeginIndex: Integer; EndIndex: Integer): String;
```

**Parâmetros**

Text: String; Texto do qual o trecho será extraído.

BeginIndex: Integer; Índice do primeiro caractere do trecho, contado a partir de 0.

EndIndex: Integer [Opcional]; Índice final do trecho, que não entra no resultado. Quando omitido, o trecho vai até o fim do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, são extraídos os quatro primeiros caracteres do ticker do ativo

```ntsl
(índices 0 a 3) e o resultado é exibido com a função PlotText(). Para o ativo PETR4, o texto exibido será PETR.
begin
if LastBarOnChart then
PlotText(SubString(GetAsset, 0, 4), clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 568

_A função StringCopy() retorna o trecho do texto a partir do índice informado, com a quantidade de caracteres definida em Count. Caso Count seja omitido, a cópia vai de Index até o fim do texto._

**Sintaxe**

```ntsl
Função StringCopy(Text: String; Index: Integer; Count: Integer): String;
```

**Parâmetros**

Text: String; Texto do qual o trecho será copiado.

Index: Integer; Índice do primeiro caractere a ser copiado, contado a partir de 0.

Count: Integer [Opcional]; Quantidade de caracteres a serem copiados. Quando omitido, copia até o fim do texto.

**Exemplo de uso:** caracteres, copiados com Count igual a 3, e o restante do texto, copiado sem informar Count. Para o ativo
PETR4, o texto exibido será PET / R4.

```ntsl
No exemplo abaixo, no último candle do gráfico, o ticker do ativo é separado em duas partes: os três primeiros
begin
if LastBarOnChart then
PlotText(StringCopy(GetAsset, 0, 3) + " / " +
StringCopy(GetAsset, 3), clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 568

_A função StringStartsWith() retorna True se o texto começa com o prefixo informado e False caso contrário._

**Sintaxe**

```ntsl
Função StringStartsWith(Text: String; Prefix: String): Boolean;
```

**Parâmetros**

Text: String; Texto a ser verificado.

Prefix: String; Prefixo procurado no início do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, é verificado se o ticker do ativo começa com WIN. Em caso

```ntsl
positivo, é exibido o texto Mini Índice em verde; caso contrário, é exibido o texto Outro ativo em vermelho.
begin
if LastBarOnChart then
begin
if StringStartsWith(GetAsset, "WIN") then
PlotText("Mini Índice", clGreen)
else
PlotText("Outro ativo", clRed);
end;
end;
```

**Gráfico:** ver exemplo no manual, p. 568

_A função StringEndsWith() retorna True se o texto termina com o sufixo informado e False caso contrário._

**Sintaxe**

```ntsl
Função StringEndsWith(Text: String; Suffix: String): Boolean;
```

**Parâmetros**

Text: String; Texto a ser verificado.

Suffix: String; Sufixo procurado no final do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, é verificado se o ticker do ativo termina com FUT, identificando um contrato futuro contínuo, como WINFUT. Em caso positivo, é exibido o texto Contrato contínuo em verde.

```ntsl
begin
if LastBarOnChart then
begin
if StringEndsWith(GetAsset, "FUT") then
PlotText("Contrato contínuo", clGreen);
end;
end;
```

**Gráfico:** ver exemplo no manual, p. 568

_A função StringPos() retorna o índice, contado a partir de 0, da primeira ocorrência do trecho SubText dentro do texto. Caso o trecho não seja encontrado, a função retorna -1._

**Sintaxe**

```ntsl
Função StringPos(Text: String; SubText: String): Integer;
```

**Parâmetros**

Text: String; Texto no qual o trecho será procurado.

SubText: String; Trecho a ser procurado.

**Exemplo de uso:** No exemplo abaixo, é procurada a posição do trecho FUT dentro do ticker do ativo, e o resultado é exibido com
PETR4, o valor exibido será -1.

```ntsl
a função Plot(). Para o ativo WINFUT, o valor exibido será 3; para um ativo que não contenha o trecho, como
var
posicao : Integer;
begin
posicao := StringPos(GetAsset, "FUT");
Plot(posicao);
end;
```

**Gráfico:** ver exemplo no manual, p. 568

_A função StringContains() retorna True se o texto contém o trecho informado, em qualquer posição, e False caso contrário._

**Sintaxe**

```ntsl
Função StringContains(Text: String; SubText: String): Boolean;
```

**Parâmetros**

Text: String; Texto no qual o trecho será procurado.

SubText: String; Trecho a ser procurado.

**Exemplo de uso:** No exemplo abaixo, os candles são pintados de azul quando o ticker do ativo contém o trecho DOL, como nos tickers DOLFUT e DOLZ25. Para o ativo WDOFUT, os candles não são pintados, já que o trecho DOL não aparece no ticker.

```ntsl
begin
if StringContains(GetAsset, "DOL") then
PaintBar(clBlue);
end;
```

### Função SubString
*Manual NTSL v4.7 (14/10/2026) — p. 568*

27 Funções de String

27.1 Função SubString

_A função SubString() retorna o trecho do texto entre os dois índices informados. O caractere da posição EndIndex não entra no resultado. Caso EndIndex seja omitido, o trecho retornado vai de BeginIndex até o fim do texto._

**Sintaxe**

```ntsl
Função SubString(Text: String; BeginIndex: Integer; EndIndex: Integer): String;
```

**Parâmetros**

Text: String; Texto do qual o trecho será extraído.

BeginIndex: Integer; Índice do primeiro caractere do trecho, contado a partir de 0.

EndIndex: Integer [Opcional]; Índice final do trecho, que não entra no resultado. Quando omitido, o trecho vai até o fim do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, são extraídos os quatro primeiros caracteres do ticker do ativo

```ntsl
(índices 0 a 3) e o resultado é exibido com a função PlotText(). Para o ativo PETR4, o texto exibido será PETR.
begin
if LastBarOnChart then
PlotText(SubString(GetAsset, 0, 4), clGreen);
end;
```

### Função StringCopy
*Manual NTSL v4.7 (14/10/2026) — p. 569*

_A função StringCopy() retorna o trecho do texto a partir do índice informado, com a quantidade de caracteres definida em Count. Caso Count seja omitido, a cópia vai de Index até o fim do texto._

**Sintaxe**

```ntsl
Função StringCopy(Text: String; Index: Integer; Count: Integer): String;
```

**Parâmetros**

Text: String; Texto do qual o trecho será copiado.

Index: Integer; Índice do primeiro caractere a ser copiado, contado a partir de 0.

Count: Integer [Opcional]; Quantidade de caracteres a serem copiados. Quando omitido, copia até o fim do texto.

**Exemplo de uso:** caracteres, copiados com Count igual a 3, e o restante do texto, copiado sem informar Count. Para o ativo
PETR4, o texto exibido será PET / R4.

```ntsl
No exemplo abaixo, no último candle do gráfico, o ticker do ativo é separado em duas partes: os três primeiros
begin
if LastBarOnChart then
PlotText(StringCopy(GetAsset, 0, 3) + " / " +
StringCopy(GetAsset, 3), clGreen);
end;
```

### Função StringStartsWith
*Manual NTSL v4.7 (14/10/2026) — p. 570*

_A função StringStartsWith() retorna True se o texto começa com o prefixo informado e False caso contrário._

**Sintaxe**

```ntsl
Função StringStartsWith(Text: String; Prefix: String): Boolean;
```

**Parâmetros**

Text: String; Texto a ser verificado.

Prefix: String; Prefixo procurado no início do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, é verificado se o ticker do ativo começa com WIN. Em caso

```ntsl
positivo, é exibido o texto Mini Índice em verde; caso contrário, é exibido o texto Outro ativo em vermelho.
begin
if LastBarOnChart then
begin
if StringStartsWith(GetAsset, "WIN") then
PlotText("Mini Índice", clGreen)
else
PlotText("Outro ativo", clRed);
end;
end;
```

### Função StringEndsWith
*Manual NTSL v4.7 (14/10/2026) — p. 571*

_A função StringEndsWith() retorna True se o texto termina com o sufixo informado e False caso contrário._

**Sintaxe**

```ntsl
Função StringEndsWith(Text: String; Suffix: String): Boolean;
```

**Parâmetros**

Text: String; Texto a ser verificado.

Suffix: String; Sufixo procurado no final do texto.

**Exemplo de uso:** No exemplo abaixo, no último candle do gráfico, é verificado se o ticker do ativo termina com FUT, identificando um contrato futuro contínuo, como WINFUT. Em caso positivo, é exibido o texto Contrato contínuo em verde.

```ntsl
begin
if LastBarOnChart then
begin
if StringEndsWith(GetAsset, "FUT") then
PlotText("Contrato contínuo", clGreen);
end;
end;
```

### Função StringPos
*Manual NTSL v4.7 (14/10/2026) — p. 572*

_A função StringPos() retorna o índice, contado a partir de 0, da primeira ocorrência do trecho SubText dentro do texto. Caso o trecho não seja encontrado, a função retorna -1._

**Sintaxe**

```ntsl
Função StringPos(Text: String; SubText: String): Integer;
```

**Parâmetros**

Text: String; Texto no qual o trecho será procurado.

SubText: String; Trecho a ser procurado.

**Exemplo de uso:** No exemplo abaixo, é procurada a posição do trecho FUT dentro do ticker do ativo, e o resultado é exibido com
PETR4, o valor exibido será -1.

```ntsl
a função Plot(). Para o ativo WINFUT, o valor exibido será 3; para um ativo que não contenha o trecho, como
var
posicao : Integer;
begin
posicao := StringPos(GetAsset, "FUT");
Plot(posicao);
end;
```

### Função StringContains
*Manual NTSL v4.7 (14/10/2026) — p. 573*

_A função StringContains() retorna True se o texto contém o trecho informado, em qualquer posição, e False caso contrário._

**Sintaxe**

```ntsl
Função StringContains(Text: String; SubText: String): Boolean;
```

**Parâmetros**

Text: String; Texto no qual o trecho será procurado.

SubText: String; Trecho a ser procurado.

**Exemplo de uso:** No exemplo abaixo, os candles são pintados de azul quando o ticker do ativo contém o trecho DOL, como nos tickers DOLFUT e DOLZ25. Para o ativo WDOFUT, os candles não são pintados, já que o trecho DOL não aparece no ticker.

```ntsl
begin
if StringContains(GetAsset, "DOL") then
PaintBar(clBlue);
end;
```

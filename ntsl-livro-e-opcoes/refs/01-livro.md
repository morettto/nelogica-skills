# 01 Livro

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Livro

### Funções de Livro
*Manual NTSL v4.7 (14/10/2026) — p. 458*

Funções de Livro

21.1 Função AskPrice

_A função AskPrice() retorna o preço da melhor oferta de venda._

**Sintaxe**

```ntsl
Função AskPrice(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** venda) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável ask o valor do topo (melhor oferta de
var
ask : Float;
begin
if not HasPosition then
ask := AskPrice;
Plot(ask);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função AskSize() retorna a quantidade da melhor oferta de venda.
Ao utilizar o modo de CrossOrder na automação, o AskSize irá retornar a quantidade do AskSize da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função AskSize(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** oferta de venda) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável qtdask a quantidade do topo (melhor
var
qtdask : Float;
begin
if not HasPosition then
qtdask := AskSize;
Plot(qtdask);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função BidPrice() retorna o preço da melhor oferta de compra._

**Sintaxe**

```ntsl
Função BidPrice(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** compra) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável bid o valor de topo (melhor oferta de
var
bid : Float;
begin
if not HasPosition then
bid := BidPrice;
Plot(bid);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função BidSize() retorna a quantidade da melhor oferta de compra.
Ao utilizar o modo de CrossOrder na automação, o BidSize irá retornar a quantidade do BidSize da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função BidSize(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** oferta de compra) do livro.

```ntsl
No exemplo, caso não tenha posição aberta será atribuído à variável qtdbid. A quantidade do topo (melhor
var
qtdbid : Float;
begin
if not HasPosition then
qtdbid := BidSize;
Plot(qtdbid);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função BookSpread() retorna a diferença entre os melhores preços de compra e venda, no topo do livro._

**Sintaxe**

```ntsl
Função BookSpread(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não tenha posição aberta, será atribuído à variável spread a diferença entre os valores das melhores ofertas de compra e venda.

```ntsl
var
spread : Float;
begin
if not HasPosition then
spread := BookSpread;
Plot(spread);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função BuyOfferCount() retorna as ofertas de compra do ativo_

**Sintaxe**

```ntsl
Função BuyOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " " (ativo do gráfico).

Níveis considerados: Integer [Opcional]; Define quantos níveis de preço serão considerados no cálculo.
Valor padrão é 0.

Importante: Caso deseje informar somente o parâmetro Níveis considerados, é obrigatório também informar explicitamente o parâmetro Asset.

**Exemplo de uso:** No exemplo 1, é plotado o total de ofertas de compra do ativo do gráfico.
No exemplo 2, sem posição aberta, é atribuído à variável buyCount o número de ofertas de compra do ativo
VALE3, considerando 3 níveis de preço.
const
21.7 Função GetAsset

```ntsl
Exemplo 1:
begin
Plot(BuyOfferCount);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
buyCount : Integer;
begin
if not HasPosition then
buyCount := BuyOfferCount(VALE3,3);
Plot(buyCount);
end;
Exemplo Gráfico 2:
```

_A função GetAsset() retorna o ticker do ativo, onde a chamada pode ser efetuada realizando a passagem do parâmetro opcional, para retornar o ticker de determinado Asset, ou declarar a função sem parametrização, onde será retornado o ticker do gráfico selecionado.
Para retornar o ticker (String) do Asset declarado, basta acessar de forma análoga às séries de dados: A1.GetAsset._

**Sintaxe**

```ntsl
Função GetAsset(Asset: Ativo): String;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

**Exemplo de uso:** No exemplo 1, para o último candle, será visualizado o nome do ativo selecionado no gráfico, com os preços de bid e ask.
ativo selecionado no gráfico.
const
21.8 Função GetFeed

```ntsl
No exemplo 2, a distinção está na especificação do Asset que será exibido (WDOFUT), independentemente do
Exemplo 1:
var
bid : Float;
ask : Float;
get : String;
begin
if (MaxBarsForward = 0) then
begin
get := GetAsset;
bid := BidPrice;
ask := AskPrice;
plotText((get + ": " + "Bid =" + bid + " Ask=" + ask),clGreen,2,8);
end;
end;
Exemplo Gráfico 1:
Exemplo 2:
WDO = Asset("WDOFUT", feedBMF);
var
bid : Float;
ask : Float;
get : String;
begin
if (MaxBarsForward = 0) then
begin
get := GetAsset(WDO);
bid := BidPrice;
ask := AskPrice;
plotText((get + ":" + " Bid =" + bid + " Ask=" + ask),clGreen,2,8);;
end
end;
Exemplo Gráfico 2:
```

_A função GetFeed() retorna o código textual do Feed do ativo.
A parametrização é opcional, caso não seja determinado o Asset, será retornado o ticker do gráfico selecionado.
Para retornar a bolsa relacionada (String) do Asset específico, pode-se acessar de forma análoga às séries de dados:
A1.GetFeed._

**Sintaxe**

```ntsl
Função GetFeed(Asset: Ativo): String;
```

**Parâmetros**

Asset: Ativo [Opcional]; Constante declarada a partir do recurso Asset.

**Exemplo de uso:** No exemplo 1, para o último candle, será visualizado o nome do ativo selecionado no gráfico, a bolsa a qual pertence, e o spread do book.
selecionado.
const
21.9 Função IsBMF

```ntsl
No exemplo 2, será identificada a bolsa (F) vinculada ao Asset definido (WDO), independentemente do ativo
Exemplo 1:
var
geta : String;
getf : String;
spread: Float;
begin
if (MaxBarsForward = 0) then
begin
geta := GetAsset;
spread := BookSpread;
getf := GetFeed;
plotText((geta + "("+getf+"): "+"Spread=" +spread), clGreen, 2, 10);
end;
end;
Exemplo Gráfico 1:
Exemplo 2:
WDO = Asset("WDOFUT", feedBMF);
var
geta : String;
getf : String;
spread : Float;
begin
if (MaxBarsForward = 0) then
begin
geta := GetAsset(WDO);
spread := BookSpread;
getf := GetFeed(WDO);
plotText((geta + "(" + getf + "): " + "Spread=" + spread),clGreen,2,10);
end;
end;
Exemplo Gráfico 2:
```

_A função IsBMF() retorna se o ativo pertence ao segmento BMF._

**Sintaxe**

```ntsl
Função IsBMF(): Boolean;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso o ativo pertença ao BMF, será plotado o preço da melhor oferta de venda.

```ntsl
begin
if (isBMF) then
Plot(AskPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função Lote() retorna a quantidade mínima de contratos referente ao lote do ativo.
Ao utilizar o modo de CrossOrder na automação, o Lote irá retornar a quantidade do Lote da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função Lote(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável qtd a quantidade do lote.

```ntsl
var
qtd : Float;
begin
if not HasPosition then
BuyAtMarket;
qtd := Lote;
Plot(qtd);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função MinPriceIncrement() retorna o incremento mínimo do preço do ativo._

**Sintaxe**

```ntsl
Função MinPriceIncrement(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin o valor do incremento mínimo.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinPriceIncrement;
Plot(incMin);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função MinOrderIncrement() retorna o incremento mínimo do preço da ordem._

**Sintaxe**

```ntsl
Função MinOrderIncrement(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin o valor do incremento mínimo de ordem.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinOrderIncrement;
Plot(incMin);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função MinOrderQty() retorna a quantidade mínima de ordem._

**Sintaxe**

```ntsl
Função MinOrderQty(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin a quantidade mínima de ordem.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinOrderQty;
Plot(incMin);
end;
```

**Gráfico:** ver exemplo no manual, p. 458

_A função SellOfferCount() retorna as Ofertas de Venda do Ativo._

**Sintaxe**

```ntsl
Função SellOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável sellCount as ofertas de venda do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável sellCount as ofertas de venda do ativo
VALE3.
const
21.15 Função TotalBuyQtd

```ntsl
Exemplo 1:
var
sellCount : Integer;
begin
if not HasPosition then
sellCount := SellOfferCount;
Plot(sellCount);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
sellCount : Integer;
begin
if not HasPosition then
sellCount := SellOfferCount(VALE3);
Plot(sellCount);
end;
Exemplo Gráfico 2:
```

_A função TotalBuyQtd() retorna a quantidade de Compras do Ativo._

**Sintaxe**

```ntsl
Função TotalBuyQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0. Caso o parâmetro não seja configurado, será retornada a quantidade total de ofertas de Compra.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável buyQtd a quantidade de compras do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável buyQtd a quantidade de compras do ativo VALE3.
const
21.16 Função TotalSellQtd

```ntsl
Exemplo 1:
var
buyQtd : Integer;
begin
if not HasPosition then
buyQtd := TotalBuyQtd;
Plot(buyQtd);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
buyQtd : Integer;
begin
if not HasPosition then
buyQtd := TotalBuyQtd(VALE3);
Plot(buyQtd);
end;
Exemplo Gráfico 2:
```

_A função TotalSellQtd() retorna a quantidade de vendas do Ativo._

**Sintaxe**

```ntsl
Função TotalSellQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0. Caso o parâmetro não seja configurado, será retornada a quantidade total de ofertas de Venda.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável sellQtd a quantidade de vendas do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável sellQtd a quantidade de vendas do ativo
VALE3.
const

```ntsl
Exemplo 1:
var
sellQtd : Integer;
begin
if not HasPosition then
sellQtd := TotalSellQtd;
Plot(sellQtd);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
sellQtd : Integer;
begin
if not HasPosition then
sellQtd := TotalSellQtd(VALE3);
Plot(sellQtd);
end;
Exemplo Gráfico 2:
```

### Função AskPrice
*Manual NTSL v4.7 (14/10/2026) — p. 458*

21 Funções de Livro

21.1 Função AskPrice

_A função AskPrice() retorna o preço da melhor oferta de venda._

**Sintaxe**

```ntsl
Função AskPrice(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** venda) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável ask o valor do topo (melhor oferta de
var
ask : Float;
begin
if not HasPosition then
ask := AskPrice;
Plot(ask);
end;
```

### Função AskSize
*Manual NTSL v4.7 (14/10/2026) — p. 459*

_A função AskSize() retorna a quantidade da melhor oferta de venda.
Ao utilizar o modo de CrossOrder na automação, o AskSize irá retornar a quantidade do AskSize da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função AskSize(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** oferta de venda) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável qtdask a quantidade do topo (melhor
var
qtdask : Float;
begin
if not HasPosition then
qtdask := AskSize;
Plot(qtdask);
end;
```

### Função BidPrice
*Manual NTSL v4.7 (14/10/2026) — p. 460*

_A função BidPrice() retorna o preço da melhor oferta de compra._

**Sintaxe**

```ntsl
Função BidPrice(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** compra) do livro.

```ntsl
No exemplo, caso não tenha posição aberta, será atribuído à variável bid o valor de topo (melhor oferta de
var
bid : Float;
begin
if not HasPosition then
bid := BidPrice;
Plot(bid);
end;
```

### Função BidSize
*Manual NTSL v4.7 (14/10/2026) — p. 461*

_A função BidSize() retorna a quantidade da melhor oferta de compra.
Ao utilizar o modo de CrossOrder na automação, o BidSize irá retornar a quantidade do BidSize da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função BidSize(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** oferta de compra) do livro.

```ntsl
No exemplo, caso não tenha posição aberta será atribuído à variável qtdbid. A quantidade do topo (melhor
var
qtdbid : Float;
begin
if not HasPosition then
qtdbid := BidSize;
Plot(qtdbid);
end;
```

### Função BookSpread
*Manual NTSL v4.7 (14/10/2026) — p. 462*

_A função BookSpread() retorna a diferença entre os melhores preços de compra e venda, no topo do livro._

**Sintaxe**

```ntsl
Função BookSpread(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não tenha posição aberta, será atribuído à variável spread a diferença entre os valores das melhores ofertas de compra e venda.

```ntsl
var
spread : Float;
begin
if not HasPosition then
spread := BookSpread;
Plot(spread);
end;
```

### Função BuyOfferCount
*Manual NTSL v4.7 (14/10/2026) — p. 463*

_A função BuyOfferCount() retorna as ofertas de compra do ativo_

**Sintaxe**

```ntsl
Função BuyOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " " (ativo do gráfico).

Níveis considerados: Integer [Opcional]; Define quantos níveis de preço serão considerados no cálculo.
Valor padrão é 0.

Importante: Caso deseje informar somente o parâmetro Níveis considerados, é obrigatório também informar explicitamente o parâmetro Asset.

**Exemplo de uso:** No exemplo 1, é plotado o total de ofertas de compra do ativo do gráfico.
No exemplo 2, sem posição aberta, é atribuído à variável buyCount o número de ofertas de compra do ativo
VALE3, considerando 3 níveis de preço.
const

```ntsl
Exemplo 1:
begin
Plot(BuyOfferCount);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
buyCount : Integer;
begin
if not HasPosition then
buyCount := BuyOfferCount(VALE3,3);
Plot(buyCount);
end;
Exemplo Gráfico 2:
```

### Função GetAsset
*Manual NTSL v4.7 (14/10/2026) — p. 466*

_A função GetAsset() retorna o ticker do ativo, onde a chamada pode ser efetuada realizando a passagem do parâmetro opcional, para retornar o ticker de determinado Asset, ou declarar a função sem parametrização, onde será retornado o ticker do gráfico selecionado.
Para retornar o ticker (String) do Asset declarado, basta acessar de forma análoga às séries de dados: A1.GetAsset._

**Sintaxe**

```ntsl
Função GetAsset(Asset: Ativo): String;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

**Exemplo de uso:** No exemplo 1, para o último candle, será visualizado o nome do ativo selecionado no gráfico, com os preços de bid e ask.
ativo selecionado no gráfico.
const

```ntsl
No exemplo 2, a distinção está na especificação do Asset que será exibido (WDOFUT), independentemente do
Exemplo 1:
var
bid : Float;
ask : Float;
get : String;
begin
if (MaxBarsForward = 0) then
begin
get := GetAsset;
bid := BidPrice;
ask := AskPrice;
plotText((get + ": " + "Bid =" + bid + " Ask=" + ask),clGreen,2,8);
end;
end;
Exemplo Gráfico 1:
Exemplo 2:
WDO = Asset("WDOFUT", feedBMF);
var
bid : Float;
ask : Float;
get : String;
begin
if (MaxBarsForward = 0) then
begin
get := GetAsset(WDO);
bid := BidPrice;
ask := AskPrice;
plotText((get + ":" + " Bid =" + bid + " Ask=" + ask),clGreen,2,8);;
end
end;
Exemplo Gráfico 2:
```

### Função GetFeed
*Manual NTSL v4.7 (14/10/2026) — p. 469*

_A função GetFeed() retorna o código textual do Feed do ativo.
A parametrização é opcional, caso não seja determinado o Asset, será retornado o ticker do gráfico selecionado.
Para retornar a bolsa relacionada (String) do Asset específico, pode-se acessar de forma análoga às séries de dados:
A1.GetFeed._

**Sintaxe**

```ntsl
Função GetFeed(Asset: Ativo): String;
```

**Parâmetros**

Asset: Ativo [Opcional]; Constante declarada a partir do recurso Asset.

**Exemplo de uso:** No exemplo 1, para o último candle, será visualizado o nome do ativo selecionado no gráfico, a bolsa a qual pertence, e o spread do book.
selecionado.
const

```ntsl
No exemplo 2, será identificada a bolsa (F) vinculada ao Asset definido (WDO), independentemente do ativo
Exemplo 1:
var
geta : String;
getf : String;
spread: Float;
begin
if (MaxBarsForward = 0) then
begin
geta := GetAsset;
spread := BookSpread;
getf := GetFeed;
plotText((geta + "("+getf+"): "+"Spread=" +spread), clGreen, 2, 10);
end;
end;
Exemplo Gráfico 1:
Exemplo 2:
WDO = Asset("WDOFUT", feedBMF);
var
geta : String;
getf : String;
spread : Float;
begin
if (MaxBarsForward = 0) then
begin
geta := GetAsset(WDO);
spread := BookSpread;
getf := GetFeed(WDO);
plotText((geta + "(" + getf + "): " + "Spread=" + spread),clGreen,2,10);
end;
end;
Exemplo Gráfico 2:
```

### Função IsBMF
*Manual NTSL v4.7 (14/10/2026) — p. 472*

_A função IsBMF() retorna se o ativo pertence ao segmento BMF._

**Sintaxe**

```ntsl
Função IsBMF(): Boolean;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso o ativo pertença ao BMF, será plotado o preço da melhor oferta de venda.

```ntsl
begin
if (isBMF) then
Plot(AskPrice);
end;
```

### Função Lote
*Manual NTSL v4.7 (14/10/2026) — p. 473*

_A função Lote() retorna a quantidade mínima de contratos referente ao lote do ativo.
Ao utilizar o modo de CrossOrder na automação, o Lote irá retornar a quantidade do Lote da seríe histórica, e não no ativo de negociação._

**Sintaxe**

```ntsl
Função Lote(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável qtd a quantidade do lote.

```ntsl
var
qtd : Float;
begin
if not HasPosition then
BuyAtMarket;
qtd := Lote;
Plot(qtd);
end;
```

### Função MinPriceIncrement
*Manual NTSL v4.7 (14/10/2026) — p. 474*

_A função MinPriceIncrement() retorna o incremento mínimo do preço do ativo._

**Sintaxe**

```ntsl
Função MinPriceIncrement(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin o valor do incremento mínimo.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinPriceIncrement;
Plot(incMin);
end;
```

### Função MinOrderIncrement
*Manual NTSL v4.7 (14/10/2026) — p. 475*

_A função MinOrderIncrement() retorna o incremento mínimo do preço da ordem._

**Sintaxe**

```ntsl
Função MinOrderIncrement(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin o valor do incremento mínimo de ordem.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinOrderIncrement;
Plot(incMin);
end;
```

### Função MinOrderQty
*Manual NTSL v4.7 (14/10/2026) — p. 476*

_A função MinOrderQty() retorna a quantidade mínima de ordem._

**Sintaxe**

```ntsl
Função MinOrderQty(Asset: Ativo): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso não haja posição, ocorrerá simulada uma ordem de compra, então será atribuído à variável incMin a quantidade mínima de ordem.

```ntsl
var
incMin : Float;
begin
if not HasPosition then
BuyAtMarket;
incMin := MinOrderQty;
Plot(incMin);
end;
```

### Função SellOfferCount
*Manual NTSL v4.7 (14/10/2026) — p. 477*

_A função SellOfferCount() retorna as Ofertas de Venda do Ativo._

**Sintaxe**

```ntsl
Função SellOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável sellCount as ofertas de venda do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável sellCount as ofertas de venda do ativo
VALE3.
const

```ntsl
Exemplo 1:
var
sellCount : Integer;
begin
if not HasPosition then
sellCount := SellOfferCount;
Plot(sellCount);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
sellCount : Integer;
begin
if not HasPosition then
sellCount := SellOfferCount(VALE3);
Plot(sellCount);
end;
Exemplo Gráfico 2:
```

### Função TotalBuyQtd
*Manual NTSL v4.7 (14/10/2026) — p. 480*

_A função TotalBuyQtd() retorna a quantidade de Compras do Ativo._

**Sintaxe**

```ntsl
Função TotalBuyQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0. Caso o parâmetro não seja configurado, será retornada a quantidade total de ofertas de Compra.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável buyQtd a quantidade de compras do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável buyQtd a quantidade de compras do ativo VALE3.
const

```ntsl
Exemplo 1:
var
buyQtd : Integer;
begin
if not HasPosition then
buyQtd := TotalBuyQtd;
Plot(buyQtd);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
buyQtd : Integer;
begin
if not HasPosition then
buyQtd := TotalBuyQtd(VALE3);
Plot(buyQtd);
end;
Exemplo Gráfico 2:
```

### Função TotalSellQtd
*Manual NTSL v4.7 (14/10/2026) — p. 483*

_A função TotalSellQtd() retorna a quantidade de vendas do Ativo._

**Sintaxe**

```ntsl
Função TotalSellQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
```

**Parâmetros**

Asset: Ativo [Opcional]; Parâmetro Opcional declarado a partir do recurso Asset, valor padrão é " ".

Nível considerado: Integer [Opcional]; Parâmetro Opcional Inteiro, valor padrão é 0. Caso o parâmetro não seja configurado, será retornada a quantidade total de ofertas de Venda.

**Exemplo de uso:** No exemplo 1, caso não tenha posição aberta, será atribuído à variável sellQtd a quantidade de vendas do ativo.
No exemplo 2, caso não tenha posição aberta, será atribuído à variável sellQtd a quantidade de vendas do ativo
VALE3.
const

```ntsl
Exemplo 1:
var
sellQtd : Integer;
begin
if not HasPosition then
sellQtd := TotalSellQtd;
Plot(sellQtd);
end;
Exemplo Gráfico 1:
Exemplo 2:
VALE3 = Asset("VALE3", feedBovespa);
var
sellQtd : Integer;
begin
if not HasPosition then
sellQtd := TotalSellQtd(VALE3);
Plot(sellQtd);
end;
Exemplo Gráfico 2:
```

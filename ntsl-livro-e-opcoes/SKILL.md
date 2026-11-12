---
name: ntsl-livro-e-opcoes
description: Funções de livro de ofertas (BidPrice, AskPrice, BidSize, AskSize, BookSpread, BuyOfferCount, TotalBuyQtd/TotalSellQtd, Lote, MinPriceIncrement, GetAsset, IsBMF) e funções gregas/opções (Delta, Gamma, Theta, Vega, Rho, Strike). Use quando a estratégia precisar do livro, do ticker, do lote, da BMF, da volatilidade implícita ou de precificar opção.
---

# Livro de ofertas e opções no NTSL

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulos 21 (Livro, p. 458) e 23 (Opções, p. 530).

## Regras que não se negociam

1. **Livro só faz sentido em backtest se o dado existir.** Em backtest OHLC o livro não é reconstruído — `BidPrice`/`AskPrice` devolvem o dado disponível, não o spread real do passado. Estratégia que depende de livro exige backtest tick a tick.
2. **`GetAsset()` devolve o ticker como texto** — é o caminho para checar ativo por nome, não para comparar com string fixa "WINFUT" sem normalizar.
3. **Lote e incremento vêm do contrato**: `Lote()`, `MinOrderQty()`, `MinOrderIncrement()`, `MinPriceIncrement()`. Quantidade "redonda" fora do lote é rejeitada.
4. **`IsBMF()`** separa B3-BMF (contratos) de ações — não infira pelo sufixo do ticker.
5. **Grega é cálculo teórico com parâmetros seus**: `Delta(DaysLeft, StrikePr, AssetPr, Rate100, Volty100, PutCall)`. O manual define `Rate100` como taxa de juros em % e `Volty100` como volatilidade em % — o exemplo oficial usa 0.1 e 0.25, ou seja, esses números são percentuais, não fração de 25%. `DaysLeft` é em **dias úteis** até o vencimento.
6. **`optCall`/`optPut` são constantes da linguagem** — não invente valor numérico.

## Assinaturas conferidas

```ntsl
Função BidPrice(Asset: Ativo): Float;
Função AskPrice(Asset: Ativo): Float;
Função BidSize(Asset: Ativo): Float;
Função AskSize(Asset: Ativo): Float;
Função BookSpread(Asset: Ativo): Float;
Função BuyOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
Função SellOfferCount(Asset: Ativo; Níveis considerados: Integer): Integer;
Função TotalBuyQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
Função TotalSellQtd(Asset: Ativo; Níveis considerados: Integer): Integer;
Função Lote(Asset: Ativo): Float;
Função MinPriceIncrement(Asset: Ativo): Float;
Função MinOrderIncrement(Asset: Ativo): Float;
Função MinOrderQty(Asset: Ativo): Float;
Função GetAsset(Asset: Ativo): String;
Função IsBMF(): Boolean;
Função Delta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :
Função Gamma(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :
Função Theta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :
Função Vega(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float
Função Rho(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float;
Função Strike(Asset : Ativo): Float;
```

## Funções cobertas

- Livro (16): AskPrice, AskSize, BidPrice, BidSize, BookSpread, BuyOfferCount, GetAsset, GetFeed, IsBMF, Lote, MinPriceIncrement, MinOrderIncrement, MinOrderQty, SellOfferCount, TotalBuyQtd, TotalSellQtd
- Opções (6): Delta, Gamma, Rho, Strike, Theta, Vega

## Referências

- `refs/01-livro.md`, `refs/02-opcoes.md`

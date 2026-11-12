---
name: ntsl-backtesting-e-ordens
description: Funções de backtesting e de ordem do NTSL — envio e cancelamento de ordens a mercado, limitada e stop, covers, reversão, posição, preço médio e resultado do backtest, mais as regras de execução que fazem uma ordem desaparecer. Use ao escrever a lógica de entrada/saída de uma estratégia, ao depurar por que uma ordem não foi enviada, ou ao ler resultados do backtest.
---

# Ordens, posição e resultado no NTSL

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulo 15 (p. 69 em diante) e capítulo 14 (alarmes, p. 68) e anexo 28 (p. 574). Conteúdo verbatim em `refs/`.

## Regras de execução que derrubam estratégia (manual, p. 574)

1. **`CancelPendingOrders` cancela o que veio antes no mesmo fluxo.** `BuyAtMarket; CancelPendingOrders;` → **nenhuma ordem é criada**.
2. **`ClosePosition` cancela a ordem de entrada do mesmo fluxo.** `BuyAtMarket; ClosePosition;` → nenhuma ordem criada.
3. **`ReversePosition` cancela a ordem contrária do mesmo fluxo.** `SellShortAtMarket; ReversePosition;` → nenhuma ordem criada.
4. **Ordens a mercado no mesmo fluxo são agrupadas.** `BuyAtMarket; SellShortAtMarket;` → nenhuma ordem criada.
5. **Não existe posição dentro do mesmo fluxo de execução.** `BuyAtMarket` seguido de `SellToCoverLimit(...)` no mesmo `if` **não** cria cover: naquele instante `HasPosition` ainda é falso. Separe com `if not HasPosition then ... else ...`.
6. **Comparação de `Float` com `=` falha** (representação de ponto flutuante): use `CompareFloat(a, b, casas) = 0`.

Essas seis são as causas mais comuns de "a estratégia não opera" e estão todas documentadas no Anexo 28 do manual. Antes de reescrever a lógica, confira se o código não cai num desses casos.

## Assinaturas conferidas

```ntsl
Função BuyAtMarket(Quantity: Float): Void;
Função BuyLimit(Limit: Float; Quantity: Float; bCanReversePosition: Boolean): Void;
Função BuyStop(Stop : Float; Limit: Float; Quantity: Float; bCanReversePosition:
Função SellShortAtMarket(Quantity: Float): Void;
Função ClosePosition(): Void;
Função CancelPendingOrders(): Void;
Função ReversePosition(): Void;
Função HasPosition(): Boolean;
Função Position(): Integer;
Função BuyPrice(): Float;
Função BuyPosition(): Integer;
Função HasPendingOrders(): Boolean;
Função AvgTradeResult(OpenResult: Boolean): Float;
Função DailyResult(OpenResult: Boolean): Float;
Função AutomationResult(OpenResult: Boolean): Float;
```

As **38 funções** do capítulo de backtesting: AutomationResult, AvgTradeResult, AvgTradeResultDaily, BuyAtMarket, BuyLimit, BuyPosition, BuyPositionQty, BuyPrice, BuyStop, BuyToCoverAtMarket, BuyToCoverLimit, BuyToCoverStop, CancelPendingOrders, ClosePosition, DailyResult, HasPendingOrders, HasPosition, IsBought, IsSold, LastTradeResult, MyPrice, Position, PositionQty, Price, ReversePosition, SellPosition, SellPositionQty, SellPrice, SellShortAtMarket, SellShortLimit, SellShortStop, SellToCoverAtMarket, SellToCoverLimit, SellToCoverStop, SendOrder, OpenResult, XRay, NumberOfPendingOrders.

## Como separar as três perguntas

- **"Quero abrir/zerar posição"** → funções de ordem (`BuyAtMarket`, `BuyLimit`, `BuyStop`, `SellShort*`, `SellToCover*`, `BuyToCover*`, `ClosePosition`, `ReversePosition`).
- **"Quero saber onde estou"** → leitura de estado: `HasPosition`, `Position`, `BuyPosition`, `BuyPositionQty`, `BuyPrice`, `HasPendingOrders`.
- **"Quero avaliar o resultado"** → `AvgTradeResult`, `AvgTradeResultDaily`, `DailyResult`, `AutomationResult`.

O manual de cada função diz se ela vale no backtest, na automação ou nos dois — informe isso ao responder, porque função de resultado não tem o mesmo comportamento nos dois modos.

## Referências

- `refs/01-conceitos-de-backtest.md` — backtest OHLC, tick a tick, gráficos atemporais
- `refs/02-ordens-posicao-e-resultados.md` — as 38 funções, com sintaxe, parâmetros e exemplos

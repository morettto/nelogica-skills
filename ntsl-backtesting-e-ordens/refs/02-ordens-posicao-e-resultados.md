# 02 Ordens Posicao E Resultados

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Alarme

### Funções de Alarme
*Manual NTSL v4.7 (14/10/2026) — p. 68*

Funções de Alarme

14.1 Função Alert

_A função Alert() tem como finalidade gerar um alarme ao usuário._

**Sintaxe**

```ntsl
Função Alert(Color: Integer): Void;
```

**Parâmetros**

Color: Integer; Determina a cor desejada para o popup de notificação, no momento de execução do alarme.

**Exemplo de uso:** móvel aritmética de 9 períodos for menor que a média de 21.

```ntsl
No exemplo abaixo, a função Alert() irá emitir um alarme (e um popup com coloração vermelha) caso a média
begin
if (Media(9,Close) < Media(21,Close)) then
Alert(clRed);
end;
```

### Função Alert
*Manual NTSL v4.7 (14/10/2026) — p. 68*

14 Funções de Alarme

14.1 Função Alert

_A função Alert() tem como finalidade gerar um alarme ao usuário._

**Sintaxe**

```ntsl
Função Alert(Color: Integer): Void;
```

**Parâmetros**

Color: Integer; Determina a cor desejada para o popup de notificação, no momento de execução do alarme.

**Exemplo de uso:** móvel aritmética de 9 períodos for menor que a média de 21.

```ntsl
No exemplo abaixo, a função Alert() irá emitir um alarme (e um popup com coloração vermelha) caso a média
begin
if (Media(9,Close) < Media(21,Close)) then
Alert(clRed);
end;
```

## Funções de Backtesting

### Funções de Backtesting
*Manual NTSL v4.7 (14/10/2026) — p. 69*

Funções de Backtesting

15.1 Função AutomationResult

_A partir da função AutomationResult() pode-se verificar o resultado acumulado das operações da au- tomação, retornado em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AutomationResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo do resultado acumulado da automação:

– Verdadeiro: Retorna o resultado acumulado das operações fechadas somado ao resultado da oper-

ação em aberto, considerando-o como parte do total;

– Falso: Retorna apenas o resultado acumulado das operações já encerradas pela automação (valor

padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta e, em seguida, verifica o resultado acumulado incluindo o resultado da operação em aberto. Caso o prejuízo ultrapasse o limite definido, a posição é encerrada.

```ntsl
var
nAutomationResult : Float;
begin
if not HasPosition then
BuyAtMarket;
nAutomationResult := AutomationResult(True);
if (nAutomationResult <= -500) then
ClosePosition;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função AvgTradeResult() pode-se verificar a média do resultado das operações da automação, retornada em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AvgTradeResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo da média dos resultados da automação:

– Verdadeiro: Calcula a média considerando as operações fechadas mais o resultado da operação em

aberto, tratando-a como mais uma operação;

– Falso: Calcula a média considerando apenas as operações já encerradas pela automação (valor padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta, encerra posições periodicamente e, em seguida, avalia a média dos resultados das operações fechadas para tomada de decisão lógica.

```ntsl
var
nAvgResult : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,5) = 0 then
ClosePosition;
nAvgResult := AvgTradeResult(False);
if (nAvgResult > 0) then
PlotText("Média positiva", clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função AvgTradeResultDaily() pode-se verificar a média do resultado das operações realizadas no dia pela automação, retornada em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AvgTradeResultDaily(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo da média diária dos resultados da automação:

– Verdadeiro: Calcula a média considerando as operações fechadas no dia mais o resultado da operação

em aberto, tratando-a como mais uma operação;

– Falso: Calcula a média considerando apenas as operações já encerradas no dia pela automação (valor

padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta, encerra posições periodicamente e, em seguida, avalia a média diária dos resultados das operações fechadas para tomada de decisão lógica.

```ntsl
var
nAvgResultDaily : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,5) = 0 then
ClosePosition;
nAvgResultDaily := AvgTradeResultDaily(False);
if (nAvgResultDaily > 0) then
PlotText("Média positiva", clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyAtMarket() tem como funcionalidade realizar uma ordem de compra a mercado.
Se o parâmetro de quantidade não for especificado, a ordem usará o valor definido no campo "Quantidade" da aba de Execução do editor de estratégias, com o mínimo sendo 1 lote.
Na automação, será considerada a quantidade configurada no campo "Quantidade por Ordem". Quando o parâmetro é especificado, a estratégia ignora essas configurações e utiliza a quantidade informada no código, que deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior, será realizada uma simulação de ordem a mercado.

```ntsl
begin
if (Low = Low[1]) then
BuyAtMarket;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyLimit() possui como finalidade enviar uma ordem de compra do tipo limite. Se a quantidade não for especificada, será usada a definida na aba de Execução do editor de estratégias, com mínimo de 1 lote.
Em automações, utiliza-se a quantidade do campo "Quantidade por Ordem". Quando a quantidade é especificada no código, ela ignora as configurações padrão e deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de compra apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando vendido em 4 contratos, uma ordem de compra de 8 contratos resulta em posição comprada de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função BuyLimit(Limit: Float; Quantity: Float; bCanReversePosition: Boolean): Void;
```

**Parâmetros**

Limit: Float; Determina o preço limite para inserção de ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso não tenha nenhuma posição aberta, será enviada uma ordem de compra do tipo limite.

```ntsl
begin
if not HasPosition then
BuyLimit(close,lote);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyPosition() retorna o tamanho da posição em lote da compra._

**Sintaxe**

```ntsl
Função BuyPosition(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso a mínima do candle atual for igual a do candle anterior, então a variável buyPos irá receber o total da posição de compra.

```ntsl
var
buyPos : Integer;
begin
buyPos := BuyPosition;
if (Low = Low[1]) then
BuyAtMarket;
Plot(buyPos);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyPositionQty() retorna o tamanho da posição em quantidade da compra._

**Sintaxe**

```ntsl
Função BuyPositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso o fechamento do candle atual for maior que o do candle anterior, então a variável buyPos irá receber o tamanho da posição em quantidade de compra.

```ntsl
var
buyPos : Float;
begin
buyPos := BuyPositionQty;
if (Close > Close[1]) then
BuyAtMarket;
Plot(BuyPositionQty);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyPrice() retorna o preço de compra da posição._

**Sintaxe**

```ntsl
Função BuyPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso a mínima do candle atual for igual a do candle anterior, então será atribuído à variável pCompra o valor de compra da posição.

```ntsl
var
pCompra : Float;
begin
pCompra := BuyPrice;
if (Low = Low[1]) then
BuyAtMarket();
Plot(BuyPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função BuyStop() permite criar uma ordem do tipo Stop, onde o preço stop define o gatilho e o limite determina até que preço a ordem pode ser executada. Se a quantidade não for especificada, será usada a do campo
Quantidade na aba de Execução (mínimo de 1 lote).
Em automações, é usada a quantidade do campo "Quantidade por Ordem". Quando a quantidade é informada no código, ela ignora as configurações padrão e deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de compra apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando vendido em 4 contratos, uma ordem de compra de 8 contratos resulta em posição comprada de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função BuyStop(Stop : Float; Limit: Float; Quantity: Float; bCanReversePosition:

Boolean): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem.

Limit: Float [Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso a mínima do candle atual seja diferente a do candle anterior, será inserida uma ordem de compra tipo stop, no nível especificado na variável pStop.
input

```ntsl
pStop(133000);
lote(1);
begin
if (Low <> Low[1]) then
BuyStop(pStop,pStop,lote);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyToCoverAtMarket() envia uma ordem de compra caso exista uma posição vendida em aberto. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se a quantidade for especificada no código, ela prevalece sobre as configurações e deve ser múltipla do lote do ativo.
O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo abaixo, caso a mínima atual seja maior que a mínima anterior e exista uma posição de venda, será

```ntsl
executada uma ordem a mercado, utilizando a função BuyToCoverAtMarket() para fechar a operação.
begin
SellShortAtMarket;
if ((Low > Low[1]) and (IsSold)) then
BuyToCoverAtMarket;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyToCoverLimit() envia uma ordem de compra limite para finalizar a operação. Se a quantidade não for especificada, será usada a configurada na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverLimit(Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Limit: Float; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso exista uma posição de venda, será inserida a ordem no preço de fechamento para zerar a posição.

```ntsl
begin
SellShortAtMarket;
if (IsSold) then
BuyToCoverLimit(Close,lote);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função BuyToCoverStop() envia uma ordem de compra do tipo Stop se houver uma posição de venda no ativo.
Se a quantidade não for especificada, será usada a configurada na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverStop(Stop : Float; Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem.

Limit: Float [Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop.
input

```ntsl
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop, pStop);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função CancelPendingOrders() possui como recurso efetuar o cancelamento de todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas._

**Sintaxe**

```ntsl
Função CancelPendingOrders(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop, caso existam ordens pendentes, ocorrerá o cancelamento e não será plotado nada no gráfico.
input

```ntsl
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop, pstop);
if (HasPendingOrders) then
CancelPendingOrders;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função ClosePosition() envia ordens para encerrar a posição. Esta função cancela todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas. Após confirmação do cancelamento das ordens, será enviada uma ordem para fechar a posição._

**Sintaxe**

```ntsl
Função ClosePosition(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, caso a mínima do candle atual seja igual a do candle anterior será realizada a simulação de uma ordem de compra e então a posição será finalizada.

```ntsl
begin
if (Low = Low[1]) then
BuyAtMarket;
if HasPosition then
ClosePosition;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função DailyResult() pode-se verificar o resultado diário das operações, retornado em valor financeiro
(resultado monetário). O parâmetro OpenResult é opcional, e seu valor padrão é verdadeiro._

**Sintaxe**

```ntsl
Função DailyResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Se deve retornar o resultado aberto:

– Verdadeiro: Retorna o resultado fechado + aberto;
– Falso: Retorna apenas o resultado fechado;

**Exemplo de uso:** No exemplo, será retornado o resultado fechado + aberto das operações do dia.

```ntsl
var
dResult : Float;
begin
if not HasPosition then
BuyAtMarket;
dResult := DailyResult(True);
Plot(dResult);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função HasPendingOrders() retorna se há ordens pendentes._

**Sintaxe**

```ntsl
Função HasPendingOrders(): Boolean;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop, e caso existam ordens input

```ntsl
pendentes, será plotado a MedianPrice() no gráfico.
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop,pstop);
if (HasPendingOrders) then
Plot(MedianPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função HasPosition() retorna verdadeiro se a posição não é zero._

**Sintaxe**

```ntsl
Função HasPosition(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, ocorrerá a simulação de uma ordem a mercado usando a função HasPosition() para validar se
há posição ou não e, caso exista posição, ocorrerá o plot de BuyPrice() no gráfico.
begin
BuyAtMarket;
if HasPosition then
Plot(BuyPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função IsBought() tem como funcionalidade determinar se há uma posição de compra em aberto._

**Sintaxe**

```ntsl
Função IsBought(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, caso exista uma posição de compra, haverá a aplicação de uma coloração (verde).
begin
BuyAtMarket;
if (IsBought) then
PaintBar(clGreen);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função IsSold() tem como funcionalidade determinar se há uma posição de venda em aberto._

**Sintaxe**

```ntsl
Função IsSold(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, caso exista uma posição de venda, haverá a aplicação de uma coloração (vermelho).
begin
SellShortAtMarket;
if (IsSold) then
PaintBar(clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função LastTradeResult() pode-se verificar o resultado da última operação encerrada pela au- tomação, retornado em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente con- figurado._

**Sintaxe**

```ntsl
Função LastTradeResult(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta e utiliza o resultado da última operação encerrada como critério de validação lógica.

```ntsl
var
nLastResult : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,3) = 0 then
ClosePosition;
nLastResult := LastTradeResult;
if (nLastResult < 0) then
PlotText("Última operação negativa", clRed);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função MyPrice() retorna a média entre a máxima, mínima e fechamento._

**Sintaxe**

```ntsl
Função MyPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** a mercado e então o plot da função no gráfico.

```ntsl
No exemplo, será atribuído à variável mPrice, o valor da função MyPrice(), será simulada uma ordem de compra
var
mPrice : Float;
begin
mPrice := MyPrice;
BuyAtMarket;
if (IsBought) then
Plot(mPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função Position() retorna o tamanho da posição em lote, positivo para compra e negativo para venda._

**Sintaxe**

```ntsl
Função Position(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável vPosition, a posição, e será simulada uma ordem de compra a mercado e então o plot da função no gráfico.

```ntsl
var
vPosition : Integer;
begin
vPosition := Position;
BuyAtMarket;
if (IsBought) then
Plot(vPosition);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função PositionQty() retorna o tamanho da posição em quantidade, positivo para compra e negativo para venda._

**Sintaxe**

```ntsl
Função PositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável vPosition, a posição, e será simulada uma ordem de compra a mercado e então o plot da função no gráfico.

```ntsl
var
vPosition : Float;
begin
vPosition := PositionQty;
BuyAtMarket;
if (IsBought) then
Plot(vPosition);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função Price() retorna o preço de compra ou venda da posição, dependendo se estiver comprado ou vendido._

**Sintaxe**

```ntsl
Função Price(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** a mercado e então o plot da função no gráfico.

```ntsl
No exemplo, será atribuído à variável vPrice, o valor da função Price(), será simulada uma ordem de compra
var
vPrice : Float;
begin
vPrice := Price;
BuyAtMarket;
if (IsBought) then
Plot(vPrice);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função ReversePosition() tem como funcionalidade realizar o envio de ordens, a fim de inversão da posição.
Esta função cancela todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas. Após confirmação do cancelamento das ordens, será enviada uma ordem para reverter a posição._

**Sintaxe**

```ntsl
Função ReversePosition(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for menor a do candle anterior, e exista uma posição de compra, será realizada a reversão.

```ntsl
begin
BuyAtMarket;
if (Low < Low[1]) and (IsBought = True) then
ReversePosition;
end
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellPosition() retorna o tamanho da posição em lote de venda._

**Sintaxe**

```ntsl
Função SellPosition(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável sellPos, irá receber a posição de venda.

```ntsl
var
sellPos : Integer;
begin
SellShortAtMarket;
sellPos := SellPosition;
Plot(sellPos);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellPositionQty() retorna o tamanho da posição em quantidade de venda._

**Sintaxe**

```ntsl
Função SellPositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável sellPos, irá receber o total da posição de venda.

```ntsl
var
sellPos : Float;
begin
SellShortAtMarket;
sellPos := SellPositionQty;
Plot(sellPos);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellPrice() retorna o preço de venda da posição._

**Sintaxe**

```ntsl
Função SellPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável pVenda, o valor de venda da posição, ocorrerá uma simulação de venda e o plot da função no gráfico.

```ntsl
var
pVenda : Float;
begin
SellShortAtMarket;
pVenda := SellPrice;
Plot(pVenda);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellShortAtMarket() envia uma ordem de venda a mercado. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo
"Quantidade por Ordem".
Se especificada no código, essa quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellShortAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo abaixo, será executada uma ordem de venda a mercado, caso a mínima do candle atual seja igual a do candle anterior.

```ntsl
begin
if (Low = Low[1]) then
SellShortAtMarket;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_Descrição:

A função SellShortLimit() envia uma ordem de venda limite. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de venda apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando comprado em 4 contratos, uma ordem de venda de 8 contratos resulta em posição vendida de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função SellShortLimit(Limit: Float; Quantity: Float; bCanReversePosition: Boolean):

Void;
```

**Parâmetros**

Limit: Float; Preço para a inserção da ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo abaixo, será executada uma ordem de venda a mercado, caso a mínima do candle atual seja igual a do candle anterior.
em 4 contratos, a ordem de venda de 8 contratos é enviada integralmente, resultando em posição vendida de 4 contratos. Sem esse parâmetro, seriam enviados apenas 4 contratos, encerrando a posição sem invertê-la.

```ntsl
begin
if (Low = Low[1]) then
SellShortLimit(Close, lote);
end;
No exemplo a seguir, o parâmetro bCanReversePosition é utilizado para inverter a posição: estando comprado
begin
if not IsBought then
BuyAtMarket(4)
else
SellShortLimit(Close, 8, True);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellShortStop() envia uma ordem de venda do tipo stop. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo
"Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de venda apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando comprado em 4 contratos, uma ordem de venda de 8 contratos resulta em posição vendida de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função SellShortStop(Stop: Float; Limit: Float; Quantity: Float;

bCanReversePosition: Boolean): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

Limit: Float[Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso a máxima atual for maior do que a anterior, será inserida uma ordem de venda stop, no preço armazenado na variável pAux.
input

```ntsl
pAux(136000);
begin
if (High > High[1]) then
SellShortStop(pAux,pAux);
end
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellToCoverAtMarket() envia uma ordem de venda a mercado se houver uma posição de compra. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de venda.

**Exemplo de uso:** No exemplo abaixo, caso a máxima atual seja maior que a máxima anterior e exista uma posição de compra, será executada uma ordem a mercado, para fechar a operação.

```ntsl
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) and (IsBought) then
SellToCoverAtMarket;
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellToCoverLimit() envia uma ordem de venda limite para finalizar a operação. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverLimit(Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Limit: Float; Preço para a inserção da ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso exista uma posição de compra, será inserida a ordem no preço de fechamento para zerar a posição.

```ntsl
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) and (IsBought) then
SellToCoverLimit(Close);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função SellToCoverStop() envia uma ordem stop de venda caso exista uma posição de compra. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverStop(Stop: Float; Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

Limit: Float [Opcional]; Valor que será o limite do preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem.

**Exemplo de uso:** No exemplo, caso a máxima do candle atual for maior que a do candle anterior e exista uma posição de compra, será inserida uma ordem de venda do tipo stop, no preço de pAux.
input

```ntsl
pAux(136000);
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) then
SellToCoverStop(pAux,pAux,lote);
end
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função SendOrder() pode-se enviar ordens customizadas, determinando o lado, tipo e quantidade._

**Sintaxe**

```ntsl
Função SendOrder(Side: Integer; Type: Integer; Quantity: Float; Limit: Float; Stop:

Float): Void;
```

**Parâmetros**

Side: Integer; Determina o lado da ordem;

Type: Integer; Tipo da ordem;

Quantity: Float; Determina a quantidade a ser executada na ordem.

Limit: Float; Quantidade de contratos / lotes.

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

**Exemplo de uso:** No exemplo, será efetuada a inserção de uma ordem de compra, tipo Stop, no preço 30.45, com limite de execução até o nível 30.55.

```ntsl
begin
if not HasPosition then
SendOrder(osBuy, otStopLimit, 100, 30.55, 30.45);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A partir da função OpenResult() pode-se verificar o resultado diário das operações em aberto._

**Sintaxe**

```ntsl
Função OpenResult(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será retornado o resultado aberto das operações do dia.

```ntsl
var
oResult : Float;
begin
if not HasPosition then
BuyAtMarket;
oResult := OpenResult;
Plot(oResult);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função XRay() permite o monitoramento em tempo real de variáveis e condições dentro de uma estratégia autom- atizada, exibindo essas informações no botão Raio-X do Gerenciador de Automações._

**Sintaxe**

```ntsl
Função XRay(strValue: String; bValue: Boolean; strGroup: String; dValue: Float;

ColorON: Integer; ColorOFF: Integer): Void;
```

**Parâmetros**

strValue: String; Nome identificador da condição ou variável que será exibido no painel Raio-X;

bValue: Boolean; Valor lógico que representa o estado atual da condição (verdadeiro ou falso);

strGroup: String; Define o nome para o grupo que será exibido no raio-x durante a execução ;

dValue: Float [Opcional]; Define o valor da variável;

colorON: Integer [Opcional]; Cor quando a condição for verdadeira;

colorOFF: Integer [Opcional]; Cor quando a condição for falsa;

```ntsl
No exemplo, será exibido o valor em tempo real da automação ao utilizar a função XRay().
var
pBuy : Float;
begin
pBuy := BuyPrice;
if (Low <= Low[1]) then
BuyAtMarket();
Plot(BuyPrice);
XRay("pBuy",(pBuy > 0),"Buy",pBuy);
end;
```

**Gráfico:** ver exemplo no manual, p. 69

_A função NumberOfPendingOrders() permite obter o número atual de ordens abertas da sua Automação de Es- tratégias, sendo útil para tomadas de decisão dentro de uma estratégia automatizada._

**Sintaxe**

```ntsl
Função NumberOfPendingOrders(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Observações**

Recomenda-se utilizar a função apenas no modo de execução Ao Satisfazer Condição, pois em outros modos o valor retornado pode estar desatualizado, gerando comportamento imprevisível na estratégia;

**Exemplo de uso:** mantidas até 10 ordens limitadas de compra pendentes, posicionadas abaixo do preço médio de entrada.
input dPrecoOrdem

```ntsl
No exemplo abaixo, a estratégia utiliza a função NumberOfPendingOrders() para garantir que sempre sejam
TicksGradiente(5);
var
nIndex,nFaltando : Integer;
: Float;
begin
if not HasPosition then
BuyAtMarket(1);
nFaltando := 10 - NumberOfPendingOrders();
if nFaltando > 0 then
begin
for nIndex := 1 to nFaltando do
begin
dPrecoOrdem := BuyPrice - (nIndex * MinPriceIncrement * TicksGradiente);
BuyLimit(dPrecoOrdem);
end;
end;
end;
```

### Função AutomationResult
*Manual NTSL v4.7 (14/10/2026) — p. 69*

15 Funções de Backtesting

15.1 Função AutomationResult

_A partir da função AutomationResult() pode-se verificar o resultado acumulado das operações da au- tomação, retornado em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AutomationResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo do resultado acumulado da automação:

– Verdadeiro: Retorna o resultado acumulado das operações fechadas somado ao resultado da oper-

ação em aberto, considerando-o como parte do total;

– Falso: Retorna apenas o resultado acumulado das operações já encerradas pela automação (valor

padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta e, em seguida, verifica o resultado acumulado incluindo o resultado da operação em aberto. Caso o prejuízo ultrapasse o limite definido, a posição é encerrada.

```ntsl
var
nAutomationResult : Float;
begin
if not HasPosition then
BuyAtMarket;
nAutomationResult := AutomationResult(True);
if (nAutomationResult <= -500) then
ClosePosition;
end;
```

### Função AvgTradeResult
*Manual NTSL v4.7 (14/10/2026) — p. 71*

_A partir da função AvgTradeResult() pode-se verificar a média do resultado das operações da automação, retornada em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AvgTradeResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo da média dos resultados da automação:

– Verdadeiro: Calcula a média considerando as operações fechadas mais o resultado da operação em

aberto, tratando-a como mais uma operação;

– Falso: Calcula a média considerando apenas as operações já encerradas pela automação (valor padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta, encerra posições periodicamente e, em seguida, avalia a média dos resultados das operações fechadas para tomada de decisão lógica.

```ntsl
var
nAvgResult : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,5) = 0 then
ClosePosition;
nAvgResult := AvgTradeResult(False);
if (nAvgResult > 0) then
PlotText("Média positiva", clRed);
end;
```

### Função AvgTradeResultDaily
*Manual NTSL v4.7 (14/10/2026) — p. 73*

_A partir da função AvgTradeResultDaily() pode-se verificar a média do resultado das operações realizadas no dia pela automação, retornada em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente configurado.
O parâmetro OpenResult é opcional, e seu valor padrão é Falso._

**Sintaxe**

```ntsl
Função AvgTradeResultDaily(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Define se o resultado da operação em aberto deve ser considerado no cálculo da média diária dos resultados da automação:

– Verdadeiro: Calcula a média considerando as operações fechadas no dia mais o resultado da operação

em aberto, tratando-a como mais uma operação;

– Falso: Calcula a média considerando apenas as operações já encerradas no dia pela automação (valor

padrão);

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta, encerra posições periodicamente e, em seguida, avalia a média diária dos resultados das operações fechadas para tomada de decisão lógica.

```ntsl
var
nAvgResultDaily : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,5) = 0 then
ClosePosition;
nAvgResultDaily := AvgTradeResultDaily(False);
if (nAvgResultDaily > 0) then
PlotText("Média positiva", clRed);
end;
```

### Função BuyAtMarket
*Manual NTSL v4.7 (14/10/2026) — p. 75*

_A função BuyAtMarket() tem como funcionalidade realizar uma ordem de compra a mercado.
Se o parâmetro de quantidade não for especificado, a ordem usará o valor definido no campo "Quantidade" da aba de Execução do editor de estratégias, com o mínimo sendo 1 lote.
Na automação, será considerada a quantidade configurada no campo "Quantidade por Ordem". Quando o parâmetro é especificado, a estratégia ignora essas configurações e utiliza a quantidade informada no código, que deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior, será realizada uma simulação de ordem a mercado.

```ntsl
begin
if (Low = Low[1]) then
BuyAtMarket;
end;
```

### Função BuyLimit
*Manual NTSL v4.7 (14/10/2026) — p. 76*

_A função BuyLimit() possui como finalidade enviar uma ordem de compra do tipo limite. Se a quantidade não for especificada, será usada a definida na aba de Execução do editor de estratégias, com mínimo de 1 lote.
Em automações, utiliza-se a quantidade do campo "Quantidade por Ordem". Quando a quantidade é especificada no código, ela ignora as configurações padrão e deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de compra apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando vendido em 4 contratos, uma ordem de compra de 8 contratos resulta em posição comprada de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função BuyLimit(Limit: Float; Quantity: Float; bCanReversePosition: Boolean): Void;
```

**Parâmetros**

Limit: Float; Determina o preço limite para inserção de ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso não tenha nenhuma posição aberta, será enviada uma ordem de compra do tipo limite.

```ntsl
begin
if not HasPosition then
BuyLimit(close,lote);
end;
```

### Função BuyPosition
*Manual NTSL v4.7 (14/10/2026) — p. 78*

_A função BuyPosition() retorna o tamanho da posição em lote da compra._

**Sintaxe**

```ntsl
Função BuyPosition(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso a mínima do candle atual for igual a do candle anterior, então a variável buyPos irá receber o total da posição de compra.

```ntsl
var
buyPos : Integer;
begin
buyPos := BuyPosition;
if (Low = Low[1]) then
BuyAtMarket;
Plot(buyPos);
end;
```

### Função BuyPositionQty
*Manual NTSL v4.7 (14/10/2026) — p. 79*

_A função BuyPositionQty() retorna o tamanho da posição em quantidade da compra._

**Sintaxe**

```ntsl
Função BuyPositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso o fechamento do candle atual for maior que o do candle anterior, então a variável buyPos irá receber o tamanho da posição em quantidade de compra.

```ntsl
var
buyPos : Float;
begin
buyPos := BuyPositionQty;
if (Close > Close[1]) then
BuyAtMarket;
Plot(BuyPositionQty);
end;
```

### Função BuyPrice
*Manual NTSL v4.7 (14/10/2026) — p. 80*

_A função BuyPrice() retorna o preço de compra da posição._

**Sintaxe**

```ntsl
Função BuyPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será realizada a simulação de uma ordem de compra caso a mínima do candle atual for igual a do candle anterior, então será atribuído à variável pCompra o valor de compra da posição.

```ntsl
var
pCompra : Float;
begin
pCompra := BuyPrice;
if (Low = Low[1]) then
BuyAtMarket();
Plot(BuyPrice);
end;
```

### Função BuyStop
*Manual NTSL v4.7 (14/10/2026) — p. 81*

_A partir da função BuyStop() permite criar uma ordem do tipo Stop, onde o preço stop define o gatilho e o limite determina até que preço a ordem pode ser executada. Se a quantidade não for especificada, será usada a do campo
Quantidade na aba de Execução (mínimo de 1 lote).
Em automações, é usada a quantidade do campo "Quantidade por Ordem". Quando a quantidade é informada no código, ela ignora as configurações padrão e deve ser múltipla do lote do ativo. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de compra apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando vendido em 4 contratos, uma ordem de compra de 8 contratos resulta em posição comprada de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função BuyStop(Stop : Float; Limit: Float; Quantity: Float; bCanReversePosition:

Boolean): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem.

Limit: Float [Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso a mínima do candle atual seja diferente a do candle anterior, será inserida uma ordem de compra tipo stop, no nível especificado na variável pStop.
input

```ntsl
pStop(133000);
lote(1);
begin
if (Low <> Low[1]) then
BuyStop(pStop,pStop,lote);
end;
```

### Função BuyToCoverAtMarket
*Manual NTSL v4.7 (14/10/2026) — p. 83*

_A função BuyToCoverAtMarket() envia uma ordem de compra caso exista uma posição vendida em aberto. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se a quantidade for especificada no código, ela prevalece sobre as configurações e deve ser múltipla do lote do ativo.
O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo abaixo, caso a mínima atual seja maior que a mínima anterior e exista uma posição de venda, será

```ntsl
executada uma ordem a mercado, utilizando a função BuyToCoverAtMarket() para fechar a operação.
begin
SellShortAtMarket;
if ((Low > Low[1]) and (IsSold)) then
BuyToCoverAtMarket;
end;
```

### Função BuyToCoverLimit
*Manual NTSL v4.7 (14/10/2026) — p. 84*

_A função BuyToCoverLimit() envia uma ordem de compra limite para finalizar a operação. Se a quantidade não for especificada, será usada a configurada na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverLimit(Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Limit: Float; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso exista uma posição de venda, será inserida a ordem no preço de fechamento para zerar a posição.

```ntsl
begin
SellShortAtMarket;
if (IsSold) then
BuyToCoverLimit(Close,lote);
end;
```

### Função BuyToCoverStop
*Manual NTSL v4.7 (14/10/2026) — p. 85*

_A função BuyToCoverStop() envia uma ordem de compra do tipo Stop se houver uma posição de venda no ativo.
Se a quantidade não for especificada, será usada a configurada na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função BuyToCoverStop(Stop : Float; Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem.

Limit: Float [Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop.
input

```ntsl
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop, pStop);
end;
```

### Função CancelPendingOrders
*Manual NTSL v4.7 (14/10/2026) — p. 87*

_A função CancelPendingOrders() possui como recurso efetuar o cancelamento de todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas._

**Sintaxe**

```ntsl
Função CancelPendingOrders(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop, caso existam ordens pendentes, ocorrerá o cancelamento e não será plotado nada no gráfico.
input

```ntsl
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop, pstop);
if (HasPendingOrders) then
CancelPendingOrders;
end;
```

### Função ClosePosition
*Manual NTSL v4.7 (14/10/2026) — p. 88*

_A função ClosePosition() envia ordens para encerrar a posição. Esta função cancela todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas. Após confirmação do cancelamento das ordens, será enviada uma ordem para fechar a posição._

**Sintaxe**

```ntsl
Função ClosePosition(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, caso a mínima do candle atual seja igual a do candle anterior será realizada a simulação de uma ordem de compra e então a posição será finalizada.

```ntsl
begin
if (Low = Low[1]) then
BuyAtMarket;
if HasPosition then
ClosePosition;
end;
```

### Função DailyResult
*Manual NTSL v4.7 (14/10/2026) — p. 89*

_A partir da função DailyResult() pode-se verificar o resultado diário das operações, retornado em valor financeiro
(resultado monetário). O parâmetro OpenResult é opcional, e seu valor padrão é verdadeiro._

**Sintaxe**

```ntsl
Função DailyResult(OpenResult: Boolean): Float;
```

**Parâmetros**

OpenResult: Boolean [Opcional]; Se deve retornar o resultado aberto:

– Verdadeiro: Retorna o resultado fechado + aberto;
– Falso: Retorna apenas o resultado fechado;

**Exemplo de uso:** No exemplo, será retornado o resultado fechado + aberto das operações do dia.

```ntsl
var
dResult : Float;
begin
if not HasPosition then
BuyAtMarket;
dResult := DailyResult(True);
Plot(dResult);
end;
```

### Função HasPendingOrders
*Manual NTSL v4.7 (14/10/2026) — p. 90*

_A função HasPendingOrders() retorna se há ordens pendentes._

**Sintaxe**

```ntsl
Função HasPendingOrders(): Boolean;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for igual a do candle anterior e exista uma posição de venda, será inserida uma ordem de compra tipo stop, no preço armazenado na variável pStop, e caso existam ordens input

```ntsl
pendentes, será plotado a MedianPrice() no gráfico.
pstop(132000);
begin
SellShortAtMarket;
if (Low = Low[1]) and (IsSold) then
BuyToCoverStop(pStop,pstop);
if (HasPendingOrders) then
Plot(MedianPrice);
end;
```

### Função HasPosition
*Manual NTSL v4.7 (14/10/2026) — p. 91*

_A função HasPosition() retorna verdadeiro se a posição não é zero._

**Sintaxe**

```ntsl
Função HasPosition(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, ocorrerá a simulação de uma ordem a mercado usando a função HasPosition() para validar se
há posição ou não e, caso exista posição, ocorrerá o plot de BuyPrice() no gráfico.
begin
BuyAtMarket;
if HasPosition then
Plot(BuyPrice);
end;
```

### Função IsBought
*Manual NTSL v4.7 (14/10/2026) — p. 92*

_A função IsBought() tem como funcionalidade determinar se há uma posição de compra em aberto._

**Sintaxe**

```ntsl
Função IsBought(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, caso exista uma posição de compra, haverá a aplicação de uma coloração (verde).
begin
BuyAtMarket;
if (IsBought) then
PaintBar(clGreen);
end;
```

### Função IsSold
*Manual NTSL v4.7 (14/10/2026) — p. 93*

_A função IsSold() tem como funcionalidade determinar se há uma posição de venda em aberto._

**Sintaxe**

```ntsl
Função IsSold(): Boolean;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo, caso exista uma posição de venda, haverá a aplicação de uma coloração (vermelho).
begin
SellShortAtMarket;
if (IsSold) then
PaintBar(clRed);
end;
```

### Função LastTradeResult
*Manual NTSL v4.7 (14/10/2026) — p. 94*

_A partir da função LastTradeResult() pode-se verificar o resultado da última operação encerrada pela au- tomação, retornado em valor financeiro (resultado monetário), considerando exclusivamente o ativo atualmente con- figurado._

**Sintaxe**

```ntsl
Função LastTradeResult(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a automação abre uma posição caso não exista posição aberta e utiliza o resultado da última operação encerrada como critério de validação lógica.

```ntsl
var
nLastResult : Float;
begin
if not HasPosition then
BuyAtMarket;
if Mod(CurrentBar,3) = 0 then
ClosePosition;
nLastResult := LastTradeResult;
if (nLastResult < 0) then
PlotText("Última operação negativa", clRed);
end;
```

### Função MyPrice
*Manual NTSL v4.7 (14/10/2026) — p. 96*

_A função MyPrice() retorna a média entre a máxima, mínima e fechamento._

**Sintaxe**

```ntsl
Função MyPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** a mercado e então o plot da função no gráfico.

```ntsl
No exemplo, será atribuído à variável mPrice, o valor da função MyPrice(), será simulada uma ordem de compra
var
mPrice : Float;
begin
mPrice := MyPrice;
BuyAtMarket;
if (IsBought) then
Plot(mPrice);
end;
```

### Função Position
*Manual NTSL v4.7 (14/10/2026) — p. 97*

_A função Position() retorna o tamanho da posição em lote, positivo para compra e negativo para venda._

**Sintaxe**

```ntsl
Função Position(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável vPosition, a posição, e será simulada uma ordem de compra a mercado e então o plot da função no gráfico.

```ntsl
var
vPosition : Integer;
begin
vPosition := Position;
BuyAtMarket;
if (IsBought) then
Plot(vPosition);
end;
```

### Função PositionQty
*Manual NTSL v4.7 (14/10/2026) — p. 98*

_A função PositionQty() retorna o tamanho da posição em quantidade, positivo para compra e negativo para venda._

**Sintaxe**

```ntsl
Função PositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável vPosition, a posição, e será simulada uma ordem de compra a mercado e então o plot da função no gráfico.

```ntsl
var
vPosition : Float;
begin
vPosition := PositionQty;
BuyAtMarket;
if (IsBought) then
Plot(vPosition);
end;
```

### Função Price
*Manual NTSL v4.7 (14/10/2026) — p. 99*

_A função Price() retorna o preço de compra ou venda da posição, dependendo se estiver comprado ou vendido._

**Sintaxe**

```ntsl
Função Price(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** a mercado e então o plot da função no gráfico.

```ntsl
No exemplo, será atribuído à variável vPrice, o valor da função Price(), será simulada uma ordem de compra
var
vPrice : Float;
begin
vPrice := Price;
BuyAtMarket;
if (IsBought) then
Plot(vPrice);
end;
```

### Função ReversePosition
*Manual NTSL v4.7 (14/10/2026) — p. 100*

_A função ReversePosition() tem como funcionalidade realizar o envio de ordens, a fim de inversão da posição.
Esta função cancela todas ordens enviadas até o momento de sua chamada, no fluxo atual de execução, e as ordens abertas. Após confirmação do cancelamento das ordens, será enviada uma ordem para reverter a posição._

**Sintaxe**

```ntsl
Função ReversePosition(): Void;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, caso a mínima do candle atual for menor a do candle anterior, e exista uma posição de compra, será realizada a reversão.

```ntsl
begin
BuyAtMarket;
if (Low < Low[1]) and (IsBought = True) then
ReversePosition;
end
```

### Função SellPosition
*Manual NTSL v4.7 (14/10/2026) — p. 101*

_A função SellPosition() retorna o tamanho da posição em lote de venda._

**Sintaxe**

```ntsl
Função SellPosition(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável sellPos, irá receber a posição de venda.

```ntsl
var
sellPos : Integer;
begin
SellShortAtMarket;
sellPos := SellPosition;
Plot(sellPos);
end;
```

### Função SellPositionQty
*Manual NTSL v4.7 (14/10/2026) — p. 102*

_A função SellPositionQty() retorna o tamanho da posição em quantidade de venda._

**Sintaxe**

```ntsl
Função SellPositionQty(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável sellPos, irá receber o total da posição de venda.

```ntsl
var
sellPos : Float;
begin
SellShortAtMarket;
sellPos := SellPositionQty;
Plot(sellPos);
end;
```

### Função SellPrice
*Manual NTSL v4.7 (14/10/2026) — p. 103*

_A função SellPrice() retorna o preço de venda da posição._

**Sintaxe**

```ntsl
Função SellPrice(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será atribuído à variável pVenda, o valor de venda da posição, ocorrerá uma simulação de venda e o plot da função no gráfico.

```ntsl
var
pVenda : Float;
begin
SellShortAtMarket;
pVenda := SellPrice;
Plot(pVenda);
end;
```

### Função SellShortAtMarket
*Manual NTSL v4.7 (14/10/2026) — p. 104*

_A função SellShortAtMarket() envia uma ordem de venda a mercado. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo
"Quantidade por Ordem".
Se especificada no código, essa quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellShortAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo abaixo, será executada uma ordem de venda a mercado, caso a mínima do candle atual seja igual a do candle anterior.

```ntsl
begin
if (Low = Low[1]) then
SellShortAtMarket;
end;
```

### Função SellShortLimit
*Manual NTSL v4.7 (14/10/2026) — p. 105*

_Descrição:

A função SellShortLimit() envia uma ordem de venda limite. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de venda apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando comprado em 4 contratos, uma ordem de venda de 8 contratos resulta em posição vendida de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função SellShortLimit(Limit: Float; Quantity: Float; bCanReversePosition: Boolean):

Void;
```

**Parâmetros**

Limit: Float; Preço para a inserção da ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo abaixo, será executada uma ordem de venda a mercado, caso a mínima do candle atual seja igual a do candle anterior.
em 4 contratos, a ordem de venda de 8 contratos é enviada integralmente, resultando em posição vendida de 4 contratos. Sem esse parâmetro, seriam enviados apenas 4 contratos, encerrando a posição sem invertê-la.

```ntsl
begin
if (Low = Low[1]) then
SellShortLimit(Close, lote);
end;
No exemplo a seguir, o parâmetro bCanReversePosition é utilizado para inverter a posição: estando comprado
begin
if not IsBought then
BuyAtMarket(4)
else
SellShortLimit(Close, 8, True);
end;
```

### Função SellShortStop
*Manual NTSL v4.7 (14/10/2026) — p. 107*

_A função SellShortStop() envia uma ordem de venda do tipo stop. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo
"Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código.

Observação

Por padrão, quando existe posição aberta em sentido contrário, a quantidade executada é limitada ao tamanho dessa posição, de modo que a ordem de venda apenas encerra a posição.

Com bCanReversePosition igual a Verdadeiro, a quantidade total informada é enviada, independentemente de haver posição aberta, e a posição pode ser invertida. Por exemplo, estando comprado em 4 contratos, uma ordem de venda de 8 contratos resulta em posição vendida de 4 contratos após a execução._

**Sintaxe**

```ntsl
Função SellShortStop(Stop: Float; Limit: Float; Quantity: Float;

bCanReversePosition: Boolean): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

Limit: Float[Opcional]; Valor do tipo Float que será o limite de preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

bCanReversePosition: Boolean [Opcional]; Define se a ordem pode inverter a posição atual:

– Verdadeiro: Envia a quantidade total informada, mesmo havendo posição aberta em sentido contrário,

permitindo a inversão da posição;

– Falso: Limita a quantidade executada ao tamanho da posição aberta em sentido contrário, não permitindo

a inversão (valor padrão);

**Exemplo de uso:** No exemplo, caso a máxima atual for maior do que a anterior, será inserida uma ordem de venda stop, no preço armazenado na variável pAux.
input

```ntsl
pAux(136000);
begin
if (High > High[1]) then
SellShortStop(pAux,pAux);
end
```

### Função SellToCoverAtMarket
*Manual NTSL v4.7 (14/10/2026) — p. 109*

_A função SellToCoverAtMarket() envia uma ordem de venda a mercado se houver uma posição de compra. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverAtMarket(Quantity: Float): Void;
```

**Parâmetros**

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de venda.

**Exemplo de uso:** No exemplo abaixo, caso a máxima atual seja maior que a máxima anterior e exista uma posição de compra, será executada uma ordem a mercado, para fechar a operação.

```ntsl
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) and (IsBought) then
SellToCoverAtMarket;
end;
```

### Função SellToCoverLimit
*Manual NTSL v4.7 (14/10/2026) — p. 110*

_A função SellToCoverLimit() envia uma ordem de venda limite para finalizar a operação. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverLimit(Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Limit: Float; Preço para a inserção da ordem.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem de compra.

**Exemplo de uso:** No exemplo, caso exista uma posição de compra, será inserida a ordem no preço de fechamento para zerar a posição.

```ntsl
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) and (IsBought) then
SellToCoverLimit(Close);
end;
```

### Função SellToCoverStop
*Manual NTSL v4.7 (14/10/2026) — p. 111*

_A função SellToCoverStop() envia uma ordem stop de venda caso exista uma posição de compra. Se a quantidade não for especificada, será usada a definida na aba de Execução, com mínimo de 1 lote. Na automação, utiliza-se a quantidade do campo "Quantidade por Ordem".
Se especificada no código, a quantidade deve ser múltipla do lote do ativo e prevalece sobre as configurações. O campo "Quantidade máxima da posição" tem prioridade sobre a quantidade definida no código._

**Sintaxe**

```ntsl
Função SellToCoverStop(Stop: Float; Limit: Float; Quantity: Float): Void;
```

**Parâmetros**

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

Limit: Float [Opcional]; Valor que será o limite do preço aceito para execução.

Quantity: Float [Opcional]; Determina a quantidade a ser executada na ordem.

**Exemplo de uso:** No exemplo, caso a máxima do candle atual for maior que a do candle anterior e exista uma posição de compra, será inserida uma ordem de venda do tipo stop, no preço de pAux.
input

```ntsl
pAux(136000);
begin
if not HasPosition then
BuyAtMarket;
if (High > High[1]) then
SellToCoverStop(pAux,pAux,lote);
end
```

### Função SendOrder
*Manual NTSL v4.7 (14/10/2026) — p. 113*

_A partir da função SendOrder() pode-se enviar ordens customizadas, determinando o lado, tipo e quantidade._

**Sintaxe**

```ntsl
Função SendOrder(Side: Integer; Type: Integer; Quantity: Float; Limit: Float; Stop:

Float): Void;
```

**Parâmetros**

Side: Integer; Determina o lado da ordem;

Type: Integer; Tipo da ordem;

Quantity: Float; Determina a quantidade a ser executada na ordem.

Limit: Float; Quantidade de contratos / lotes.

Stop: Float; Valor do tipo Float que será o gatilho da ordem;

**Exemplo de uso:** No exemplo, será efetuada a inserção de uma ordem de compra, tipo Stop, no preço 30.45, com limite de execução até o nível 30.55.

```ntsl
begin
if not HasPosition then
SendOrder(osBuy, otStopLimit, 100, 30.55, 30.45);
end;
```

### Função OpenResult
*Manual NTSL v4.7 (14/10/2026) — p. 114*

_A partir da função OpenResult() pode-se verificar o resultado diário das operações em aberto._

**Sintaxe**

```ntsl
Função OpenResult(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, será retornado o resultado aberto das operações do dia.

```ntsl
var
oResult : Float;
begin
if not HasPosition then
BuyAtMarket;
oResult := OpenResult;
Plot(oResult);
end;
```

### Função XRay
*Manual NTSL v4.7 (14/10/2026) — p. 115*

_A função XRay() permite o monitoramento em tempo real de variáveis e condições dentro de uma estratégia autom- atizada, exibindo essas informações no botão Raio-X do Gerenciador de Automações._

**Sintaxe**

```ntsl
Função XRay(strValue: String; bValue: Boolean; strGroup: String; dValue: Float;

ColorON: Integer; ColorOFF: Integer): Void;
```

**Parâmetros**

strValue: String; Nome identificador da condição ou variável que será exibido no painel Raio-X;

bValue: Boolean; Valor lógico que representa o estado atual da condição (verdadeiro ou falso);

strGroup: String; Define o nome para o grupo que será exibido no raio-x durante a execução ;

dValue: Float [Opcional]; Define o valor da variável;

colorON: Integer [Opcional]; Cor quando a condição for verdadeira;

colorOFF: Integer [Opcional]; Cor quando a condição for falsa;

```ntsl
No exemplo, será exibido o valor em tempo real da automação ao utilizar a função XRay().
var
pBuy : Float;
begin
pBuy := BuyPrice;
if (Low <= Low[1]) then
BuyAtMarket();
Plot(BuyPrice);
XRay("pBuy",(pBuy > 0),"Buy",pBuy);
end;
```

### Função NumberOfPendingOrders
*Manual NTSL v4.7 (14/10/2026) — p. 116*

_A função NumberOfPendingOrders() permite obter o número atual de ordens abertas da sua Automação de Es- tratégias, sendo útil para tomadas de decisão dentro de uma estratégia automatizada._

**Sintaxe**

```ntsl
Função NumberOfPendingOrders(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Observações**

Recomenda-se utilizar a função apenas no modo de execução Ao Satisfazer Condição, pois em outros modos o valor retornado pode estar desatualizado, gerando comportamento imprevisível na estratégia;

**Exemplo de uso:** mantidas até 10 ordens limitadas de compra pendentes, posicionadas abaixo do preço médio de entrada.
input dPrecoOrdem

```ntsl
No exemplo abaixo, a estratégia utiliza a função NumberOfPendingOrders() para garantir que sempre sejam
TicksGradiente(5);
var
nIndex,nFaltando : Integer;
: Float;
begin
if not HasPosition then
BuyAtMarket(1);
nFaltando := 10 - NumberOfPendingOrders();
if nFaltando > 0 then
begin
for nIndex := 1 to nFaltando do
begin
dPrecoOrdem := BuyPrice - (nIndex * MinPriceIncrement * TicksGradiente);
BuyLimit(dPrecoOrdem);
end;
end;
end;
```

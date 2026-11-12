# 05 Anexos Erros Comuns

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Anexos

### Anexos
*Manual NTSL v4.7 (14/10/2026) — p. 574*

Anexos

Este anexo apresenta exemplos de comportamentos incorretos que podem ocorrer ao desenvolver scripts em NTSL, seguidos das respectivas boas práticas para evitá-los. O objetivo é auxiliar desenvolvedores a escrever códigos mais seguros, previsíveis e compatíveis com o motor de execução da plataforma.

Esses casos foram observados com frequência no uso prático da linguagem e, quando corrigidos, contribuem direta- mente para a estabilidade e a assertividade das estratégias criadas.

28.1 Exemplos de funcionamento de estratégias

1 - Nenhuma ordem será criada, já que existe um cancelamento de ordens.

begin

BuyAtMarket;
CancelPendingOrders;

end; //Fim do fluxo de execução

2 - Nenhuma ordem será criada, pois o ClosePosition vai cancelar a ordem BuyAtMarket.

begin

BuyAtMarket;
ClosePosition;

end; //Fim do fluxo de execução

3 - Nenhuma ordem será criada, pois o ReversePosition vai cancelar a ordem SellShortAtMarket.

begin

SellShortAtMarket;
ReversePosition;

end; //Fim do fluxo de execução

4 - Nenhuma ordem será criada, pois é realizada o agrupamento de ordens AtMarket que estão dentro do mesmo fluxo de execução.

begin

BuyAtMarket;
SellShortAtMarket;

end; //Fim do fluxo de execução

5 - O código abaixo não abre ordens covers. Pois ao passar pela linha BuyAtMarket não é gerada uma posição, pois não há execução da ordem. Desta maneira, a posição não é alterada e o SellToCover não será criado já que não há posição.

begin

if not HasPosition then

begin

BuyAtMarket;
SellToCoverLimit(Close + 10 * MinPriceIncrement);
SellToCoverStop(Close - 10 * MinPriceIncrement);

end;

end //Fim do fluxo de execução

Como alternativa, é aconselhável usar o código abaixo. Desta forma quando existir posição as ordens covers serão enviadas.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

SellToCoverLimit(Close + 10 * MinPriceIncrement);
SellToCoverStop(Close - 10 * MinPriceIncrement);

end;

end //Fim do fluxo de execução

6 - Comparações diretas entre valores do tipo float podem resultar em comportamentos inesperados devido à natureza da representação de ponto flutuante em computadores. Pequenas diferenças de precisão podem fazer com que comparações como a < b, a = b ou a > b produzam resultados incorretos.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

if(BuyPrice =

Close + 10)then

ClosePosition;

end;

end //Fim do fluxo de execução

Para evitar esse tipo de problema, utilize a função CompareFloat, que compara dois números float com uma precisão definida em casas decimais.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

if (CompareFloat(BuyPrice , Close + 10, 2) = 0) then

ClosePosition;

end;

end //Fim do fluxo de execução

### Exemplos de funcionamento de estratégias
*Manual NTSL v4.7 (14/10/2026) — p. 574*

28 Anexos

Este anexo apresenta exemplos de comportamentos incorretos que podem ocorrer ao desenvolver scripts em NTSL, seguidos das respectivas boas práticas para evitá-los. O objetivo é auxiliar desenvolvedores a escrever códigos mais seguros, previsíveis e compatíveis com o motor de execução da plataforma.

Esses casos foram observados com frequência no uso prático da linguagem e, quando corrigidos, contribuem direta- mente para a estabilidade e a assertividade das estratégias criadas.

28.1 Exemplos de funcionamento de estratégias

1 - Nenhuma ordem será criada, já que existe um cancelamento de ordens.

begin

BuyAtMarket;
CancelPendingOrders;

end; //Fim do fluxo de execução

2 - Nenhuma ordem será criada, pois o ClosePosition vai cancelar a ordem BuyAtMarket.

begin

BuyAtMarket;
ClosePosition;

end; //Fim do fluxo de execução

3 - Nenhuma ordem será criada, pois o ReversePosition vai cancelar a ordem SellShortAtMarket.

begin

SellShortAtMarket;
ReversePosition;

end; //Fim do fluxo de execução

4 - Nenhuma ordem será criada, pois é realizada o agrupamento de ordens AtMarket que estão dentro do mesmo fluxo de execução.

begin

BuyAtMarket;
SellShortAtMarket;

end; //Fim do fluxo de execução

5 - O código abaixo não abre ordens covers. Pois ao passar pela linha BuyAtMarket não é gerada uma posição, pois não há execução da ordem. Desta maneira, a posição não é alterada e o SellToCover não será criado já que não há posição.

begin

if not HasPosition then

begin

BuyAtMarket;
SellToCoverLimit(Close + 10 * MinPriceIncrement);
SellToCoverStop(Close - 10 * MinPriceIncrement);

end;

end //Fim do fluxo de execução

Como alternativa, é aconselhável usar o código abaixo. Desta forma quando existir posição as ordens covers serão enviadas.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

SellToCoverLimit(Close + 10 * MinPriceIncrement);
SellToCoverStop(Close - 10 * MinPriceIncrement);

end;

end //Fim do fluxo de execução

6 - Comparações diretas entre valores do tipo float podem resultar em comportamentos inesperados devido à natureza da representação de ponto flutuante em computadores. Pequenas diferenças de precisão podem fazer com que comparações como a < b, a = b ou a > b produzam resultados incorretos.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

if(BuyPrice =

Close + 10)then

ClosePosition;

end;

end //Fim do fluxo de execução

Para evitar esse tipo de problema, utilize a função CompareFloat, que compara dois números float com uma precisão definida em casas decimais.

begin

if not HasPosition then

begin

BuyAtMarket;

end

else

begin

if (CompareFloat(BuyPrice , Close + 10, 2) = 0) then

ClosePosition;

end;

end //Fim do fluxo de execução

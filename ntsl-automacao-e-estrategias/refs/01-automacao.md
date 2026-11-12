# 01 Automacao

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Automação de Estratégias

### Automação de Estratégias
*Manual NTSL v4.7 (14/10/2026) — p. 40*

Automação de Estratégias

O módulo de Automação de Estratégias tem o objetivo de automatizar as estratégias de execução criadas no Editor de Estratégias. Ele está disponível nas versões mais avançadas das plataformas Nelogica, em modo simulação de forma gratuita e disponível para contas reais por meio de módulos opcionais.
O novo módulo de automação espelha o funcionamento do backtest das estratégias para execução de ordens reais e em simulador. Para fazer o gerenciamento dessas automações pode-se acessar o menu Estratégias > Automação de
Estratégias.
A janela de Automações de Estratégias permite que possamos criar e gerenciar automações, acompanhar o resultado de todas as automações de maneira simplificada. Caso queira um detalhamento maior da automação pode-se clicar com o botão direito e ir em "Detalhes da Automação". Nos detalhes é possível acompanhar todos os eventos que a execução gerou, assim como diversos indicadores de performance da automação.

Os próximos capítulos detalham desde a criação de uma estratégia de execução utilizando o novo módulo de Au- tomação de Estratégias, como o usuário pode acompanhar essas automações, e por fim detalha regras gerais da execução das estratégias.

11.1 Criando uma estratégia de execução

Para criar uma automação você precisará criar uma estratégia de execução, que pode ser criada a partir do Editor de
Estratégias. Se você já sabe o que é isso, pode seguir para o próximo passo.
Ao abrir o Editor de Estratégias, você pode criar sua estratégia de execução utilizando funções de backtest (essas funções irão caracterizar a estratégia como sendo uma estratégia de execução e isso possibilitará a sua seleção no próximo passo para que a estratégia seja automatizada). Para criar uma estratégia de execução você deve usar funções do módulo backtest, que pode ser visto na imagem abaixo:

Sugerimos que você utilize a função Nova estratégia, e selecione exemplos de estratégias de execução se você não estiver familiarizado com programação ou com o Editor de Estratégias.

Abaixo é apresentado um exemplo de estratégia, utilizando o indicador IFR/RSI, que pode ser utilizado no módulo de estratégias automatizadas:

/////////////////////////////////////////////////////////////////////
//
//
IFR
///////////////////////////////////////////////////////////////////// begin

// Verifica se está comprado

if (IsBought) then

begin

// Fecha a posição com uma venda caso o IFR
// esteja superior a 70 (sobrecomprado)

if (RSI(9,0) > 70) then
SellToCoverAtMarket;

end
// Verifica se está vendido

else if (IsSold) then

begin

// Fecha a posição com uma compra caso o IFR
// esteja inferior a 30 (sobrevendido)
if (RSI(9,0) < 30) then
BuyToCoverAtMarket;

end;

end;

11.2 Criando uma automação

Para criar uma nova automação, basta abrir a interface de controle e localizar o botão "Nova Automação", disponível no menu superior da janela. Esse botão estará sempre visível nessa área da interface. Caso ainda não exista nenhuma automação criada, o mesmo botão "Nova Automação" será exibido em destaque no centro da tela.

Após clicar nesse botão será aberta a janela de criação da da estratégia automatizada onde será configurada os parâmetros da automação em duas etapas. A primeira etapa contém configurações essenciais e obrigatórias para a criação da automação.
Na primeira etapa, nas configurações obrigatórias, é possível definir a conta, a estratégia de execução, ativo alvo, quantidade por ordem, quantidade máxima da posição e o período que a estratégia usará como base para as análises.
A Estratégia de execução é o "cérebro" da automação. Aqui será selecionado aquela estratégia implementada no editor. Ao clicar no botão "Selecionar Estratégia" estarão listadas todas as estratégias de execução presentes na plataforma. Além disso, caso a estratégia selecionada possua parâmetros de entrada, os mesmos serão listados nessa janela para que possam ser editados da melhor maneira para a estratégia específica.

A próxima etapa contém configurações opcionais que podem ser exploradas nos menus acima quando as Configu- rações Avançadas estiverem ativas (canto inferior esquerdo). Aqui podemos configurar opções de Entrada e Saída,
Risco e Segurança. Essas opções estão detalhadas a seguir:

11.3 Opções de entrada

Nesta seção é possível especificar parâmetros que alterem a estratégia de abertura de ordens da automatização.
Em ordem de entrada você pode especificar qual vai ser o tipo de abertura de posição, ou seja, se a estratégia irá abrir novas posições apenas de compra, ou apenas de venda ou ambos os lados.
É possível também escolher se você deseja confirmar cada ordem de aumento de posição. Neste caso, a confirmação de ordens será mostrada para cada nova ordem da estratégia.

11.4 Modo de Execução

Há dois modos de execução: "Realizar envio de ordens no fechamento do candle" e "Realizar envio de ordens quando a condição for satisfeita". A mudança de uma opção para a outra causa grande impacto na maneira como o código da estratégia é interpretado. Abaixo, é detalhado como cada modo se comporta.

Ordens no Fechamento do Candle

Esta é a configuração padrão do modo de execução da automação e é a que traz maior semelhança com as operações realizadas por meio do backtest no Editor de Estratégias. Para ativar este modo selecione a opção "Realizar envio de ordens no fechamento do candle".

A cada fechamento de candle, o código para envio de ordens é reavaliado e se torna disponível para o envio de novas ordens de entrada, ou a alteração de ordens de entrada abertas ou de ordens Cover, caso haja posição. Deste modo, a escolha de tempo gráfico é crucial para sua automação.

Ordens que foram enviadas ao final de um candle e que não forem executadas até o final do candle seguinte serão canceladas quando o próximo candle finalizar, a menos que a estratégia do usuário as reenvie ou edite, situação em que serão editadas de acordo com a estratégia. Uma vez que, apenas sabemos que um candle foi finalizado quando o próximo iniciar em gráficos atemporais, poderá ocorrer a execução de ordens em um candle subsequente caso o cancelamento chegue na bolsa após a execução da mesma.

É importante ressaltar que a automação poderá apresentar divergências em relação ao backtest ao ser comparado com a execução da automação em uma conta de simulação (ordens simuladas) ou conta real (ordens reais), operando ao vivo no mercado real. Isso se deve a diversos fatores, como: Spread, Margem, RLP, Delays na Bolsa, Alta volatil- idade de preço de alguns ativos, entre outros.

Essas diferenças acontecem primordialmente em séries de dados atemporais, as quais podem causar a criação de muitos candles em pouco tempo. No backtest, por termos zero delay, as ordens são criadas sempre no candle subsequente, porém no mercado real, onde há delay, por menor que ele seja, ordens podem ser executadas em candles subsequentes já que não houve tempo na criação do cancelamento dessas ordens.

Além disso, há uma segunda opção caso esse modo seja selecionado. Ativando essa função, você terá uma execução mais próxima ao backtest, já que o código executará apenas no fechamento do candle ou com uma atualização de posição. Com a opção desativada, o código é executado diversas vezes no mesmo candle.

Ordens ao Satisfazer Condição

Este é o modo avançado de envio de ordens automatizadas. Ele não é compatível com o backtest da aplicação, uma vez que realiza operações a qualquer momento durante a formação dos candles, o que impede o backtest de simular adequadamente esse modo de execução. Para ativar este modo, selecione a opção "Realizar envio de ordens quando a condição for satisfeita".

Neste modo, o código é constantemente avaliado durante a execução da automação, e as ordens podem ser envi- adas a qualquer momento durante a formação do candle, desde que o código satisfaça a condição de envio. Como mostrado na imagem acima, existem duas opções que podem ser configuradas neste modo. Detalhamos cada uma delas a seguir:

A primeira opção, "Esperar o fechamento do candle para primeira execução" faz com que a automação aguarde o encerramento do candle atual para começar a executar ordens. Ou seja, somente quando um novo candle for iniciado é que as ordens serão enviadas.

A segunda opção, "Permitir múltiplos envios e alterações de ordens para a mesma barra", quando habil- itada, permite que a automação envie e modifique ordens de entrada e saída à medida que o código satisfaça as condições de envio. Isso ocorre respeitando um intervalo mínimo entre as alterações, como medida de proteção contra envio excessivo de ordens (flood). Caso essa opção não esteja selecionada, a automação limitará o envio e a modificação de ordens a apenas uma vez por barra, sempre que a condição definida no código for satisfeita.

A estratégia de atualização das ordens, quando a opção de múltiplos envios para a mesma barra estiver habilitada, seguirá uma equação linear que depende da proximidade das ordens em relação ao preço atual. Ou seja:

• Se as ordens estiverem muito distantes do preço atual, serão atualizadas com menor frequência;

• Se estiverem muito próximas do preço atual, serão atualizadas com maior frequência.

Vale ressaltar que todas as ordens são atualizadas simultaneamente. No entanto, a frequência de atualização é definida com base na ordem mais próxima do preço atual.

Existe um intervalo mínimo de atualização de 10 segundos. Assim, as ordens serão enviadas ou alteradas, no máximo, a cada 10 segundos.

O temporizador de envio de ordens só é atualizado quando ocorre alguma modificação. Ou seja, se o código enviar uma ordem diferente das que já estão apregoadas, o sistema irá verificar quando ocorreu a última modificação e determinar o momento da próxima atualização, liberando então novos envios ou alterações.

Assim como no modo de atualização ao fechamento do candle, as ordens de saída sempre serão atualizadas quando houver um aumento de posição, a fim de realizar o rebalanceamento das ordens de cobertura.

Neste modo de execução, as condições para envio de ordens são avaliadas de forma contínua e em tempo real, permitindo que a entrada ocorra imediatamente assim que a condição especificada for satisfeita como, por exemplo, no cruzamento de médias móveis ou no rompimento de um nível de preço pré-definido. Essa abordagem proporciona maior agilidade e precisão na execução, pois as ordens podem ser enviadas no exato momento em que as condições são atendidas.

Lembre-se de que este modo não é compatível com o backtest de estratégias, pois depende de dados em tempo real, o que inviabiliza a previsão precisa do comportamento da automação. Para testar o desempenho de sua estratégia neste modo, é necessário utilizar o recurso de replay de mercado ou realizar os testes diretamente no pregão, utilizando uma conta de simulação.

11.5 Horários de Operação

Nesta seção é possível configurar os períodos em que a estratégia poderá ou não enviar ordens, conforme as opções disponíveis:

• Intervalo de Execução: define o período em que a estratégia estará habilitada para enviar ordens. Após o horário final do intervalo, a estratégia não será pausada, mas deixará de enviar novas ordens automaticamente.
Caso deseje, é possível marcar a opção Zerar Posição para que, ao final do intervalo, todas as posições abertas sejam encerradas automaticamente.

• Intervalo de Suspensão: ao invés de definir quando a automação irá operar, este modo permite configurar períodos em que a estratégia não deverá operar. Durante esse intervalo, nenhuma nova ordem será enviada.
Assim como no modo anterior, é possível habilitar a opção Zerar Posição para forçar o encerramento de posições abertas no início do intervalo de suspensão.

Essas configurações permitem maior controle sobre a atuação da estratégia durante o pregão, possibilitando, por exemplo, evitar operações em horários de baixa liquidez ou eventos de maior volatilidade.

11.6 Opções de saída

Nesta outra etapa da configuração, é possível alterar configurações de saída de sua automação.
Aqui é possível configurar uma estratégia OCO que será aberta junto com suas ordens, mas atenção, caso você já tenha ordens de saída implementadas em sua estratégia de negociação (ordens de cobertura), estas não serão mais executadas já que as ordens OCO terão preferência.

Também é possível configurar nesta seção a zeragem automática por horário. A plataforma precisa estar aberta para que a zeragem aconteça, assim como para que a automação funcione.

11.7 Risco

Seguindo as configurações temos as configurações de risco da automação. Na seção Pausar e Zerar ao Alcançar é possível configurar parâmetros que irão pausar e encerrar as posições abertas de acordo com um objetivo de ganho, ou um limite de perda. Caso você não deseje encerrar a posição quando atingir um objetivo de ganho seleciona a opção "Não Zerar ao Atingir Objetivo de Ganho".

Atualmente, o mecanismo de zeragem do risco funciona por meio do envio de uma ordem a mercado assim que o valor de meta de ganho ou de limite de perda é atingido. Dessa forma, pode existir uma diferença entre o preço identificado no momento do disparo do gatilho e o preço efetivo de execução da ordem de zeragem, permitindo uma margem de resultado positiva ou negativa além do risco configurado.

Já a seção Pausar ao Alcançar possibilita que a automação seja pausada quando alcançados os números de perdas consecutivas e máximo de operações configurados.

Aqui também disponibilizamos um atalho para que você possa configurar o risco global da carteira/conta no gerenci- ador de risco da plataforma.

11.8 Segurança

Por fim, na seção Segurança, temos algumas configurações para definir o comportamento da estratégia em caso ocorra um erro de execução no código da mesma ou eventuais mudanças do mercado, como a entrada do ativo em

leilão.

Uma vez criada a automação, você pode visualizá-la na janela Automação de Estratégias:

11.9 Acompanhamento

Para acompanhar a sua automação você pode visualizar um resumo rápido das principais informações na lista de automações da janela Automação de Estratégias. Nela você pode visualizar o status, conta e carteira em que a automação está vinculada, ativo, nome da estratégia, período gráfico e os resultados relacionados à execução.
Você também pode visualizar nesta janela um resumo das estatísticas relacionadas a essa estratégia que contém mais detalhes da estratégia:

Para ligar/pausar uma automação de maneira individual pode-se utilizar o painel, e clicar em executar:

Através do menu de contexto também é possível zerar a posição de uma estratégia pausada ou Pausar + Zerar Posição de uma estratégia em execução. Podemos também editar o código da automação no Editor de Estratégias, Excluir a automação que irá excluir também a carteira atrelada a ela. Para realizar edições na sua automação, você pode, dentro do interface de controle, clicar com botão direito na estratégia desejada e ir em "Editar Automação" ou clicar diretamente na engrenagem. Lembrando que caso a sua automação esteja ligada, ao realizar alguma edição ela será pausada.

Para acompanhar os detalhes do que a execução está executando, vá em Detalhes da Automação. Nesta janela você poderá acompanhar tanto as ordens e sinais que a estratégia está gerando, como também acompanhar a performance e resultados da estratégia mais detalhadamente.

Na janela de Automações é possível utilizar os botões no canto superior direito da interface de controle para pausar todas as automações em execução ou para pausar e zerar todas as posições em aberto:

Caso você possua alguma automação ligada será possível identificar mesmo com a janela de estratégias automatizadas fechadas, pois no menu superior da sua Plataforma será destacado em azul o menu de Estratégias.

Neste menu você será informado quantas estratégias você possui em execução e permitirá que você tome ações rápidas através do menu como pausar tudo ou pausar e zerar tudo.

11.10 Raio-X

_dos principais recursos introduzidos na Automação 2.0. Ela foi desenvolvida para proporcionar maior visibilidade e controle sobre as condições e variáveis envolvidas na execução de estratégias automatizadas.

Objetivo

A função XRay permite:

• Acompanhar o estado das condições utilizadas na lógica da estratégia.

• Visualizar os valores atuais das variáveis envolvidas na tomada de decisão.

• Agrupar visualmente as condições no Gerenciador de Automações, utilizando cores e nomes distintos para

facilitar a leitura (ex: amarelo para compra, verde para venda).

Para que as informações apareçam corretamente no Gerenciador de Automações, é necessário inserir a função XRay no código da estratégia. A chamada da função deve indicar o nome da condição, seu valor lógico, o grupo ao qual pertence, o valor associado e a cor correspondente.

Visualização no Gerenciador de Automações

Ao executar uma automação com a função XRay no código, o botão Raio-X ficará disponível no Gerenciador de
Automações. Através dele, é possível:

• Verificar quais condições foram satisfeitas durante a execução.

• Observar os valores das variáveis associadas a cada condição.

• Distinguir entre diferentes grupos de condições (como compra e venda) por meio de cores e identificadores.

Diferenciais do recurso

• Facilita o entendimento do comportamento da automação durante a execução.

• Permite identificar rapidamente falhas lógicas ou inconsistências nas condições.

• Atua como uma ferramenta de depuração visual para aprimoramento das estratégias.

Para mais informações sobre a função XRay, consulte a seção 15.37 - Função XRay no capítulo Funções de
Backtesting.

11.11 Regras de Execução

As automações de estratégias funcionam com as mesmas regras que são utilizadas no backtest das estratégias de execução. Para entender melhor o que cada função faz relacionada à execução de ordens, recomendamos primeira- mente a leitura da seção 15 - Funções de Backtesting. Aqui detalhamos as regras por trás dos mecanismos de automação para facilitar o entendimento do usuário na hora de implementar uma estratégia de execução já pensando na sua automação.

Reprocessamento do candle em aumentos de posição

Caso houver execução de alguma ordem (aumento de posição), o código é reprocessado para a criação de eventuais ordens de cobertura da operação (ordens ToCover). A reexecução da estratégia para posicionamento de ordens de cobertura acontece quando ordens forem executadas, ou seja, podem ocorrer no meio de um candle para não deixar o usuário exposto a riscos do mercado. Nesse reprocessamento, por mais que o código faça a chamada de ordens que poderiam aumentar a exposição, essas ordens não são enviadas. Mais detalhes sobre ordens de cobertura podem ser vistos a seguir.

Ordens para aumento de posição (Buy e Sell)

É possível enviar ordens Buy e Sell tanto quando você estiver comprado ou vendido, porém quando uma ordem
Buy for enviada enquanto você estiver em uma posição vendida, ela será tratada como uma ordem de cobertura automaticamente. O mesmo acontece para uma ordem Sell, quando você estiver uma posição comprada, ela será tratada como uma ordem de cobertura. Caso contrário, elas apenas aumentaram a sua posição até o limite definido na configuração da estratégia.
Ordens conflitantes são automaticamente gerenciadas pelo automatizador, ou seja, quando for enviada uma ordem
BuyToCover e você estiver em uma posição comprada ou zerada, ela será ignorada, da mesma maneira se for enviada uma ordem SellToCover e você estiver em uma posição vendida ou zerada, ela também será ignorada.

Ordens de cobertura de posição (BuyToCover e SellToCover)

Ordens de cobertura, ou ordens ToCover, nunca irão inverter a sua posição; elas garantem que a ordem contrária vai respeitar sempre a posição da operação. Recomendamos que o programador utilize sempre ordens de saída de posição como ordens ToCover explicitamente no código para garantir que o operacional que o usuário está programando está correto. Para isso, as ordens ToCover são sempre enviadas como ordens OCO, logo você não precisa se preocupar em gerenciar e cancelar eventuais ordens de cobertura que poderiam ficar abertas após a execução de apenas uma das pernas de saída.
Ordens de cobertura são enviadas ou atualizadas a toda mudança de candle, cabe ao usuário gerenciar a quantidade de cada ordem caso você esteja posicionado em mais de um lote para cobrir corretamente a exposição ao mercado. Na finalização do candle, caso o código indique um envio de um mesmo número de ordens de cobertura, será realizada uma edição da OCO para os novos valores de preço correspondentes. Por outro lado, caso o envio aumente ou diminua o número de ordens para aquele candle, a OCO aberta será cancelada, e será enviada uma nova OCO com as saídas definidas pelo código.

Ordens OCO

Caso o usuário configure uma ordem OCO pela configuração da automação, as ordens de cobertura definidas pela estratégia serão desconsideradas, já que todas ordens já vão possuir essa cobertura natural da ordem OCO.

Indicadores que atualizam valores anteriores

Se forem utilizados indicadores que alterem seus valores em candles antigos (candles já finalizados), o valor do indicador que será considerado será o do momento em que o candle finalizar, desse modo caso não houver a entrada da execução na virada do candle, não será feito envio de ordens para aquele candle no futuro, mesmo que algum indicador altere seu valor no passado e troque a decisão de envio de ordem. Alguns exemplos de indicadores que podem causar esse comportamento são indicadores que tem apenas um valor durante todo dia, por exemplo: Preço
Ask e Bid e também indicadores que decidem apenas depois de alguns candles, como por exemplo o Detector de topos e fundos ou a linha Chikou Span (2) do indicador IchimokuCloud, entre outros.

Cálculo Automático do Preço Limite (a partir do Preço Stop)

A NTSL possui suporte para o cálculo automático do preço limite em ordens do tipo Stop, quando esse valor não é explicitamente definido no código. Esse mecanismo garante que as ordens sejam enviadas com parâmetros válidos e aceitos pela bolsa ou corretora, prevenindo rejeições por ultrapassarem as bandas de preço permitidas.
Esse processo define a diferença máxima entre o preço stop e o preço limite, com base nas características do ativo e nas regras do ambiente de negociação. As regras aplicadas são as seguintes:

• Ativos com valor mínimo de tick configurado (variação mínima permitida entre ofertas):

– Criptomoedas: diferença igual a 1 tick.

– Contratos ISDI1 (ex.: swaps, compromissadas de índice): diferença igual a 7 ticks.

– Opções: diferença igual a 20 ticks.

– Contratos futuros da BMF:

* Criptoativos: diferença igual a 100 ticks.
* Demais contratos futuros da BMF: diferença igual a 30 ticks.

• Ações negociadas na B3 (mercado Bovespa): limite de 15% sobre o preço de referência, respeitando

a margem operacional dentro do limite de 20% estabelecido pela bolsa.

• Ativos operados por integração externa: limite de 1% sobre o preço.

• Demais ativos não contemplados pelas regras anteriores: limite de 5% sobre o preço.

Caso o ativo não possua tick mínimo configurado (ou seja, o valor seja igual a zero), será aplicado automatica- mente um valor padrão de 1% sobre o preço de referência como fallback de segurança.

Esse comportamento assegura que, mesmo na ausência de um valor de limite explicitamente definido na ordem, o sistema utilizará parâmetros compatíveis com os requisitos operacionais do mercado, garantindo o envio bem-sucedido da ordem.

11.12 Utilização da Função ConsoleLog na Automação

A função ConsoleLog pode ser utilizada dentro das automações em NTSL para registrar eventos em tempo real diretamente nos eventos da automação.
Essa funcionalidade é especialmente útil para depuração de estratégias, acompanhamento de variáveis internas e verificação de condições durante a execução.

Como funciona

• As mensagens registradas por ConsoleLog ficam visíveis na janela de Detalhes da Automação.

• O comportamento da emissão dos logs varia conforme o modo de execução da automação:

– Modo Candle a Candle: os logs são enviados a cada novo candle e a cada reavaliação de candle.

– Modo Ao Satisfazer Condição: os logs são enviados a cada 5 segundos ou a cada reavaliação de

candle por mudança de posição._

**Exemplo de uso:** No exemplo acima, sempre que ocorrer um cruzamento entre as médias móveis, a automação registrará um log informativo na janela de Detalhes da Automação, permitindo acompanhar em tempo real os eventos da es- tratégia.

```ntsl
var
sAvgFast ,sAvgSlow ,sPrevAvgFast ,sPrevAvgSlow : Float;
begin
sAvgFast := Media(9,Close);
sAvgSlow := Media(21,Close);
sPrevAvgFast := sAvgFast[1];
sPrevAvgSlow := sAvgSlow[1];
if (sPrevAvgFast < sPrevAvgSlow) and (sAvgFast > sAvgSlow) then
begin
ConsoleLog("Cruzamento de compra detectado no preço " + sPrevAvgFast);
buyLimit(Close,1);
end
else if (sPrevAvgFast > sPrevAvgSlow) and (sAvgFast < sAvgSlow) then
begin
ConsoleLog("Cruzamento de venda detectado no preço " + sPrevAvgSlow);
SellShortLimit(Close,1);
end;
end;
```

### Criando uma estratégia de execução
*Manual NTSL v4.7 (14/10/2026) — p. 40*

11 Automação de Estratégias

O módulo de Automação de Estratégias tem o objetivo de automatizar as estratégias de execução criadas no Editor de Estratégias. Ele está disponível nas versões mais avançadas das plataformas Nelogica, em modo simulação de forma gratuita e disponível para contas reais por meio de módulos opcionais.
O novo módulo de automação espelha o funcionamento do backtest das estratégias para execução de ordens reais e em simulador. Para fazer o gerenciamento dessas automações pode-se acessar o menu Estratégias > Automação de
Estratégias.
A janela de Automações de Estratégias permite que possamos criar e gerenciar automações, acompanhar o resultado de todas as automações de maneira simplificada. Caso queira um detalhamento maior da automação pode-se clicar com o botão direito e ir em "Detalhes da Automação". Nos detalhes é possível acompanhar todos os eventos que a execução gerou, assim como diversos indicadores de performance da automação.

Os próximos capítulos detalham desde a criação de uma estratégia de execução utilizando o novo módulo de Au- tomação de Estratégias, como o usuário pode acompanhar essas automações, e por fim detalha regras gerais da execução das estratégias.

11.1 Criando uma estratégia de execução

Para criar uma automação você precisará criar uma estratégia de execução, que pode ser criada a partir do Editor de
Estratégias. Se você já sabe o que é isso, pode seguir para o próximo passo.
Ao abrir o Editor de Estratégias, você pode criar sua estratégia de execução utilizando funções de backtest (essas funções irão caracterizar a estratégia como sendo uma estratégia de execução e isso possibilitará a sua seleção no próximo passo para que a estratégia seja automatizada). Para criar uma estratégia de execução você deve usar funções do módulo backtest, que pode ser visto na imagem abaixo:

Sugerimos que você utilize a função Nova estratégia, e selecione exemplos de estratégias de execução se você não estiver familiarizado com programação ou com o Editor de Estratégias.

### Criando uma automação
*Manual NTSL v4.7 (14/10/2026) — p. 42*

Abaixo é apresentado um exemplo de estratégia, utilizando o indicador IFR/RSI, que pode ser utilizado no módulo de estratégias automatizadas:

/////////////////////////////////////////////////////////////////////
//
//
IFR
///////////////////////////////////////////////////////////////////// begin

// Verifica se está comprado

if (IsBought) then

begin

// Fecha a posição com uma venda caso o IFR
// esteja superior a 70 (sobrecomprado)

if (RSI(9,0) > 70) then
SellToCoverAtMarket;

end
// Verifica se está vendido

else if (IsSold) then

begin

// Fecha a posição com uma compra caso o IFR
// esteja inferior a 30 (sobrevendido)
if (RSI(9,0) < 30) then
BuyToCoverAtMarket;

end;

end;

11.2 Criando uma automação

Para criar uma nova automação, basta abrir a interface de controle e localizar o botão "Nova Automação", disponível no menu superior da janela. Esse botão estará sempre visível nessa área da interface. Caso ainda não exista nenhuma automação criada, o mesmo botão "Nova Automação" será exibido em destaque no centro da tela.

Após clicar nesse botão será aberta a janela de criação da da estratégia automatizada onde será configurada os parâmetros da automação em duas etapas. A primeira etapa contém configurações essenciais e obrigatórias para a criação da automação.
Na primeira etapa, nas configurações obrigatórias, é possível definir a conta, a estratégia de execução, ativo alvo, quantidade por ordem, quantidade máxima da posição e o período que a estratégia usará como base para as análises.
A Estratégia de execução é o "cérebro" da automação. Aqui será selecionado aquela estratégia implementada no editor. Ao clicar no botão "Selecionar Estratégia" estarão listadas todas as estratégias de execução presentes na plataforma. Além disso, caso a estratégia selecionada possua parâmetros de entrada, os mesmos serão listados nessa janela para que possam ser editados da melhor maneira para a estratégia específica.

A próxima etapa contém configurações opcionais que podem ser exploradas nos menus acima quando as Configu- rações Avançadas estiverem ativas (canto inferior esquerdo). Aqui podemos configurar opções de Entrada e Saída,
Risco e Segurança. Essas opções estão detalhadas a seguir:

### Opções de entrada
*Manual NTSL v4.7 (14/10/2026) — p. 44*

Nesta seção é possível especificar parâmetros que alterem a estratégia de abertura de ordens da automatização.
Em ordem de entrada você pode especificar qual vai ser o tipo de abertura de posição, ou seja, se a estratégia irá abrir novas posições apenas de compra, ou apenas de venda ou ambos os lados.
É possível também escolher se você deseja confirmar cada ordem de aumento de posição. Neste caso, a confirmação de ordens será mostrada para cada nova ordem da estratégia.

11.4 Modo de Execução

Há dois modos de execução: "Realizar envio de ordens no fechamento do candle" e "Realizar envio de ordens quando a condição for satisfeita". A mudança de uma opção para a outra causa grande impacto na maneira como o código da estratégia é interpretado. Abaixo, é detalhado como cada modo se comporta.

### Modo de Execução
*Manual NTSL v4.7 (14/10/2026) — p. 44*

11.3 Opções de entrada

Nesta seção é possível especificar parâmetros que alterem a estratégia de abertura de ordens da automatização.
Em ordem de entrada você pode especificar qual vai ser o tipo de abertura de posição, ou seja, se a estratégia irá abrir novas posições apenas de compra, ou apenas de venda ou ambos os lados.
É possível também escolher se você deseja confirmar cada ordem de aumento de posição. Neste caso, a confirmação de ordens será mostrada para cada nova ordem da estratégia.

11.4 Modo de Execução

Há dois modos de execução: "Realizar envio de ordens no fechamento do candle" e "Realizar envio de ordens quando a condição for satisfeita". A mudança de uma opção para a outra causa grande impacto na maneira como o código da estratégia é interpretado. Abaixo, é detalhado como cada modo se comporta.

Ordens no Fechamento do Candle

Esta é a configuração padrão do modo de execução da automação e é a que traz maior semelhança com as operações realizadas por meio do backtest no Editor de Estratégias. Para ativar este modo selecione a opção "Realizar envio de ordens no fechamento do candle".

A cada fechamento de candle, o código para envio de ordens é reavaliado e se torna disponível para o envio de novas ordens de entrada, ou a alteração de ordens de entrada abertas ou de ordens Cover, caso haja posição. Deste modo, a escolha de tempo gráfico é crucial para sua automação.

Ordens que foram enviadas ao final de um candle e que não forem executadas até o final do candle seguinte serão canceladas quando o próximo candle finalizar, a menos que a estratégia do usuário as reenvie ou edite, situação em que serão editadas de acordo com a estratégia. Uma vez que, apenas sabemos que um candle foi finalizado quando o próximo iniciar em gráficos atemporais, poderá ocorrer a execução de ordens em um candle subsequente caso o cancelamento chegue na bolsa após a execução da mesma.

É importante ressaltar que a automação poderá apresentar divergências em relação ao backtest ao ser comparado com a execução da automação em uma conta de simulação (ordens simuladas) ou conta real (ordens reais), operando ao vivo no mercado real. Isso se deve a diversos fatores, como: Spread, Margem, RLP, Delays na Bolsa, Alta volatil- idade de preço de alguns ativos, entre outros.

Essas diferenças acontecem primordialmente em séries de dados atemporais, as quais podem causar a criação de muitos candles em pouco tempo. No backtest, por termos zero delay, as ordens são criadas sempre no candle subsequente, porém no mercado real, onde há delay, por menor que ele seja, ordens podem ser executadas em candles subsequentes já que não houve tempo na criação do cancelamento dessas ordens.

Além disso, há uma segunda opção caso esse modo seja selecionado. Ativando essa função, você terá uma execução mais próxima ao backtest, já que o código executará apenas no fechamento do candle ou com uma atualização de posição. Com a opção desativada, o código é executado diversas vezes no mesmo candle.

Ordens ao Satisfazer Condição

Este é o modo avançado de envio de ordens automatizadas. Ele não é compatível com o backtest da aplicação, uma vez que realiza operações a qualquer momento durante a formação dos candles, o que impede o backtest de simular adequadamente esse modo de execução. Para ativar este modo, selecione a opção "Realizar envio de ordens quando a condição for satisfeita".

Neste modo, o código é constantemente avaliado durante a execução da automação, e as ordens podem ser envi- adas a qualquer momento durante a formação do candle, desde que o código satisfaça a condição de envio. Como mostrado na imagem acima, existem duas opções que podem ser configuradas neste modo. Detalhamos cada uma delas a seguir:

A primeira opção, "Esperar o fechamento do candle para primeira execução" faz com que a automação aguarde o encerramento do candle atual para começar a executar ordens. Ou seja, somente quando um novo candle for iniciado é que as ordens serão enviadas.

A segunda opção, "Permitir múltiplos envios e alterações de ordens para a mesma barra", quando habil- itada, permite que a automação envie e modifique ordens de entrada e saída à medida que o código satisfaça as condições de envio. Isso ocorre respeitando um intervalo mínimo entre as alterações, como medida de proteção contra envio excessivo de ordens (flood). Caso essa opção não esteja selecionada, a automação limitará o envio e a modificação de ordens a apenas uma vez por barra, sempre que a condição definida no código for satisfeita.

A estratégia de atualização das ordens, quando a opção de múltiplos envios para a mesma barra estiver habilitada, seguirá uma equação linear que depende da proximidade das ordens em relação ao preço atual. Ou seja:

• Se as ordens estiverem muito distantes do preço atual, serão atualizadas com menor frequência;

• Se estiverem muito próximas do preço atual, serão atualizadas com maior frequência.

### Horários de Operação
*Manual NTSL v4.7 (14/10/2026) — p. 46*

Vale ressaltar que todas as ordens são atualizadas simultaneamente. No entanto, a frequência de atualização é definida com base na ordem mais próxima do preço atual.

Existe um intervalo mínimo de atualização de 10 segundos. Assim, as ordens serão enviadas ou alteradas, no máximo, a cada 10 segundos.

O temporizador de envio de ordens só é atualizado quando ocorre alguma modificação. Ou seja, se o código enviar uma ordem diferente das que já estão apregoadas, o sistema irá verificar quando ocorreu a última modificação e determinar o momento da próxima atualização, liberando então novos envios ou alterações.

Assim como no modo de atualização ao fechamento do candle, as ordens de saída sempre serão atualizadas quando houver um aumento de posição, a fim de realizar o rebalanceamento das ordens de cobertura.

Neste modo de execução, as condições para envio de ordens são avaliadas de forma contínua e em tempo real, permitindo que a entrada ocorra imediatamente assim que a condição especificada for satisfeita como, por exemplo, no cruzamento de médias móveis ou no rompimento de um nível de preço pré-definido. Essa abordagem proporciona maior agilidade e precisão na execução, pois as ordens podem ser enviadas no exato momento em que as condições são atendidas.

Lembre-se de que este modo não é compatível com o backtest de estratégias, pois depende de dados em tempo real, o que inviabiliza a previsão precisa do comportamento da automação. Para testar o desempenho de sua estratégia neste modo, é necessário utilizar o recurso de replay de mercado ou realizar os testes diretamente no pregão, utilizando uma conta de simulação.

11.5 Horários de Operação

Nesta seção é possível configurar os períodos em que a estratégia poderá ou não enviar ordens, conforme as opções disponíveis:

• Intervalo de Execução: define o período em que a estratégia estará habilitada para enviar ordens. Após o horário final do intervalo, a estratégia não será pausada, mas deixará de enviar novas ordens automaticamente.
Caso deseje, é possível marcar a opção Zerar Posição para que, ao final do intervalo, todas as posições abertas sejam encerradas automaticamente.

• Intervalo de Suspensão: ao invés de definir quando a automação irá operar, este modo permite configurar períodos em que a estratégia não deverá operar. Durante esse intervalo, nenhuma nova ordem será enviada.
Assim como no modo anterior, é possível habilitar a opção Zerar Posição para forçar o encerramento de posições abertas no início do intervalo de suspensão.

Essas configurações permitem maior controle sobre a atuação da estratégia durante o pregão, possibilitando, por exemplo, evitar operações em horários de baixa liquidez ou eventos de maior volatilidade.

11.6 Opções de saída

Nesta outra etapa da configuração, é possível alterar configurações de saída de sua automação.
Aqui é possível configurar uma estratégia OCO que será aberta junto com suas ordens, mas atenção, caso você já tenha ordens de saída implementadas em sua estratégia de negociação (ordens de cobertura), estas não serão mais executadas já que as ordens OCO terão preferência.

### Opções de saída
*Manual NTSL v4.7 (14/10/2026) — p. 46*

Vale ressaltar que todas as ordens são atualizadas simultaneamente. No entanto, a frequência de atualização é definida com base na ordem mais próxima do preço atual.

Existe um intervalo mínimo de atualização de 10 segundos. Assim, as ordens serão enviadas ou alteradas, no máximo, a cada 10 segundos.

O temporizador de envio de ordens só é atualizado quando ocorre alguma modificação. Ou seja, se o código enviar uma ordem diferente das que já estão apregoadas, o sistema irá verificar quando ocorreu a última modificação e determinar o momento da próxima atualização, liberando então novos envios ou alterações.

Assim como no modo de atualização ao fechamento do candle, as ordens de saída sempre serão atualizadas quando houver um aumento de posição, a fim de realizar o rebalanceamento das ordens de cobertura.

Neste modo de execução, as condições para envio de ordens são avaliadas de forma contínua e em tempo real, permitindo que a entrada ocorra imediatamente assim que a condição especificada for satisfeita como, por exemplo, no cruzamento de médias móveis ou no rompimento de um nível de preço pré-definido. Essa abordagem proporciona maior agilidade e precisão na execução, pois as ordens podem ser enviadas no exato momento em que as condições são atendidas.

Lembre-se de que este modo não é compatível com o backtest de estratégias, pois depende de dados em tempo real, o que inviabiliza a previsão precisa do comportamento da automação. Para testar o desempenho de sua estratégia neste modo, é necessário utilizar o recurso de replay de mercado ou realizar os testes diretamente no pregão, utilizando uma conta de simulação.

11.5 Horários de Operação

Nesta seção é possível configurar os períodos em que a estratégia poderá ou não enviar ordens, conforme as opções disponíveis:

• Intervalo de Execução: define o período em que a estratégia estará habilitada para enviar ordens. Após o horário final do intervalo, a estratégia não será pausada, mas deixará de enviar novas ordens automaticamente.
Caso deseje, é possível marcar a opção Zerar Posição para que, ao final do intervalo, todas as posições abertas sejam encerradas automaticamente.

• Intervalo de Suspensão: ao invés de definir quando a automação irá operar, este modo permite configurar períodos em que a estratégia não deverá operar. Durante esse intervalo, nenhuma nova ordem será enviada.
Assim como no modo anterior, é possível habilitar a opção Zerar Posição para forçar o encerramento de posições abertas no início do intervalo de suspensão.

Essas configurações permitem maior controle sobre a atuação da estratégia durante o pregão, possibilitando, por exemplo, evitar operações em horários de baixa liquidez ou eventos de maior volatilidade.

11.6 Opções de saída

Nesta outra etapa da configuração, é possível alterar configurações de saída de sua automação.
Aqui é possível configurar uma estratégia OCO que será aberta junto com suas ordens, mas atenção, caso você já tenha ordens de saída implementadas em sua estratégia de negociação (ordens de cobertura), estas não serão mais executadas já que as ordens OCO terão preferência.

### Risco
*Manual NTSL v4.7 (14/10/2026) — p. 47*

Também é possível configurar nesta seção a zeragem automática por horário. A plataforma precisa estar aberta para que a zeragem aconteça, assim como para que a automação funcione.

11.7 Risco

Seguindo as configurações temos as configurações de risco da automação. Na seção Pausar e Zerar ao Alcançar é possível configurar parâmetros que irão pausar e encerrar as posições abertas de acordo com um objetivo de ganho, ou um limite de perda. Caso você não deseje encerrar a posição quando atingir um objetivo de ganho seleciona a opção "Não Zerar ao Atingir Objetivo de Ganho".

Atualmente, o mecanismo de zeragem do risco funciona por meio do envio de uma ordem a mercado assim que o valor de meta de ganho ou de limite de perda é atingido. Dessa forma, pode existir uma diferença entre o preço identificado no momento do disparo do gatilho e o preço efetivo de execução da ordem de zeragem, permitindo uma margem de resultado positiva ou negativa além do risco configurado.

Já a seção Pausar ao Alcançar possibilita que a automação seja pausada quando alcançados os números de perdas consecutivas e máximo de operações configurados.

Aqui também disponibilizamos um atalho para que você possa configurar o risco global da carteira/conta no gerenci- ador de risco da plataforma.

11.8 Segurança

Por fim, na seção Segurança, temos algumas configurações para definir o comportamento da estratégia em caso ocorra um erro de execução no código da mesma ou eventuais mudanças do mercado, como a entrada do ativo em

### Segurança
*Manual NTSL v4.7 (14/10/2026) — p. 47*

Também é possível configurar nesta seção a zeragem automática por horário. A plataforma precisa estar aberta para que a zeragem aconteça, assim como para que a automação funcione.

11.7 Risco

Seguindo as configurações temos as configurações de risco da automação. Na seção Pausar e Zerar ao Alcançar é possível configurar parâmetros que irão pausar e encerrar as posições abertas de acordo com um objetivo de ganho, ou um limite de perda. Caso você não deseje encerrar a posição quando atingir um objetivo de ganho seleciona a opção "Não Zerar ao Atingir Objetivo de Ganho".

Atualmente, o mecanismo de zeragem do risco funciona por meio do envio de uma ordem a mercado assim que o valor de meta de ganho ou de limite de perda é atingido. Dessa forma, pode existir uma diferença entre o preço identificado no momento do disparo do gatilho e o preço efetivo de execução da ordem de zeragem, permitindo uma margem de resultado positiva ou negativa além do risco configurado.

Já a seção Pausar ao Alcançar possibilita que a automação seja pausada quando alcançados os números de perdas consecutivas e máximo de operações configurados.

Aqui também disponibilizamos um atalho para que você possa configurar o risco global da carteira/conta no gerenci- ador de risco da plataforma.

11.8 Segurança

Por fim, na seção Segurança, temos algumas configurações para definir o comportamento da estratégia em caso ocorra um erro de execução no código da mesma ou eventuais mudanças do mercado, como a entrada do ativo em

### Acompanhamento
*Manual NTSL v4.7 (14/10/2026) — p. 48*

leilão.

Uma vez criada a automação, você pode visualizá-la na janela Automação de Estratégias:

11.9 Acompanhamento

Para acompanhar a sua automação você pode visualizar um resumo rápido das principais informações na lista de automações da janela Automação de Estratégias. Nela você pode visualizar o status, conta e carteira em que a automação está vinculada, ativo, nome da estratégia, período gráfico e os resultados relacionados à execução.
Você também pode visualizar nesta janela um resumo das estatísticas relacionadas a essa estratégia que contém mais detalhes da estratégia:

Para ligar/pausar uma automação de maneira individual pode-se utilizar o painel, e clicar em executar:

Através do menu de contexto também é possível zerar a posição de uma estratégia pausada ou Pausar + Zerar Posição de uma estratégia em execução. Podemos também editar o código da automação no Editor de Estratégias, Excluir a automação que irá excluir também a carteira atrelada a ela. Para realizar edições na sua automação, você pode, dentro do interface de controle, clicar com botão direito na estratégia desejada e ir em "Editar Automação" ou clicar diretamente na engrenagem. Lembrando que caso a sua automação esteja ligada, ao realizar alguma edição ela será pausada.

Para acompanhar os detalhes do que a execução está executando, vá em Detalhes da Automação. Nesta janela você poderá acompanhar tanto as ordens e sinais que a estratégia está gerando, como também acompanhar a performance e resultados da estratégia mais detalhadamente.

Na janela de Automações é possível utilizar os botões no canto superior direito da interface de controle para pausar todas as automações em execução ou para pausar e zerar todas as posições em aberto:

### Raio-X
*Manual NTSL v4.7 (14/10/2026) — p. 51*

Caso você possua alguma automação ligada será possível identificar mesmo com a janela de estratégias automatizadas fechadas, pois no menu superior da sua Plataforma será destacado em azul o menu de Estratégias.

Neste menu você será informado quantas estratégias você possui em execução e permitirá que você tome ações rápidas através do menu como pausar tudo ou pausar e zerar tudo.

11.10 Raio-X

_dos principais recursos introduzidos na Automação 2.0. Ela foi desenvolvida para proporcionar maior visibilidade e controle sobre as condições e variáveis envolvidas na execução de estratégias automatizadas.

Objetivo

A função XRay permite:

• Acompanhar o estado das condições utilizadas na lógica da estratégia.

• Visualizar os valores atuais das variáveis envolvidas na tomada de decisão.

• Agrupar visualmente as condições no Gerenciador de Automações, utilizando cores e nomes distintos para

facilitar a leitura (ex: amarelo para compra, verde para venda).

Para que as informações apareçam corretamente no Gerenciador de Automações, é necessário inserir a função XRay no código da estratégia. A chamada da função deve indicar o nome da condição, seu valor lógico, o grupo ao qual pertence, o valor associado e a cor correspondente.

Visualização no Gerenciador de Automações

Ao executar uma automação com a função XRay no código, o botão Raio-X ficará disponível no Gerenciador de
Automações. Através dele, é possível:

• Verificar quais condições foram satisfeitas durante a execução.

• Observar os valores das variáveis associadas a cada condição.

• Distinguir entre diferentes grupos de condições (como compra e venda) por meio de cores e identificadores._

### Regras de Execução
*Manual NTSL v4.7 (14/10/2026) — p. 53*

Diferenciais do recurso

• Facilita o entendimento do comportamento da automação durante a execução.

• Permite identificar rapidamente falhas lógicas ou inconsistências nas condições.

• Atua como uma ferramenta de depuração visual para aprimoramento das estratégias.

Para mais informações sobre a função XRay, consulte a seção 15.37 - Função XRay no capítulo Funções de
Backtesting.

11.11 Regras de Execução

As automações de estratégias funcionam com as mesmas regras que são utilizadas no backtest das estratégias de execução. Para entender melhor o que cada função faz relacionada à execução de ordens, recomendamos primeira- mente a leitura da seção 15 - Funções de Backtesting. Aqui detalhamos as regras por trás dos mecanismos de automação para facilitar o entendimento do usuário na hora de implementar uma estratégia de execução já pensando na sua automação.

Reprocessamento do candle em aumentos de posição

Caso houver execução de alguma ordem (aumento de posição), o código é reprocessado para a criação de eventuais ordens de cobertura da operação (ordens ToCover). A reexecução da estratégia para posicionamento de ordens de cobertura acontece quando ordens forem executadas, ou seja, podem ocorrer no meio de um candle para não deixar o usuário exposto a riscos do mercado. Nesse reprocessamento, por mais que o código faça a chamada de ordens que poderiam aumentar a exposição, essas ordens não são enviadas. Mais detalhes sobre ordens de cobertura podem ser vistos a seguir.

Ordens para aumento de posição (Buy e Sell)

É possível enviar ordens Buy e Sell tanto quando você estiver comprado ou vendido, porém quando uma ordem
Buy for enviada enquanto você estiver em uma posição vendida, ela será tratada como uma ordem de cobertura automaticamente. O mesmo acontece para uma ordem Sell, quando você estiver uma posição comprada, ela será tratada como uma ordem de cobertura. Caso contrário, elas apenas aumentaram a sua posição até o limite definido na configuração da estratégia.
Ordens conflitantes são automaticamente gerenciadas pelo automatizador, ou seja, quando for enviada uma ordem
BuyToCover e você estiver em uma posição comprada ou zerada, ela será ignorada, da mesma maneira se for enviada uma ordem SellToCover e você estiver em uma posição vendida ou zerada, ela também será ignorada.

Ordens de cobertura de posição (BuyToCover e SellToCover)

Ordens de cobertura, ou ordens ToCover, nunca irão inverter a sua posição; elas garantem que a ordem contrária vai respeitar sempre a posição da operação. Recomendamos que o programador utilize sempre ordens de saída de posição como ordens ToCover explicitamente no código para garantir que o operacional que o usuário está programando está correto. Para isso, as ordens ToCover são sempre enviadas como ordens OCO, logo você não precisa se preocupar em gerenciar e cancelar eventuais ordens de cobertura que poderiam ficar abertas após a execução de apenas uma das pernas de saída.
Ordens de cobertura são enviadas ou atualizadas a toda mudança de candle, cabe ao usuário gerenciar a quantidade de cada ordem caso você esteja posicionado em mais de um lote para cobrir corretamente a exposição ao mercado. Na finalização do candle, caso o código indique um envio de um mesmo número de ordens de cobertura, será realizada uma edição da OCO para os novos valores de preço correspondentes. Por outro lado, caso o envio aumente ou diminua o número de ordens para aquele candle, a OCO aberta será cancelada, e será enviada uma nova OCO com as saídas definidas pelo código.

Ordens OCO

Caso o usuário configure uma ordem OCO pela configuração da automação, as ordens de cobertura definidas pela estratégia serão desconsideradas, já que todas ordens já vão possuir essa cobertura natural da ordem OCO.

### Utilização da Função ConsoleLog na Automação
*Manual NTSL v4.7 (14/10/2026) — p. 54*

Indicadores que atualizam valores anteriores

Se forem utilizados indicadores que alterem seus valores em candles antigos (candles já finalizados), o valor do indicador que será considerado será o do momento em que o candle finalizar, desse modo caso não houver a entrada da execução na virada do candle, não será feito envio de ordens para aquele candle no futuro, mesmo que algum indicador altere seu valor no passado e troque a decisão de envio de ordem. Alguns exemplos de indicadores que podem causar esse comportamento são indicadores que tem apenas um valor durante todo dia, por exemplo: Preço
Ask e Bid e também indicadores que decidem apenas depois de alguns candles, como por exemplo o Detector de topos e fundos ou a linha Chikou Span (2) do indicador IchimokuCloud, entre outros.

Cálculo Automático do Preço Limite (a partir do Preço Stop)

A NTSL possui suporte para o cálculo automático do preço limite em ordens do tipo Stop, quando esse valor não é explicitamente definido no código. Esse mecanismo garante que as ordens sejam enviadas com parâmetros válidos e aceitos pela bolsa ou corretora, prevenindo rejeições por ultrapassarem as bandas de preço permitidas.
Esse processo define a diferença máxima entre o preço stop e o preço limite, com base nas características do ativo e nas regras do ambiente de negociação. As regras aplicadas são as seguintes:

• Ativos com valor mínimo de tick configurado (variação mínima permitida entre ofertas):

– Criptomoedas: diferença igual a 1 tick.

– Contratos ISDI1 (ex.: swaps, compromissadas de índice): diferença igual a 7 ticks.

– Opções: diferença igual a 20 ticks.

– Contratos futuros da BMF:

* Criptoativos: diferença igual a 100 ticks.
* Demais contratos futuros da BMF: diferença igual a 30 ticks.

• Ações negociadas na B3 (mercado Bovespa): limite de 15% sobre o preço de referência, respeitando

a margem operacional dentro do limite de 20% estabelecido pela bolsa.

• Ativos operados por integração externa: limite de 1% sobre o preço.

• Demais ativos não contemplados pelas regras anteriores: limite de 5% sobre o preço.

Caso o ativo não possua tick mínimo configurado (ou seja, o valor seja igual a zero), será aplicado automatica- mente um valor padrão de 1% sobre o preço de referência como fallback de segurança.

Esse comportamento assegura que, mesmo na ausência de um valor de limite explicitamente definido na ordem, o sistema utilizará parâmetros compatíveis com os requisitos operacionais do mercado, garantindo o envio bem-sucedido da ordem.

11.12 Utilização da Função ConsoleLog na Automação

A função ConsoleLog pode ser utilizada dentro das automações em NTSL para registrar eventos em tempo real diretamente nos eventos da automação.
Essa funcionalidade é especialmente útil para depuração de estratégias, acompanhamento de variáveis internas e verificação de condições durante a execução.

Como funciona

• As mensagens registradas por ConsoleLog ficam visíveis na janela de Detalhes da Automação.

• O comportamento da emissão dos logs varia conforme o modo de execução da automação:

– Modo Candle a Candle: os logs são enviados a cada novo candle e a cada reavaliação de candle.

– Modo Ao Satisfazer Condição: os logs são enviados a cada 5 segundos ou a cada reavaliação de

candle por mudança de posição.

**Exemplo de uso:** No exemplo acima, sempre que ocorrer um cruzamento entre as médias móveis, a automação registrará um log informativo na janela de Detalhes da Automação, permitindo acompanhar em tempo real os eventos da es- tratégia.

```ntsl
var
sAvgFast ,sAvgSlow ,sPrevAvgFast ,sPrevAvgSlow : Float;
begin
sAvgFast := Media(9,Close);
sAvgSlow := Media(21,Close);
sPrevAvgFast := sAvgFast[1];
sPrevAvgSlow := sAvgSlow[1];
if (sPrevAvgFast < sPrevAvgSlow) and (sAvgFast > sAvgSlow) then
begin
ConsoleLog("Cruzamento de compra detectado no preço " + sPrevAvgFast);
buyLimit(Close,1);
end
else if (sPrevAvgFast > sPrevAvgSlow) and (sAvgFast < sAvgSlow) then
begin
ConsoleLog("Cruzamento de venda detectado no preço " + sPrevAvgSlow);
SellShortLimit(Close,1);
end;
end;
```

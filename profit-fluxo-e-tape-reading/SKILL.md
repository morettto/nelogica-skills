---
name: profit-fluxo-e-tape-reading
description: Leitura de fluxo no Profit — Livro de Ofertas (modelos preços, profundidade, ofertas, gráfico e netrix), SuperDOM, PriceTrader, Times & Trades com suas nove abas, Mapa de Fluxo, Medidores de Pressão, Volume At Market, Volume At Price, Áreas de Valor, Identificando os Grandes Players, BookMap e o plugin Tape Reading. Use quando a pergunta for sobre tape reading, agressão, delta, liquidez, player grande, livro ou DOM.
---

# Fluxo e tape reading no Profit

Base: seções "Ferramentas de Fluxo", "Ferramentas Gráficas", "BookMap" e "Plugin Tape Reading" da Central de Ajuda Nelogica (textos de 12/11/2026, com data de cada artigo nas refs).

## Livro de Ofertas

O Profit tem vários modelos de livro (preços, profundidade, ofertas, gráfico, netrix), e é dentro do livro que ficam SuperDOM e PriceTrader, em abas na parte inferior. Preço, quantidade e cor mudam em Propriedades do Livro, aba Execução.

## As ferramentas e o que cada uma mede de fato

- **SuperDOM** — negociação pelo livro, com ordens padronizadas via tecnologia **AutoOp**; painel de negociação e barra de Descrição são habilitados com o botão direito sobre a ferramenta.
- **PriceTrader** — negociação por fila de preço: clica no nível e a ordem vai para a fila, com leitura de fluxo na mesma tela (aba inferior do livro).
- **Times & Trades** — histórico de negócios com nove abas: Negócios, Ordem Original, Compradores, Vendedores, Saldo, Evolução no Tempo, Evolução do Player, Análise do Player (mais configuração, colunas de Tape Reading e coloração por ranking de tape reading). É a ferramenta de tape reading mais completa da plataforma.
- **Mapa de Fluxo** — une gráfico e fluxo: linhas acima do centro = volume de ofertas de venda por faixa, abaixo = compra, quanto mais claras maior o volume; círculos verdes e vermelhos = agressões.
- **Medidores de Pressão** — compara três coisas entre compra e venda: **Quantidade** (profundidade, soma dos contratos ofertados), **Oferta** (número de ordens no livro) e **Agressão** (volume executado a mercado). As duas primeiras são intenção, a terceira é execução — ensine sempre essa distinção.
- **Volume At Market** — regiões de defesa de preço dos grandes players; colunas de Preço, Ofertas/Delta (delta = diferença entre negócios de compra e de venda no nível) e volume.
- **Volume At Price / Áreas de Valor** — volume por preço e por período, para achar área de valor e aceitação/rejeição de preço.
- **Identificando os Grandes Players** — menu Ferramentas › Players; abas Negócios e Posição, com filtros por mercado (Bovespa/BMF), ativo e lado.
- **BookMap** (módulo à parte) e **plugin Tape Reading** — refs próprias; são pagos, não vêm em toda versão.

## Regra de ouro para responder

Fluxo no Profit é sempre um de três: **intenção** (o que está no livro), **execução** (o que foi agredido) e **histórico** (quem comprou/vendeu e quando). Se a pergunta for "a pressão vai continuar?", a resposta honesta é: o livro mostra intenção e pode ser cancelado; só a agressão confirma. Use Medidores de Pressão para ver os dois lado a lado e Times & Trades para o detalhe por negócio.

## Pegadinhas

- Delta não é saldo de contratos do dia do usuário; é diferença entre negócios de compra e de venda no nível/período exibido.
- Times & Trades depende do feed de negócios do ativo; em ativo com pouca liquidez as abas de player ficam vazias e isso não é defeito.
- Coloração por ranking de tape reading é configuração, não indicador: se as cores não aparecem, é coluna/ranking desligado.

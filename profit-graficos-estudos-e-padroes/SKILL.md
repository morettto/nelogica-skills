---
name: profit-graficos-estudos-e-padroes
description: O gráfico do Profit — tipos e períodos de gráfico, agrupamento de ativos, múltiplos períodos, modelos de estudo e templates, ferramentas gráficas de desenho, padrões gráficos automáticos, Renko (incluindo plugin SomosRenko), indicadores da plataforma (lista completa e o que cada um mede), escala, cores, temas, sincronização de janelas, workspaces e backup de configurações. Use quando a pergunta for sobre montar gráfico, estudo, desenho ou indicador na plataforma.
---

# Gráfico, estudos e padrões no Profit

Base: seções "Ferramentas Gráficas" (18), "Estudos" (28), "Padrões Gráficos" (12) e "Indicadores" (89) da Central de Ajuda Nelogica, baixadas em 12/11/2026. As refs têm um verbete por indicador/ferramenta, com URL e data.

## Estrutura do gráfico

- O gráfico do Profit é uma janela com ativo, período e tipo de gráfico (candle, barra, linha, Renko etc.). Análise de um ativo em vários tempos ao mesmo tempo se faz com **Múltiplos Períodos** ou com janelas sincronizadas.
- **Agrupamento** (de ativos) repete o mesmo estudo em vários gráficos de uma vez; mudar período/indicador em um reflete nos demais.
- **Modelos de estudo** salvam o conjunto de indicadores + desenhos e podem ser exportados/importados — é assim que se leva o setup de uma máquina para outra.
- **Workspaces**: conjunto de janelas salvo e recarregado; junto com exportação/importação de configurações, é o backup do ambiente.

## Ferramentas gráficas (desenho)

Linhas de tendência, canais, Fibonacci, retângulos, textos, setas, marca d'água, escalas (linear/log), cores e espessuras, travar/desbloquear desenhos, apagar todos os estudos, salvar desenho como modelo. Detalhe por ferramenta nas refs.

## Padrões gráficos

O Profit tem biblioteca de padrões gráficos automáticos (ombro-cabeça-ombro, triângulos, cunhas, topos e fundos, bandeiras etc.) que marca no gráfico quando detectado. É recurso da plataforma, não código NTSL — na dúvida, o artigo de padrão específico está na ref.

## Indicadores da plataforma

São ~89 artigos de indicadores na Central de Ajuda (médias móveis, MACD, ADX, IFR, Bollinger, VWAP, OBV, Dinâmica, fluxo de agressão, market profile, indicadores de plugins como 2MV, Phicube, EduIndex, AMZ 2000, FGZ, Rafa Ansani, Opp Joy, PNB). Dois mundos diferentes, nunca misture:

- **Indicador da plataforma**: você insere pela janela de estudos; tem artigo na Central de Ajuda.
- **Função NTSL**: você chama no código da estratégia (`BollingerBands(...)`, `AvgTrueRange(...)`); tem assinatura no Manual NTSL v4.7 e vive nas skills `ntsl-*`.

## Pegadinhas

- "Não aparece o indicador X" costuma ser versão da plataforma ou módulo/plugin não contratado, não erro do gráfico.
- Histórico curto de candles/backtest se resolve nas configurações de séries históricas, não reinstalando a plataforma.
- Indicador que multiplica candles (Renko, point & figure) muda a série: volume e média calculados sobre ela não são iguais aos do candle de tempo.

## Arquivos de referência

- `refs/01-indicadores.md` — profit-graficos-estudos-e-padroes — Indicadores (89 verbetes)
- `refs/02-estudos.md` — profit-graficos-estudos-e-padroes — Estudos (27 verbetes)
- `refs/03-duvidas-comuns.md` — profit-graficos-estudos-e-padroes — Dúvidas Comuns (22 verbetes)
- `refs/04-ferramentas-graficas.md` — profit-graficos-estudos-e-padroes — Ferramentas Gráficas (18 verbetes)
- `refs/05-padroes-graficos.md` — profit-graficos-estudos-e-padroes — Padrões Gráficos (12 verbetes)

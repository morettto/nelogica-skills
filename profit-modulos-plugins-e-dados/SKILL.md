---
name: profit-modulos-plugins-e-dados
description: O que é módulo pago, plugin e fonte de dados no Profit — Módulo de Opções (grade, boleta de rolagem, gregas, acompanhamento), Módulo NQuant, BookMap, Módulos CME, DJI e US Equities, plugins (Plano de Trade, Tape Reading, SomosRenko, Tradencia, Toscana, PNB, Long & Short, 2MV, AMZ 2000, Phicube, EduIndex, FGZ, Rafa Ansani, Opp Joy), ProfitDLL e DataFeed, RTD/DDE com Excel, notícias, custos operacionais e calculadora de IR. Use quando a pergunta for "isso é módulo?", "como ligo o Profit no Excel?", "como pego dados via API?".
---

# Módulos, plugins e dados do Profit

Base: seções "Módulos Opcionais", "Módulo de Opções", "Módulo NQuant", "BookMap", "Módulo CME", "Módulo DJI", "Módulo US Equities", "Plugin *", "DataFeed - DLL" e os artigos de RTD/DDE da Central de Ajuda Nelogica (12/11/2026). Uma ref por módulo/plugin, com URL e data.

## Módulo x plugin x versão

- **Versão** é o Profit em si (One, Plus, Pro, Ultra, Training).
- **Módulo** é um pacote funcional contratado à parte na Profit Store (Automação de Estratégias para conta real, Módulo de Opções, NQuant, BookMap, CME, DJI, US Equities, AI Code Builder).
- **Plugin** é uma ferramenta de terceiro ou parceiro embutida na plataforma (SomosRenko, Tradencia, Toscana, PNB, Long & Short, 2MV, AMZ 2000, Phicube, EduIndex, FGZ, Rafa Ansani, Opp Joy, Plano de Trade).

Diagnóstico padrão de "não encontro a ferramenta": primeiro versão, depois módulo/plugin, só por último suporte.

## Módulo de Opções

Traz grade de opções, boleta do módulo, boleta de rolagem de contratos e tela de Acompanhamento com status das estratégias e configurações. As gregas e funções de opções em código estão na skill `ntsl-livro-e-opcoes`.

## Módulo NQuant

Desenvolvido em conjunto com a **NCH** (gestora americana): analisa ativos com dados fundamentalistas e técnicos. Contratação própria, fora do plano da plataforma.

## Módulos internacionais

- **CME**: libera mini S&P 500 e demais contratos da bolsa americana; adesão à parte (contato pelo relacionamento Nelogica).
- **DJI** e **US Equities**: pacotes separados para índice Dow Jones e ações americanas.
Regra: sem o módulo, o ativo não aparece para operar, mesmo com a plataforma em tempo real na B3.

## Dados e integrações

- **ProfitDLL (DataFeed)**: integra aplicações externas ao Profit, com dados de mercado e funcionalidades da plataforma via desenvolvimento próprio; o acesso é pedido à Nelogica (Data Solution) e tem regras comerciais. Existe material de primeiros passos, cotação, trades históricos e roteamento de ordens.
- **RTD/DDE**: leva cotação do Profit para o Excel e recebe de volta; a sintaxe do RTD (`=RTD(...)`) tem artigo próprio com nome de campo, ativo e parâmetros — é a integração mais comum para planilha.
- **Notícias**: feed de notícias na plataforma, BM&C News, Play Now e TraderVoice; alarme de notícia no Gerenciador de Alarmes.
- **Custos operacionais** e **calculadora de IR (Akeloo)**: artigos próprios, útil para responder "quanto sobra do trade".

## Pegadinhas

- RTD/DDE não é API de ordem: para enviar ordem por fora é ProfitDLL (com as permissões da conta), não Excel.
- Módulo contratado mas não ativo normalmente é licença no usuário certo (mesma conta Nelogica) ou versão da plataforma desatualizada.
- Plugin de terceiro segue o fornecedor para suporte de conteúdo; a Nelogica documenta a instalação e a contratação.

## Arquivos de referência

- `refs/01-modulo-de-opcoes.md` — profit-modulos-plugins-e-dados — Módulo de Opções (19 verbetes)
- `refs/02-datafeed-dll.md` — profit-modulos-plugins-e-dados — DataFeed - DLL (17 verbetes)
- `refs/03-plugin-tradencia.md` — profit-modulos-plugins-e-dados — Plugin Tradencia (7 verbetes)
- `refs/04-plugin-long-short.md` — profit-modulos-plugins-e-dados — Plugin Long & Short (6 verbetes)
- `refs/05-modulo-us-equities.md` — profit-modulos-plugins-e-dados — Módulo US Equities (5 verbetes)
- `refs/06-indicador-pnb-poe-no-bolso.md` — profit-modulos-plugins-e-dados — Indicador PNB (Põe no Bolso) (4 verbetes)
- `refs/07-modulo-nquant.md` — profit-modulos-plugins-e-dados — Módulo NQuant (4 verbetes)
- `refs/08-modulos-opcionais.md` — profit-modulos-plugins-e-dados — Módulos Opcionais (3 verbetes)
- `refs/09-plugin-somosrenko.md` — profit-modulos-plugins-e-dados — Plugin SomosRenko (3 verbetes)
- `refs/10-duvidas-comuns.md` — profit-modulos-plugins-e-dados — Dúvidas Comuns (2 verbetes)
- `refs/11-indicador-fgz.md` — profit-modulos-plugins-e-dados — Indicador FGZ (2 verbetes)
- `refs/12-indicador-opp-joy.md` — profit-modulos-plugins-e-dados — Indicador Opp Joy (2 verbetes)
- `refs/13-indicador-rafa-ansani.md` — profit-modulos-plugins-e-dados — Indicador Rafa Ansani (2 verbetes)
- `refs/14-indicadores-2mv.md` — profit-modulos-plugins-e-dados — Indicadores 2MV (2 verbetes)
- `refs/15-indicadores-amz-2000.md` — profit-modulos-plugins-e-dados — Indicadores AMZ 2000 (2 verbetes)
- `refs/16-indicadores-eduindex.md` — profit-modulos-plugins-e-dados — Indicadores EduIndex (2 verbetes)
- `refs/17-indicadores-phicube.md` — profit-modulos-plugins-e-dados — Indicadores Phicube (2 verbetes)
- `refs/18-modulo-cme.md` — profit-modulos-plugins-e-dados — Módulo CME (2 verbetes)
- `refs/19-modulo-dji.md` — profit-modulos-plugins-e-dados — Módulo DJI (2 verbetes)
- `refs/20-plugin-toscana.md` — profit-modulos-plugins-e-dados — Plugin Toscana (2 verbetes)
- `refs/21-sinais-internacionais.md` — profit-modulos-plugins-e-dados — Sinais Internacionais (1 verbetes)

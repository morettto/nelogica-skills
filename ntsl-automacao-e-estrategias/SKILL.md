---
name: ntsl-automacao-e-estrategias
description: Como se cria, testa e coloca no ar uma estratégia no Profit Pro — backtest OHLC e tick a tick, backtest em gráfico atemporal, Automação de Estratégias (opções de entrada e saída, horários, risco, segurança, acompanhamento, raio-X, regras de execução), Central de Estratégias, Screening com Select, Block Builder e ConsoleLog. Use quando a pergunta for "como automatizo", "por que a automação não entrou", "qual a diferença de OHLC e tick a tick", ou sobre o fluxo operacional da estratégia.
---

# Automação de estratégias no Profit Pro

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulos 10 a 13 e 24. Conteúdo verbatim em `refs/01-automacao.md` e `refs/02-estrategias-e-screening.md`.

## O que é o quê (não confunda)

- **Estratégia** é o código NTSL (o que compra e vende).
- **Automação** é a configuração de execução dessa estratégia: quando entra, quando sai, horário, risco, tamanho, segurança. Não se escreve no NTSL.
- **Backtest** é o teste sobre histórico; **automação** é o mesmo código rodando ao vivo. O manual trata os dois em capítulos separados justamente porque a maior parte dos problemas de "não entrou" é configuração, não código.
- **Screening** filtra ativos por regra; **Block Builder** monta estratégia sem escrever código.

## Regras que não se negociam

1. **Backtest OHLC ≠ tick a tick.** O resultado muda porque a ordem de toque em alta/baixa dentro da barra é suposta no OHLC e real no tick a tick. Nunca apresente resultado de backtest OHLC como se fosse execução real.
2. **Gráfico atemporal** tem regra própria de backtest — não é o mesmo motor do gráfico por tempo.
3. **Horário de operação, risco e segurança são configuração da automação**, não `if` no código. Estratégia que "só opera até 17h" com `if` no NTSL é frágil: a automação já tem esse campo.
4. **ConsoleLog é o depurador oficial.** O manual tem tópico próprio de uso do ConsoleLog na automação — use isso em vez de `Plot` para depurar.
5. **`Select()` é ressalva do manual**: a função existe na linguagem, não tem parâmetros, mas o próprio manual diz que ela "não possui recursos para utilização do usuário" — a implementação é do sistema, para habilitar o Screening. Ou seja: **não se escreve `Select` em estratégia de usuário**. Se alguém pedir isso, corrija: o filtro é na tela de Screening.
6. **Central de Estratégias** é onde ficam as estratégias (criar, exportar, importar). Estratégia não salva não roda.
7. **Raio-X e acompanhamento** são as telas de diagnóstico da execução: antes de dizer que "a plataforma não enviou", olhe o raio-X da ordem.

## Assinaturas conferidas

```ntsl
Função Select(): Void;
Função ConsoleLog(Content: String; Color: Integer): Void;
Função AutomationResult(OpenResult: Boolean): Float;
Função PlotText(Content: String Color: Integer Position: Integer FontSize: Integer
Função PaintBar(Cor: Integer): Void;
Função Alert(Color: Integer): Void;
```

## O que está coberto

- Backtesting (2): Modo de Execução do Backtest: OHLC e Tick a Tick, Backtest em Gráficos Atemporais
- Automação de Estratégias (12): Criando uma estratégia de execução, Criando uma automação, Opções de entrada, Modo de Execução, Horários de Operação, Opções de saída, Risco, Segurança, Acompanhamento, Raio-X, Regras de Execução, Utilização da Função ConsoleLog na Automação
- Estratégias (9): Abrir Estratégias, Central de Estratégias, Exportar / Importar Estratégias, Screening, Inserir Regra de Coloração, Editor de Estratégias, Propriedades do Editor de Estratégias, Nova Estratégia, Termômetro de Estratégia
- Block Builder (4): Tipos de Estratégias Suportadas, Criando uma Estratégia, Aplicando a Estratégia no Gráfico, Exemplo Prático
- Screening (1): Select

## Referências

- `refs/01-automacao.md` — backtesting e todo o fluxo da automação (13 seções, p. 38 a 68)
- `refs/02-estrategias-e-screening.md` — Central/Editor de Estratégias, Block Builder, Screening e `Select` (p. 56 e 541)

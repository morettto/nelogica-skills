---
name: ntsl-fundamentos
description: Fundamentos da linguagem NTSL do Profit — as três áreas do código, fluxo de execução barra a barra, tipos de dados, séries e séries históricas, arrays, correlação de múltiplos ativos, controle de fluxo, operadores, funções e procedimentos do usuário, Initialization e as armadilhas de compilação. Use ao escrever, revisar ou explicar qualquer código NTSL.
---

# NTSL — fundamentos que decidem se o código compila e se ele faz o que você acha

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulos 1 a 12 e 28 (páginas 11 a 57 e 574). Conteúdo verbatim em `refs/`.

## As três áreas de uma estratégia

O Editor de Estratégias tem três áreas, nesta ordem, e a ordem importa:

1. **Área de declaração de parâmetros de entrada** — vira campo de configuração na tela da estratégia.
2. **Área de declaração de variáveis e funções** — variáveis primeiro, depois as funções/procedimentos do usuário.
3. **Área de código** — `begin ... end`, o que roda a cada barra. `Initialization` roda uma vez, antes do laço de barras.

Página 11-12 do manual (`refs/01-estrutura-e-fluxo.md`).

## Regras que não se negociam

1. **Função do usuário não enxerga variável global.** Precisa receber tudo por parâmetro. Tentar ler uma global dentro de uma função gera erro de compilação — é a causa nº 1 de "meu código não compila".
2. **Nunca compare `Float` com `=`.** Use `CompareFloat(a, b, casas) = 0`. O manual traz o exemplo: `if (CompareFloat(BuyPrice, Close + 10, 2) = 0) then`. Página 574.
3. **Código roda barra a barra, do começo ao fim, sem voltar.** Não existe estado entre barras fora de variáveis — para ler o passado use série (`Close[1]`, `Close[2]`).
4. **Ordens do mesmo fluxo de execução interagem entre si** (ver `ntsl-backtesting-e-ordens`): a linha de baixo pode cancelar a de cima.
5. **Não invente função, tipo ou constante.** Se não está nas referências, diga que não achou no manual em vez de completar por analogia com outras linguagens.
6. NTSL **não é Pascal puro nem C**: a sintaxe lembra Pascal (`begin/end`, `:=`), mas as regras de execução são as do motor do Profit. Não transporte construções de fora.

## Tipos, séries e arrays

- Tipos: `Float`/`Real`, `Integer`/`Inteiro`, `Boolean`/`Booleano`, `String`, além de tipos próprios da plataforma como `Ativo`. Detalhe e exemplos em `refs/02-variaveis-tipos-series.md` (p. 15 em diante).
- **Séries de dados**: o histórico de uma expressão (`Close`, `Volume`, o retorno de um indicador) indexado para trás com `[n]`. É o mecanismo de memória da linguagem.
- **Arrays**: coleções com índice, declare o tamanho; não confunda array com série.
- **Correlação de múltiplos ativos**: o manual mostra como referenciar o dado de outro ativo dentro da mesma estratégia — é o que permite operar WIN olhando o Dólar, por exemplo.

## Controle de fluxo e operadores (p. 28 a 33)

`For ... To/DownTo ... Do`, `If ... Then ... Else`, `Repeat ... Until`, `While ... Do`; operadores matemáticos, de comparação e lógicos. Cuidado com a precedência e com curto-circuito: escreva parênteses explícitos.

## Funções e procedimentos do usuário (p. 33 a 35)

Sintaxe na área de declaração, com tipo de retorno declarado. `Initialization` para o que precisa rodar uma única vez. Modelo e exemplos em `refs/04-funcoes-e-procedimentos.md`.

## Armadilhas documentadas pelo próprio manual (p. 574)

O capítulo 28 é uma lista de erros reais observados no uso da linguagem, cada um com o código errado e a correção. É a primeira coisa a conferir quando uma estratégia "compila mas não opera". Ver `refs/05-anexos-erros-comuns.md`.

## Como responder

Ao explicar NTSL, mostre o código compilável na ordem correta (parâmetros → variáveis/funções → `begin/end`), diga a página do manual e aponte a armadilha relevante. Se a dúvida for de indicador, mande para a skill `ntsl-indicadores`; se for de ordem/posição, para `ntsl-backtesting-e-ordens`.

## Referências

- `refs/01-estrutura-e-fluxo.md` — estrutura, áreas, fluxo de execução
- `refs/02-variaveis-tipos-series.md` — tipos, séries, arrays, multiativo, constantes
- `refs/03-controle-de-fluxo-e-operadores.md` — laços, condicionais, operadores
- `refs/04-funcoes-e-procedimentos.md` — funções do usuário, Initialization
- `refs/05-anexos-erros-comuns.md` — erros documentados e boas práticas

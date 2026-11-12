---
name: ntsl-matematica-e-series
description: Funções matemáticas e utilitárias do NTSL — ABS, Round, Power, Sqrt, Max/Min, Random, FastK/FastD/SlowK, ExtremePriceRatio, Volatility, PercentR, comparação segura de Float (CompareFloat), conversão de número/texto (FloatToString, BoolToString) e funções de texto (SubString, StringContains, StringPos). Use em cálculo dentro de estratégia, arredondamento, comparação de float, montagem de texto e operações matemáticas em série.
---

# Matemática, utilitários e texto no NTSL

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulos 22 (Matemáticas, p. 486), 25 (Usuário, p. 542), 26 (Utils, p. 564) e 27 (String, p. 568).

## Regras que não se negociam

1. **Nunca compare Float com `=` ou `<>`.** Use `CompareFloat(a, b, casas) = 0`. Igualdade exata de ponto flutuante é o erro número um em NTSL.
2. **`Round2Fraction(Valor)` arredonda para o múltiplo do incremento mínimo do ativo** (31.626 → 31.63 em Bovespa). Para preço use essa, não `Round`, que só devolve inteiro.
3. **`FloatToString`/`BoolToString` existem** para compor texto; não concatene número com string.
4. **Funções de texto trabalham com índice começando em 0** e índice final exclusivo (`SubString(texto, 0, 4)` devolve 4 caracteres).
5. **`Random(Limite)` devolve inteiro de 0 até `Limite`** — não é uniforme em preço nem tem semente documentada; não use para simular execução.
6. **Função de usuário não enxerga variável global.** Passe tudo por parâmetro; retorno tem tipo declarado.

## Assinaturas conferidas

```ntsl
Função ABS(Valor: Float): Float;
Função Round(Valor: Float): Integer;
Função Round2Fraction(Valor: Float): Float;
Função Power(Valor: Float; Potência: Integer): Float;
Função Sqrt(Valor: Float): Float;
Função Max(Valor1: Float; Valor2: Float): Float;
Função Min(Valor1: Float; Valor2: Float): Float;
Função BoolToString(Content: Boolean): String;
Função FloatToString(Valor: Float; Dígitos: Integer): String;
Função BoolToString(Content: Boolean): String;
Função SubString(Text: String; BeginIndex: Integer; EndIndex: Integer): String;
Função StringContains(Text: String; SubText: String): Boolean;
Função StringPos(Text: String; SubText: String): Integer;
Função StringStartsWith(Text: String; Prefix: String): Boolean;
Função FastK(StochLength: Integer): Float;
Função FastD(StochLength: Integer): Float;
Função SlowK(StochLength: Integer): Float;
Função PercentR(Length: Integer): Float;
Função Volatility(Period: Integer): Float;
Função ExtremePriceRatio(Length: Integer; UseLog: Boolean): Float;
```

## Funções cobertas

- Matemáticas (44): ABS, Arctangent, Ceiling, Combination, Cos, Cosine, Cotangent, Exp, ExpValue, ExtremePriceRatio, Factorial, FastD, FastK, Floor, FracPortion, GCD, IntPortion, Log, LogN, Max, Min, MinutesToTime, Mod, Neg, NumUnits, PercentR, Permutation, Pos, Power, PowerF, Random, Round, Round2Fraction, Sign, Sin, Sine, SlowK, Sqrt, Square, Tangent, UltimateOscillator, Volatility, VolumeOsc, VolumeROC
- Usuário (21): Cum, FastKCustom, HarmonicMean, Highest, HighestBar, Lowest, LowestBar, Media, MediaExp, MidPoint, PercentChange, PriceOscillator, RateOfChange, SlowD, StdDevs, Summation, TriAverage, UlcerIndex, WAverage, WellesSum, xAverage
- Utils (4): AssetHasValue, BoolToString, CompareFloat, FloatToString
- String (6): SubString, StringCopy, StringStartsWith, StringEndsWith, StringPos, StringContains

## Referências

- `refs/01-matematicas.md`, `refs/02-funcoes-de-usuario.md`, `refs/03-utils-e-string.md`

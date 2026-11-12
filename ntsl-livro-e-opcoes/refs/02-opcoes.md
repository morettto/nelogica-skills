# 02 Opcoes

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Opções

### Funções de Opções
*Manual NTSL v4.7 (14/10/2026) — p. 530*

Funções de Opções

23.1 Função Delta

_A função Delta() mede a variação do preço da opção com o preço da ação._

**Sintaxe**

```ntsl
Função Delta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 13 dias para o vencimento, 16.47 como
Strike, 17.25 como preço da ação, 0.1 para taxa de juros e 0.25 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Delta(13, 16.47, 17.25, 0.1, 0.25, optCall));
end
```

**Gráfico:** ver exemplo no manual, p. 530

_A função Gamma() retorna o valor de Gamma._

**Sintaxe**

```ntsl
Função Gamma(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 9 dias para o vencimento, 11.08 como
Strike, 11.94 como preço da ação, 0.2 para taxa de juros e 0.3 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Gamma(9, 11.08, 11.94, 0.2, 0.3, optCall));
end
```

**Gráfico:** ver exemplo no manual, p. 530

_A função Rho() retorna a variação da opção em relação à taxa de juros._

**Sintaxe**

```ntsl
Função Rho(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float;

Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 60 dias para o vencimento, 11.00 como
Strike, 12.92 como preço da ação, 0.2 para taxa de juros e 0.3 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Rho(60, 11.00, 12.92, 0.2, 0.3, optCall));
end
```

**Gráfico:** ver exemplo no manual, p. 530

_A função Strike() retorna o valor de strike caso o ativo seja uma opção._

**Sintaxe**

```ntsl
Função Strike(Asset : Ativo): Float;
```

**Parâmetros**

Asset: Ativo [Opcional]; Determina o ativo para a função.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor da opção PETRE285W2, onde a constante PETR recebe o nome e bolsa do ativo.
const

```ntsl
PETR = Asset("PETRE285W2", feedBovespa);
begin
Plot(Strike(PETR));
end
```

**Gráfico:** ver exemplo no manual, p. 530

_A função Theta() retorna a variação da opção em relação à taxa de juros._

**Sintaxe**

```ntsl
Função Theta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 9 dias para o vencimento, 17.22 como
Strike, 11.94 como preço da ação, 0.1 para taxa de juros e 0.32 para volatilidade, aplicados para uma Put.

```ntsl
begin
Plot(Theta(9, 17.22, 11.94, 0.1, 0.32, optPut));
end
```

**Gráfico:** ver exemplo no manual, p. 530

_A função Vega() retorna a variação da opção em relação à volatilidade._

**Sintaxe**

```ntsl
Função Vega(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float

; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 28 dias para o vencimento, 11.08 como
Strike, 11.94 como preço da ação, 0.2 para taxa de juros e 0.36 para volatilidade, aplicados para uma Put.

```ntsl
begin
Plot(Vega(28, 11.08, 11.94, 0.2, 0.36, optPut));
end
```

### Função Delta
*Manual NTSL v4.7 (14/10/2026) — p. 530*

23 Funções de Opções

23.1 Função Delta

_A função Delta() mede a variação do preço da opção com o preço da ação._

**Sintaxe**

```ntsl
Função Delta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 13 dias para o vencimento, 16.47 como
Strike, 17.25 como preço da ação, 0.1 para taxa de juros e 0.25 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Delta(13, 16.47, 17.25, 0.1, 0.25, optCall));
end
```

### Função Gamma
*Manual NTSL v4.7 (14/10/2026) — p. 532*

_A função Gamma() retorna o valor de Gamma._

**Sintaxe**

```ntsl
Função Gamma(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 9 dias para o vencimento, 11.08 como
Strike, 11.94 como preço da ação, 0.2 para taxa de juros e 0.3 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Gamma(9, 11.08, 11.94, 0.2, 0.3, optCall));
end
```

### Função Rho
*Manual NTSL v4.7 (14/10/2026) — p. 534*

_A função Rho() retorna a variação da opção em relação à taxa de juros._

**Sintaxe**

```ntsl
Função Rho(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float;

Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 60 dias para o vencimento, 11.00 como
Strike, 12.92 como preço da ação, 0.2 para taxa de juros e 0.3 para volatilidade, aplicados para uma Call.

```ntsl
begin
Plot(Rho(60, 11.00, 12.92, 0.2, 0.3, optCall));
end
```

### Função Strike
*Manual NTSL v4.7 (14/10/2026) — p. 536*

_A função Strike() retorna o valor de strike caso o ativo seja uma opção._

**Sintaxe**

```ntsl
Função Strike(Asset : Ativo): Float;
```

**Parâmetros**

Asset: Ativo [Opcional]; Determina o ativo para a função.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor da opção PETRE285W2, onde a constante PETR recebe o nome e bolsa do ativo.
const

```ntsl
PETR = Asset("PETRE285W2", feedBovespa);
begin
Plot(Strike(PETR));
end
```

### Função Theta
*Manual NTSL v4.7 (14/10/2026) — p. 537*

_A função Theta() retorna a variação da opção em relação à taxa de juros._

**Sintaxe**

```ntsl
Função Theta(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 :

Float; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 9 dias para o vencimento, 17.22 como
Strike, 11.94 como preço da ação, 0.1 para taxa de juros e 0.32 para volatilidade, aplicados para uma Put.

```ntsl
begin
Plot(Theta(9, 17.22, 11.94, 0.1, 0.32, optPut));
end
```

### Função Vega
*Manual NTSL v4.7 (14/10/2026) — p. 539*

_A função Vega() retorna a variação da opção em relação à volatilidade._

**Sintaxe**

```ntsl
Função Vega(DaysLeft : Integer; StrikePr : Float; AssetPr : Float; Rate100 : Float

; Volty100 : Float; PutCall : Integer): Float;
```

**Parâmetros**

DaysLeft: Integer; Dias uteis até o vencimento da opção.

StrikePr: Float; Preço do exercício da opção.

AssetPr: Float; Preço da ação.

Rate100: Float; Taxa de juros em %.

Volty100: Float; Volatilidade em %.

PutCall: Integer; Indica se é uma put ou uma call:

– [optPut:] Opção de venda.

– [optCall:] Opção de compra.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a variação, considerando 28 dias para o vencimento, 11.08 como
Strike, 11.94 como preço da ação, 0.2 para taxa de juros e 0.36 para volatilidade, aplicados para uma Put.

```ntsl
begin
Plot(Vega(28, 11.08, 11.94, 0.2, 0.36, optPut));
end
```

# 03 Exemplos

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Exemplos

### Exemplos
*Manual NTSL v4.7 (14/10/2026) — p. 202*

Exemplos

18.1 Função DiMaisDiMenos

_O indicador "Diferencial(DI+/DI-)" é chamado pela função DiMaisDiMenos(), sendo um indicador de momento, tenta qualificar a tendência ou comportamento direcional de um mercado. O exemplo com o código fonte está_

**Sintaxe**

```ntsl
Função DiMaisDiMenos(Periodo : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o indicador criado.

```ntsl
begin
Plot(DiMaisDiMenos(14));
end;
```

**Gráfico:** ver exemplo no manual, p. 202

_O "Índice de Força Relativo" IFR() mede a evolução da relação de forças entre compradores e vendedores ao longo do tempo. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu:
"abrir > exemplos"._

**Sintaxe**

```ntsl
Função IFR(Periodo : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor do indicador "IFR", considerando 2 períodos para o cálculo.

```ntsl
begin
Plot(IFR(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 202

_A função PaintVar() possui a implementação de uma estratégia de coloração, a qual compara se o fechamento do último candle é positivo ou negativo em relação ao fechamento do (candle) anterior, e, como indicador, apenas retorna o último preço do ativo. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função PaintVar(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado o último preço, onde a regra de coloração correspondente poderá ser aplicada sobre o indicador.

```ntsl
begin
Plot(PaintVar);
end;
```

### Função DiMaisDiMenos
*Manual NTSL v4.7 (14/10/2026) — p. 202*

18 Exemplos

18.1 Função DiMaisDiMenos

_O indicador "Diferencial(DI+/DI-)" é chamado pela função DiMaisDiMenos(), sendo um indicador de momento, tenta qualificar a tendência ou comportamento direcional de um mercado. O exemplo com o código fonte está_

**Sintaxe**

```ntsl
Função DiMaisDiMenos(Periodo : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o indicador criado.

```ntsl
begin
Plot(DiMaisDiMenos(14));
end;
```

### Função IFR
*Manual NTSL v4.7 (14/10/2026) — p. 203*

_O "Índice de Força Relativo" IFR() mede a evolução da relação de forças entre compradores e vendedores ao longo do tempo. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu:
"abrir > exemplos"._

**Sintaxe**

```ntsl
Função IFR(Periodo : Integer): Float;
```

**Parâmetros**

Periodo: Integer; Período utilizado no momento do cálculo do indicador.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor do indicador "IFR", considerando 2 períodos para o cálculo.

```ntsl
begin
Plot(IFR(2));
end;
```

### Função PaintVar
*Manual NTSL v4.7 (14/10/2026) — p. 204*

_A função PaintVar() possui a implementação de uma estratégia de coloração, a qual compara se o fechamento do último candle é positivo ou negativo em relação ao fechamento do (candle) anterior, e, como indicador, apenas retorna o último preço do ativo. O exemplo com o código fonte está disponível no editor de estratégias, para visualizá-lo, acesse o menu: "abrir > exemplos"._

**Sintaxe**

```ntsl
Função PaintVar(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado o último preço, onde a regra de coloração correspondente poderá ser aplicada sobre o indicador.

```ntsl
begin
Plot(PaintVar);
end;
```

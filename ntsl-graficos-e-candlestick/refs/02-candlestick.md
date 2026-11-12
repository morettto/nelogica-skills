# 02 Candlestick

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Candlestick

### Funções de Candlestick
*Manual NTSL v4.7 (14/10/2026) — p. 192*

Funções de Candlestick

17.1 Função C_3WhSolds_3BlkCrows

_A função C_3WhSolds_3BlkCrows() identifica a ocorrência de dois tipos de candles: 3 White Soldiers e 3 Black
Crows._

**Sintaxe**

```ntsl
Função C_3WhSolds_3BlkCrows(Length : Integer; Factor : Integer; o3WhiteSoldiers :

Integer; o3BlackCrows : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

o3WhiteSoldiers: Integer [var]; Variável para identificação de padrão (3 White Soldiers).

o3BlackCrows: Integer [var]; Variável para identificação de padrão (3 Black Crows).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre 3 White Soldiers ou 3 Black Crows,

```ntsl
considerando 20 (Length) e 20 (Factor), será aplicada uma coloração (vermelho).
var
o3WhiteSoldiers , o3BlackCrows: Integer;
begin
if(C_3WhSolds_3BlkCrows(20, 20, o3WhiteSoldiers , o3BlackCrows) = 1) then
PaintBar(clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_BullEng_BearEng() identifica a ocorrência de dois tipos de candles: Bullish Engulfing e Bearish
Engulfing._

**Sintaxe**

```ntsl
Função C_BullEng_BearEng(Length : Integer; oBullishEngulfing : Integer;

oBearishEngulfing : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oBullishEngulfing: Integer [var]; Variável para identificação de padrão (Bullish Engulfing).

oBearishEngulfing: Integer [var]; Variável para identificação de padrão (Bearish Engulfing).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Bullish Engulfing ou Bearish

```ntsl
Engulfing, considerando 20 (Length), será aplicada uma coloração (amarelo).
var
oBullishEngulfing , oBearishEngulfing: Integer;
begin
if (C_BullEng_BearEng(20, oBullishEngulfing , oBearishEngulfing) = 1) then
PaintBar(clYellow);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_Doji() identifica a ocorrência de um candle tipo Doji._

**Sintaxe**

```ntsl
Função C_Doji(Percentual : Integer): Integer;
```

**Parâmetros**

Percentual: Integer; Limiar para (Abertura - Fechamento) que seria uma percentagem do intervalo do candle.

**Exemplo de uso:** No exemplo a seguir, caso o padrão seja identificado, considerando percentual de 5%, será aplicada uma coloração

```ntsl
(vermelho).
begin
if(C_Doji(5) = 1) then
PaintBar(clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_Hammer_HangingMan() identifica a ocorrência de dois tipos de candles: Hammer e Hanging Man._

**Sintaxe**

```ntsl
Função C_Hammer_HangingMan(Length : Integer; Factor : Integer; oHammer : Integer;

oHangingMan : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

oHammer: Integer [var]; Variável para identificação de padrão (Hammer).

oHangingMan: Integer [var]; Variável para identificação de padrão (Hanging Man).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Hammer ou Hanging Man, considerando 30

```ntsl
(Length) e 30 (Factor), será aplicada uma coloração (vermelho).
var
oHammer , oHangingMan: Integer;
begin
if (C_Hammer_HangingMan(30, 30, oHammer , oHangingMan) = 1) then
PaintBar(clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_MornDoji_EveDoji() identifica a ocorrência de dois tipos de candles: Morning Doji Star e Evening
Doji Star._

**Sintaxe**

```ntsl
Função C_MornDoji_EveDoji(Length : Integer; Percentual : Float; oMorningDojiStar :

Integer; oEveningDojiStar : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Percentual: Float; Doji limiar para o (abrir - fechar) como uma percentagem do intervalo da barra.

oMorningDojiStar: Integer [var]; Variável para identificação de padrão (Morning Doji Star).

oEveningDojiStar: Integer [var]; Variável para identificação de padrão (Evening Doji Star).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Morning Doji Star ou Evening Doji

```ntsl
Star, considerando 30 (Length) e 30 (Percentual), será aplicada uma coloração (vermelho).
var
oMorningDojiStar , oEveningDojiStar : Integer;
begin
if (C_MornDoji_EveDoji(30, 30, oMorningDojiStar , oEveningDojiStar) = 1) then
PaintBar(clRed);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_MornStar_EveStar() identifica a ocorrência de dois tipos de candles: Morning Star e Evening Star._

**Sintaxe**

```ntsl
Função C_MornStar_EveStar(Length : Integer; oMorningStar : Integer; oEveningStar :

Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oMorningStar: Integer [var]; Variável para identificação de padrão (Morning Star).

oEveningStar: Integer [var]; Variável para identificação de padrão (Evening Star).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Evening Star e Morning Star, con-

```ntsl
siderando 30 (Length), será aplicada uma coloração (verde).
var
oMorningStar , oEveningStar : Integer;
begin
if (C_MornStar_EveStar(30, oMorningStar , oEveningStar) = 1) then
PaintBar(clGreen);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_PierceLine_DkCloud() identifica a ocorrência de dois tipos de candles: Piercing Line e Dark
Cloud._

**Sintaxe**

```ntsl
Função C_PierceLine_DkCloud(Length : Integer; oPiercingLine : Integer; oDarkCloud :

Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oPiercingLine: Integer [var]; Variável para identificação de padrão (Piercing Line).

oDarkCloud: Integer [var]; Variável para identificação de padrão (Dark Cloud).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Dark Cloud e Piercing Line, con-

```ntsl
siderando 30 (Length), será aplicada uma coloração (verde).
var
oPiercingLine , oDarkCloud : Integer;
begin
if (C_PierceLine_DkCloud(30, oPiercingLine , oDarkCloud) = 1) then
PaintBar(clGreen);
end
```

**Gráfico:** ver exemplo no manual, p. 192

_A função C_ShootingStar() identifica a ocorrência de candles tipo Shooting Star._

**Sintaxe**

```ntsl
Função C_ShootingStar(Length : Integer; Factor : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

```ntsl
No exemplo a seguir, caso o padrão seja identificado, considerando 30 (Length) e 1 (Factor), será aplicada uma
coloração (verde).
begin
if (C_ShootingStar(30, 1) = 1) then
PaintBar(clGreen);
end
```

### Função C_3WhSolds_3BlkCrows
*Manual NTSL v4.7 (14/10/2026) — p. 192*

17 Funções de Candlestick

17.1 Função C_3WhSolds_3BlkCrows

_A função C_3WhSolds_3BlkCrows() identifica a ocorrência de dois tipos de candles: 3 White Soldiers e 3 Black
Crows._

**Sintaxe**

```ntsl
Função C_3WhSolds_3BlkCrows(Length : Integer; Factor : Integer; o3WhiteSoldiers :

Integer; o3BlackCrows : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

o3WhiteSoldiers: Integer [var]; Variável para identificação de padrão (3 White Soldiers).

o3BlackCrows: Integer [var]; Variável para identificação de padrão (3 Black Crows).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre 3 White Soldiers ou 3 Black Crows,

```ntsl
considerando 20 (Length) e 20 (Factor), será aplicada uma coloração (vermelho).
var
o3WhiteSoldiers , o3BlackCrows: Integer;
begin
if(C_3WhSolds_3BlkCrows(20, 20, o3WhiteSoldiers , o3BlackCrows) = 1) then
PaintBar(clRed);
end
```

### Função C_BullEng_BearEng
*Manual NTSL v4.7 (14/10/2026) — p. 194*

_A função C_BullEng_BearEng() identifica a ocorrência de dois tipos de candles: Bullish Engulfing e Bearish
Engulfing._

**Sintaxe**

```ntsl
Função C_BullEng_BearEng(Length : Integer; oBullishEngulfing : Integer;

oBearishEngulfing : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oBullishEngulfing: Integer [var]; Variável para identificação de padrão (Bullish Engulfing).

oBearishEngulfing: Integer [var]; Variável para identificação de padrão (Bearish Engulfing).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Bullish Engulfing ou Bearish

```ntsl
Engulfing, considerando 20 (Length), será aplicada uma coloração (amarelo).
var
oBullishEngulfing , oBearishEngulfing: Integer;
begin
if (C_BullEng_BearEng(20, oBullishEngulfing , oBearishEngulfing) = 1) then
PaintBar(clYellow);
end
```

### Função C_Doji
*Manual NTSL v4.7 (14/10/2026) — p. 195*

_A função C_Doji() identifica a ocorrência de um candle tipo Doji._

**Sintaxe**

```ntsl
Função C_Doji(Percentual : Integer): Integer;
```

**Parâmetros**

Percentual: Integer; Limiar para (Abertura - Fechamento) que seria uma percentagem do intervalo do candle.

**Exemplo de uso:** No exemplo a seguir, caso o padrão seja identificado, considerando percentual de 5%, será aplicada uma coloração

```ntsl
(vermelho).
begin
if(C_Doji(5) = 1) then
PaintBar(clRed);
end
```

### Função C_Hammer_HangingMan
*Manual NTSL v4.7 (14/10/2026) — p. 196*

_A função C_Hammer_HangingMan() identifica a ocorrência de dois tipos de candles: Hammer e Hanging Man._

**Sintaxe**

```ntsl
Função C_Hammer_HangingMan(Length : Integer; Factor : Integer; oHammer : Integer;

oHangingMan : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

oHammer: Integer [var]; Variável para identificação de padrão (Hammer).

oHangingMan: Integer [var]; Variável para identificação de padrão (Hanging Man).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Hammer ou Hanging Man, considerando 30

```ntsl
(Length) e 30 (Factor), será aplicada uma coloração (vermelho).
var
oHammer , oHangingMan: Integer;
begin
if (C_Hammer_HangingMan(30, 30, oHammer , oHangingMan) = 1) then
PaintBar(clRed);
end
```

### Função C_MornDoji_EveDoji
*Manual NTSL v4.7 (14/10/2026) — p. 197*

_A função C_MornDoji_EveDoji() identifica a ocorrência de dois tipos de candles: Morning Doji Star e Evening
Doji Star._

**Sintaxe**

```ntsl
Função C_MornDoji_EveDoji(Length : Integer; Percentual : Float; oMorningDojiStar :

Integer; oEveningDojiStar : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Percentual: Float; Doji limiar para o (abrir - fechar) como uma percentagem do intervalo da barra.

oMorningDojiStar: Integer [var]; Variável para identificação de padrão (Morning Doji Star).

oEveningDojiStar: Integer [var]; Variável para identificação de padrão (Evening Doji Star).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Morning Doji Star ou Evening Doji

```ntsl
Star, considerando 30 (Length) e 30 (Percentual), será aplicada uma coloração (vermelho).
var
oMorningDojiStar , oEveningDojiStar : Integer;
begin
if (C_MornDoji_EveDoji(30, 30, oMorningDojiStar , oEveningDojiStar) = 1) then
PaintBar(clRed);
end
```

### Função C_MornStar_EveStar
*Manual NTSL v4.7 (14/10/2026) — p. 199*

_A função C_MornStar_EveStar() identifica a ocorrência de dois tipos de candles: Morning Star e Evening Star._

**Sintaxe**

```ntsl
Função C_MornStar_EveStar(Length : Integer; oMorningStar : Integer; oEveningStar :

Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oMorningStar: Integer [var]; Variável para identificação de padrão (Morning Star).

oEveningStar: Integer [var]; Variável para identificação de padrão (Evening Star).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Evening Star e Morning Star, con-

```ntsl
siderando 30 (Length), será aplicada uma coloração (verde).
var
oMorningStar , oEveningStar : Integer;
begin
if (C_MornStar_EveStar(30, oMorningStar , oEveningStar) = 1) then
PaintBar(clGreen);
end
```

### Função C_PierceLine_DkCloud
*Manual NTSL v4.7 (14/10/2026) — p. 200*

_A função C_PierceLine_DkCloud() identifica a ocorrência de dois tipos de candles: Piercing Line e Dark
Cloud._

**Sintaxe**

```ntsl
Função C_PierceLine_DkCloud(Length : Integer; oPiercingLine : Integer; oDarkCloud :

Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

oPiercingLine: Integer [var]; Variável para identificação de padrão (Piercing Line).

oDarkCloud: Integer [var]; Variável para identificação de padrão (Dark Cloud).

**Exemplo de uso:** No exemplo a seguir, caso seja identificado algum dos padrões entre Dark Cloud e Piercing Line, con-

```ntsl
siderando 30 (Length), será aplicada uma coloração (verde).
var
oPiercingLine , oDarkCloud : Integer;
begin
if (C_PierceLine_DkCloud(30, oPiercingLine , oDarkCloud) = 1) then
PaintBar(clGreen);
end
```

### Função C_ShootingStar
*Manual NTSL v4.7 (14/10/2026) — p. 201*

_A função C_ShootingStar() identifica a ocorrência de candles tipo Shooting Star._

**Sintaxe**

```ntsl
Função C_ShootingStar(Length : Integer; Factor : Integer): Integer;
```

**Parâmetros**

Length: Integer; Tamanho utilizado para calcular a média do corpo do candle.

Factor: Integer; Determina quantas vezes a sombra do candle deve ser maior que o seu corpo.

```ntsl
No exemplo a seguir, caso o padrão seja identificado, considerando 30 (Length) e 1 (Factor), será aplicada uma
coloração (verde).
begin
if (C_ShootingStar(30, 1) = 1) then
PaintBar(clGreen);
end
```

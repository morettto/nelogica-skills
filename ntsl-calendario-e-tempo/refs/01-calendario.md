# 01 Calendario

*Fonte: Manual NTSL, Módulo Estratégias, versão 4.7 (14/10/2026), Nelogica — https://downloadserver-cdn.nelogica.com.br/content/profit/manual_ntsl/ManualNTSL.pdf*

Conteúdo extraído verbatim do manual (títulos e referências de página preservados). Texto do manual, em português.

## Funções de Calendário

### Funções de Calendário
*Manual NTSL v4.7 (14/10/2026) — p. 118*

Funções de Calendário

16.1 Função BarAnnualization

_A função BarAnnualization() retorna o fator de anualização (raiz quadrada) baseado no intervalo do candle (diário
= 365, semanal = 52, mensal = 12)._

**Sintaxe**

```ntsl
Função BarAnnualization(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** diário.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado de retorno da função BarAnnualization() de PETR4
var
temp : Float;
begin
temp := BarAnnualization();
Plot(temp);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função BarDuration() retorna, em minutos, a duração da barra atual._

**Sintaxe**

```ntsl
Função BarDuration(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado da função BarDuration().
var
temp : Integer;
begin
temp := BarDuration();
Plot(temp);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função BarDurationF() retorna, em minutos, a duração da barra atual com valores não inteiros._

**Sintaxe**

```ntsl
Função BarDurationF(): Float;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado da função BarDurationF().
var
temp : Float;
begin
temp := BarDurationF();
Plot(temp);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Bartype() retorna um código numérico referente ao período utilizado._

**Sintaxe**

```ntsl
Função Bartype(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável numCode irá receber um inteiro referente ao tempo determinado.

```ntsl
var
numCode : Integer;
begin
numCode := Bartype();
Plot(numCode);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CalcDate() retorna um valor o qual representa uma data deslocada, obtida ao adicionar ou subtrair dias de uma data de referência. Datas são representadas pelo tipo de dado Integer, no formato: AnoMêsDia._

**Sintaxe**

```ntsl
Função CalcDate(RefDate: Integer; DaysChange: Integer): Integer;
```

**Parâmetros**

RefDate: Integer; Determina a data que será utilizada como base para o deslocamento.

DaysChange: Integer; Determina quantos dias serão adicionados ou subtraídos da data de referência.

**Exemplo de uso:** No exemplo abaixo, será visualizada, graficamente, a data resultante ao subtrair 14 dias da data de 16/04/2025

```ntsl
(1250416).
begin
Plot(CalcDate(1250416, -14));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CalcTime() retorna um valor o qual representa uma hora deslocada, obtida ao adicionar ou subtrair minutos de uma hora de referência. Horas são representadas pelo tipo de dado Integer, no formato (24 horas):
HorasMinutos._

**Sintaxe**

```ntsl
Função CalcTime(RefTime: Integer; MinuteChange: Integer): Integer;
```

**Parâmetros**

RefTime: Integer; Determina a hora que será utilizada como base para o deslocamento.

MinuteChange: Integer; Determina quantos minutos serão adicionados ou subtraídos da hora de referência.

**Exemplo de uso:** No exemplo abaixo, será visualizada, graficamente, a hora resultante ao deslocar 65 minutos a partir das 9h.

```ntsl
begin
Plot(CalcTime(900, 65));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CalcWorkingDate() retorna uma nova data obtida a partir da soma ou subtração de uma quantidade especificada de dias úteis em relação a uma data base._

**Sintaxe**

```ntsl
Função CalcWorkingDate(Data: Integer, Dias: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para o cálculo.

Dias: Integer; Quantidade de dias úteis a serem somados ou subtraídos. Valores positivos somam dias úteis e valores negativos subtraem dias úteis.

**Exemplo de uso:** No exemplo abaixo, o código calcula uma nova data adicionando uma quantidade de dias úteis a uma data fixa e marca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,12,01);
nNewDate := CalcWorkingDate(nDate, 2);
if (Date = nNewDate) then
VerticalLineCustom(ClGreen, 2.5, psDash, "");
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CloseD() tem como finalidade retornar o valor de fechamento de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função CloseD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento de dois dias anteriores ao dia atual.

```ntsl
begin
Plot(CloseD(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CloseM() tem como finalidade retornar o valor de fechamento de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função CloseM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento de 3 meses anteriores ao mês atual.

```ntsl
begin
Plot(CloseM(3));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CloseW() tem como finalidade retornar o valor de fechamento de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função CloseW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento 2 semanas anteriores à semana atual.

```ntsl
begin
Plot(CloseW(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CloseY() tem como finalidade retornar o valor de fechamento de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função CloseY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de valor de fechamento do ano anterior.

```ntsl
begin
Plot(CloseY(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CurrentAssetDate() retorna a data atual do ativo no gráfico. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função CurrentAssetDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do ativo.

```ntsl
begin
Plot(CurrentAssetDate);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CurrentDate() possui como finalidade retornar a data atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função CurrentDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do dia atual.

```ntsl
begin
Plot(CurrentDate);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função CurrentTime() possui como finalidade retornar a hora atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: HHMM._

**Sintaxe**

```ntsl
Função CurrentTime(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora atual.

```ntsl
begin
Plot(CurrentTime);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Date() possui como finalidade retornar a data do candle que está sendo analisado. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Date(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do candle atual.

```ntsl
begin
Plot(Date);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função DayOfMonth() retorna o dia do mês de uma data específica. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função DayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o dia.

```ntsl
No exemplo a seguir, será plotado no gráfico o dia do mês dia 01/04/25 (1250401).
begin
Plot(DayOfMonth(1250401));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função DayOfWeek() retorna o dia da semana de uma data específica. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função DayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o dia da semana.

```ntsl
No exemplo a seguir, será plotado no gráfico o dia da semana relativo ao dia 01/04/25 (1250401), que é 2
(terça-feira).
begin
Plot(DayOfWeek(1250401));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função DaysToExpiration() retorna a quantidade de dias úteis restantes até a terceira sexta-feira de um deter- minado mês e ano._

**Sintaxe**

```ntsl
Função DaysToExpiration(ExpMonth: Integer; ExpYear: Integer): Integer;
```

**Parâmetros**

ExpMonth: Integer; Determina o mês que se deseja a informação.

ExpYear: Integer; Determina o ano desejado para análise, onde deverá estar no formato: 1AnoDesejado.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico quantidade de dias úteis até a terceira sexta-feira de dezembro/2025.

```ntsl
begin
Plot(DaysToExpiration(12, 125));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função ELDate() possui como finalidade retornar uma data em EasyLanguage format (YYYMMDD). Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função ELDate(Year: Integer; Month: Integer; Day: Integer): Integer;
```

**Parâmetros**

Year: Integer; Determina o ano no formato YYYY.

Month: Integer; Determina mês no formato MM.

Day: Integer; Determina o dia no formato DD.

```ntsl
No exemplo a seguir, será plotado no gráfico a data de 25/12/2024 no formato: 1241225.
begin
Plot(ELDate(2024, 12, 25));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função ELDate_Consol() possui como finalidade converter uma data YYYYMMDD em formato EasyLanguage (YYYM-
MDD)._

**Sintaxe**

```ntsl
Função ELDate_Consol(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data no formato YYYYMMDD.

```ntsl
No exemplo a seguir, será plotado no gráfico a data de 25/12/2024 no formato: 20241225.
begin
Plot(ELDate_Consol(20241225));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função FindBar() retorna o índice de uma barra através de uma data e hora, onde a contagem é iniciada a partir do candle atual (índice 0). Datas e horas são representadas, respectivamente, pelo tipo de dado Integer, no formato:
1AnoMêsDia e HHMM._

**Sintaxe**

```ntsl
Função FindBar(TargetDate: Integer; TargetTime: Integer): Integer;
```

**Parâmetros**

TargetDate: Integer; Data do candle.

TargetTime: Integer; Hora do candle específico.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o índice do candle relacionado com o horário 11h00 do dia atual.

```ntsl
begin
Plot(FindBar(CurrentDate, 1100));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função FirstWorkingDayOfMonth() retorna a data correspondente ao primeiro dia útil do mês da data informada ou da data atual._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil do mês. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil do mês e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfMonth() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função FirstWorkingDayOfWeek() retorna a data correspondente ao primeiro dia útil da semana._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil da semana. Valor padrão é Today
(data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil da semana e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfWeek() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função FirstWorkingDayOfYear() retorna a data correspondente ao primeiro dia útil do ano._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfYear(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil do ano. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil do ano e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfYear() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Friday() retorna o número 5, representando o dia da semana: sexta-feira._

**Sintaxe**

```ntsl
Função Friday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 5, referente ao dia específico da semana.

```ntsl
begin
Plot(Friday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função HighD() tem como finalidade retornar o valor de máxima de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função HighD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de dois dias anteriores ao dia atual.

```ntsl
begin
Plot(HighD(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função HighM() tem como finalidade retornar o valor de máxima de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função HighM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de cinco meses anteriores ao mês atual.

```ntsl
begin
Plot(HighM(5));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função HighW() tem como finalidade retornar o valor de máxima de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função HighW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de sete semanas anteriores à semana atual.

```ntsl
begin
Plot(HighW(7));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função HighY() tem como finalidade retornar o valor de máxima de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função HighY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de dois anos anteriores ao atual.

```ntsl
begin
Plot(HighY(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função IsWorkingDay() retorna True caso a data informada seja um dia útil._

**Sintaxe**

```ntsl
Função IsWorkingDay(Date: Integer): Boolean;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para verificar se é um dia útil. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde a um dia útil, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if IsWorkingDay() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastCalcDate() retorna a data do último candle completo formado dentro do gráfico. Datas são repre- sentadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função LastCalcDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data dos candles de acordo com o andamento do mercado.

```ntsl
begin
Plot(LastCalcDate);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastCalcTime() retorna a hora do último candle completo formado dentro do gráfico, no formato 24h
(HHMM)._

**Sintaxe**

```ntsl
Função LastCalcTime(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora de fechamento dos candles, de acordo com o andamento do mercado.

```ntsl
begin
Plot(LastCalcTime);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastDayOfMonth() retorna o último dia do mês de referência._

**Sintaxe**

```ntsl
Função LastDayOfMonth(Month: Integer): Integer;
```

**Parâmetros**

Month: Integer; Determina o mês de referência, de Janeiro (1) a Dezembro (12).

```ntsl
No exemplo a seguir, será plotado no gráfico o último dia (30) do mês de abril.
begin
Plot(LastDayOfMonth(4));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastWorkingDayOfMonth() retorna a data correspondente ao último dia útil do mês._

**Sintaxe**

```ntsl
Função LastWorkingDayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil do mês. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil do mês e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfMonth() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastWorkingDayOfWeek() retorna a data correspondente ao último dia útil da semana._

**Sintaxe**

```ntsl
Função LastWorkingDayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil da semana. Valor padrão é Today
(data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil da semana e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfWeek() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LastWorkingDayOfYear() retorna a data correspondente ao último dia útil do ano._

**Sintaxe**

```ntsl
Função LastWorkingDayOfYear(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil do ano. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil do ano e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfYear() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LowD() tem como finalidade retornar o valor de mínima de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função LowD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de três dias anteriores ao dia atual.

```ntsl
begin
Plot(LowD(3));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LowM() tem como finalidade retornar o valor de mínima de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função LowM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

```ntsl
No exemplo a seguir, será plotado no gráfico o valor de mínima de três meses (3) atrás.
begin
Plot(LowM(3));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LowW() tem como finalidade retornar o valor de mínima de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função LowW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de sete semanas anteriores à semana atual.

```ntsl
begin
Plot(LowW(7));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função LowY() tem como finalidade retornar o valor de mínima de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função LowY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de dois anos anteriores ao atual.

```ntsl
begin
Plot(LowY(2));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

**Sintaxe**

```ntsl
Função MinutesIntoWeek(XDay: Integer; XTime: Integer): Integer;
```

**Parâmetros**

XDay: Integer; Dia de limite para a conversão em minutos.

– 0: Domingo;

– 1: Segunda;

– 2: Terça;

– 3: Quarta;

– 4: Quinta;

– 5: Sexta;

– 6: Sábado.

XTime: Integer; Hora de limite para a conversão.

```ntsl
No exemplo a seguir, será atribuído à variável tMin o total de 8640 minutos entre domingo (Dia 0, 00h00) e
sábado (Dia 6, 00h00).
var
tMin : Integer;
begin
tMin := MinutesIntoWeek(6 , 0000);
Plot(tMin);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

**Sintaxe**

```ntsl
Função Monday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor 1, referente ao dia específico da semana.

```ntsl
begin
Plot(Monday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Month() retorna o mês de uma data específica. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Month(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o mês.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o mês atual.

```ntsl
begin
Plot(Month(CurrentDate));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Next3rdFriday() retorna a quantidade de dias úteis restantes até a terceira sexta-feira de determinado mês subsequente._

**Sintaxe**

```ntsl
Função Next3rdFriday(Series: Integer): Integer;
```

**Parâmetros**

Series: Integer; Determina o mês que se deseja a informação, onde a contagem inicia-se a partir do mês atual (0).

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a quantidade de dias úteis até a terceira sexta-feira do mês seguinte.

```ntsl
begin
Plot(Next3rdFriday(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função OpenD() tem como finalidade retornar o valor de abertura de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função OpenD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura de seis dias anteriores ao dia atual.

```ntsl
begin
Plot(OpenD(6));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função OpenM() tem como finalidade retornar o valor de abertura de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função OpenM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura do mês anterior ao atual.

```ntsl
begin
Plot(OpenM(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função OpenW() tem como finalidade retornar o valor de abertura de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função OpenW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura de cinco semanas anteriores à semana atual.

```ntsl
begin
Plot(OpenW(5));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função OpenY() tem como finalidade retornar o valor de abertura de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função OpenY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura do ano anterior ao atual.

```ntsl
begin
Plot(OpenY(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função QuarterEnd() recebe uma data e retorna a data correspondente ao último dia do trimestre ao qual ela pertence._

**Sintaxe**

```ntsl
Função QuarterEnd(Data: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para identificar o trimestre.

**Exemplo de uso:** No exemplo abaixo, o código calcula o último dia do trimestre para uma data informada e destaca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,09,01);
nNewDate := QuarterEnd(nDate);
if (Date = nNewDate) then
VerticalLineCustom(clRed, 2.5, psDash, "Fim", 8, 0, 33, 27);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função QuarterStart() recebe uma data e retorna a data correspondente ao primeiro dia do trimestre ao qual ela pertence._

**Sintaxe**

```ntsl
Função QuarterStart(Data: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para identificar o trimestre.

**Exemplo de uso:** No exemplo abaixo, o código calcula o primeiro dia do trimestre para uma data informada e destaca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,09,01);
nNewDate := QuarterStart(nDate);
if (Date = nNewDate) then
VerticalLineCustom(clGreen, 2.5, psDash, "Inicio", 8, 0, 33, 27);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função RS_BarsPerDay() retorna o número estimado de candles de determinada periodicidade (em minutos).
Caso o periodo seja diário, será obtido 1 como retorno, e, para períodos em minutos, ocorrerá a divisão do número total de minutos em um dia (1440) pela periodicidade selecionada._

**Sintaxe**

```ntsl
Função RS_BarsPerDay(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o retorno da chamada de função.

```ntsl
begin
Plot(RS_BarsPerDay);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Saturday() retorna o número 6, representando o dia da semana: sábado._

**Sintaxe**

```ntsl
Função Saturday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 6, referente ao dia específico da semana.

```ntsl
begin
Plot(Saturday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Sunday() retorna o número 0, representando o dia da semana: domingo._

**Sintaxe**

```ntsl
Função Sunday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 0, referente ao dia específico da semana.

```ntsl
begin
Plot(Sunday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Thursday() retorna o número 4, representando o dia da semana: quinta-feira._

**Sintaxe**

```ntsl
Função Thursday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 4, referente ao dia específico da semana.

```ntsl
begin
Plot(Thursday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Time() possui como finalidade retornar a hora de abertura do candle atual._

**Sintaxe**

```ntsl
Função Time(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora de abertura do candle.

```ntsl
begin
Plot(Time);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função TimeExchange() retorna o tempo do candle de acordo com o timezone da bolsa._

**Sintaxe**

```ntsl
Função TimeExchange(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data de acordo com o timezone da bolsa.

```ntsl
begin
Plot(TimeExchange);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função TimeToMinutes() tem como propósito converter um valor de hora no formato inteiro (HHMM) para a sua representação correspondente em minutos decorridos desde 00h00._

**Sintaxe**

```ntsl
Função TimeToMinutes(XTime: Integer): Integer;
```

**Parâmetros**

XTime: Integer; Hora para a conversão.

```ntsl
No exemplo a seguir, será plotado no gráfico a conversão em minutos da hora: 12h30 (750 minutos).
begin
Plot(TimeToMinutes(1230));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Today() possui como finalidade retornar a data atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Today(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do dia atual.

```ntsl
begin
Plot(Today);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Tuesday() retorna o número 2, representando o dia da semana: terça-feira._

**Sintaxe**

```ntsl
Função Tuesday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 2, referente ao dia específico da semana.

```ntsl
begin
Plot(Tuesday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função VolumeD() tem como finalidade retornar o volume financeiro de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função VolumeD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume de 6 dias anteriores ao dia atual.

```ntsl
begin
Plot(VolumeD(6));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função VolumeM() tem como finalidade retornar o volume financeiro de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função VolumeM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume do mês anterior ao atual.

```ntsl
begin
Plot(VolumeM(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função VolumeW() tem como finalidade retornar o volume financeiro de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função VolumeW(WeeksAgo: Integer): Float;
```

**Parâmetros**

WeeksAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor volume de cinco semanas anteriores à semana atual.

```ntsl
begin
Plot(VolumeW(5));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função VolumeY() tem como finalidade retornar o volume financeiro de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função VolumeY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume do ano anterior ao atual.

```ntsl
begin
Plot(VolumeY(1));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Wednesday() retorna o número 3, representando o dia da semana: quarta-feira._

**Sintaxe**

```ntsl
Função Wednesday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 3, referente ao dia específico da semana.

```ntsl
begin
Plot(Wednesday);
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Year() retorna o ano de uma data específica. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Year(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o ano.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o ano atual.

```ntsl
begin
Plot(Year(CurrentDate));
end;
```

**Gráfico:** ver exemplo no manual, p. 118

_A função Yesterday() retorna a data do dia de ontem. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Yesterday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data de ontem.

```ntsl
begin
Plot(Yesterday);
end;
```

### Função BarAnnualization
*Manual NTSL v4.7 (14/10/2026) — p. 118*

16 Funções de Calendário

16.1 Função BarAnnualization

_A função BarAnnualization() retorna o fator de anualização (raiz quadrada) baseado no intervalo do candle (diário
= 365, semanal = 52, mensal = 12)._

**Sintaxe**

```ntsl
Função BarAnnualization(): Float;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** diário.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado de retorno da função BarAnnualization() de PETR4
var
temp : Float;
begin
temp := BarAnnualization();
Plot(temp);
end;
```

### Função BarDuration
*Manual NTSL v4.7 (14/10/2026) — p. 119*

_A função BarDuration() retorna, em minutos, a duração da barra atual._

**Sintaxe**

```ntsl
Função BarDuration(): Integer;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado da função BarDuration().
var
temp : Integer;
begin
temp := BarDuration();
Plot(temp);
end;
```

### Função BarDurationF
*Manual NTSL v4.7 (14/10/2026) — p. 120*

_A função BarDurationF() retorna, em minutos, a duração da barra atual com valores não inteiros._

**Sintaxe**

```ntsl
Função BarDurationF(): Float;
```

**Parâmetros**

Sem parâmetros.

```ntsl
No exemplo abaixo, a variável temp irá receber o dado da função BarDurationF().
var
temp : Float;
begin
temp := BarDurationF();
Plot(temp);
end;
```

### Função Bartype
*Manual NTSL v4.7 (14/10/2026) — p. 121*

_A função Bartype() retorna um código numérico referente ao período utilizado._

**Sintaxe**

```ntsl
Função Bartype(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo, a variável numCode irá receber um inteiro referente ao tempo determinado.

```ntsl
var
numCode : Integer;
begin
numCode := Bartype();
Plot(numCode);
end;
```

### Função CalcDate
*Manual NTSL v4.7 (14/10/2026) — p. 122*

_A função CalcDate() retorna um valor o qual representa uma data deslocada, obtida ao adicionar ou subtrair dias de uma data de referência. Datas são representadas pelo tipo de dado Integer, no formato: AnoMêsDia._

**Sintaxe**

```ntsl
Função CalcDate(RefDate: Integer; DaysChange: Integer): Integer;
```

**Parâmetros**

RefDate: Integer; Determina a data que será utilizada como base para o deslocamento.

DaysChange: Integer; Determina quantos dias serão adicionados ou subtraídos da data de referência.

**Exemplo de uso:** No exemplo abaixo, será visualizada, graficamente, a data resultante ao subtrair 14 dias da data de 16/04/2025

```ntsl
(1250416).
begin
Plot(CalcDate(1250416, -14));
end;
```

### Função CalcTime
*Manual NTSL v4.7 (14/10/2026) — p. 123*

_A função CalcTime() retorna um valor o qual representa uma hora deslocada, obtida ao adicionar ou subtrair minutos de uma hora de referência. Horas são representadas pelo tipo de dado Integer, no formato (24 horas):
HorasMinutos._

**Sintaxe**

```ntsl
Função CalcTime(RefTime: Integer; MinuteChange: Integer): Integer;
```

**Parâmetros**

RefTime: Integer; Determina a hora que será utilizada como base para o deslocamento.

MinuteChange: Integer; Determina quantos minutos serão adicionados ou subtraídos da hora de referência.

**Exemplo de uso:** No exemplo abaixo, será visualizada, graficamente, a hora resultante ao deslocar 65 minutos a partir das 9h.

```ntsl
begin
Plot(CalcTime(900, 65));
end;
```

### Função CalcWorkingDate
*Manual NTSL v4.7 (14/10/2026) — p. 124*

_A função CalcWorkingDate() retorna uma nova data obtida a partir da soma ou subtração de uma quantidade especificada de dias úteis em relação a uma data base._

**Sintaxe**

```ntsl
Função CalcWorkingDate(Data: Integer, Dias: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para o cálculo.

Dias: Integer; Quantidade de dias úteis a serem somados ou subtraídos. Valores positivos somam dias úteis e valores negativos subtraem dias úteis.

**Exemplo de uso:** No exemplo abaixo, o código calcula uma nova data adicionando uma quantidade de dias úteis a uma data fixa e marca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,12,01);
nNewDate := CalcWorkingDate(nDate, 2);
if (Date = nNewDate) then
VerticalLineCustom(ClGreen, 2.5, psDash, "");
end;
```

### Função CloseD
*Manual NTSL v4.7 (14/10/2026) — p. 126*

_A função CloseD() tem como finalidade retornar o valor de fechamento de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função CloseD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento de dois dias anteriores ao dia atual.

```ntsl
begin
Plot(CloseD(2));
end;
```

### Função CloseM
*Manual NTSL v4.7 (14/10/2026) — p. 127*

_A função CloseM() tem como finalidade retornar o valor de fechamento de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função CloseM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento de 3 meses anteriores ao mês atual.

```ntsl
begin
Plot(CloseM(3));
end;
```

### Função CloseW
*Manual NTSL v4.7 (14/10/2026) — p. 128*

_A função CloseW() tem como finalidade retornar o valor de fechamento de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função CloseW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de fechamento 2 semanas anteriores à semana atual.

```ntsl
begin
Plot(CloseW(2));
end;
```

### Função CloseY
*Manual NTSL v4.7 (14/10/2026) — p. 129*

_A função CloseY() tem como finalidade retornar o valor de fechamento de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função CloseY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de valor de fechamento do ano anterior.

```ntsl
begin
Plot(CloseY(1));
end;
```

### Função CurrentAssetDate
*Manual NTSL v4.7 (14/10/2026) — p. 130*

_A função CurrentAssetDate() retorna a data atual do ativo no gráfico. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função CurrentAssetDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do ativo.

```ntsl
begin
Plot(CurrentAssetDate);
end;
```

### Função CurrentDate
*Manual NTSL v4.7 (14/10/2026) — p. 131*

_A função CurrentDate() possui como finalidade retornar a data atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função CurrentDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do dia atual.

```ntsl
begin
Plot(CurrentDate);
end;
```

### Função CurrentTime
*Manual NTSL v4.7 (14/10/2026) — p. 132*

_A função CurrentTime() possui como finalidade retornar a hora atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: HHMM._

**Sintaxe**

```ntsl
Função CurrentTime(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora atual.

```ntsl
begin
Plot(CurrentTime);
end;
```

### Função Date
*Manual NTSL v4.7 (14/10/2026) — p. 133*

_A função Date() possui como finalidade retornar a data do candle que está sendo analisado. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Date(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do candle atual.

```ntsl
begin
Plot(Date);
end;
```

### Função DayOfMonth
*Manual NTSL v4.7 (14/10/2026) — p. 134*

_A função DayOfMonth() retorna o dia do mês de uma data específica. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função DayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o dia.

```ntsl
No exemplo a seguir, será plotado no gráfico o dia do mês dia 01/04/25 (1250401).
begin
Plot(DayOfMonth(1250401));
end;
```

### Função DayOfWeek
*Manual NTSL v4.7 (14/10/2026) — p. 135*

_A função DayOfWeek() retorna o dia da semana de uma data específica. Datas são representadas pelo tipo de dado
Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função DayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o dia da semana.

```ntsl
No exemplo a seguir, será plotado no gráfico o dia da semana relativo ao dia 01/04/25 (1250401), que é 2
(terça-feira).
begin
Plot(DayOfWeek(1250401));
end;
```

### Função DaysToExpiration
*Manual NTSL v4.7 (14/10/2026) — p. 136*

_A função DaysToExpiration() retorna a quantidade de dias úteis restantes até a terceira sexta-feira de um deter- minado mês e ano._

**Sintaxe**

```ntsl
Função DaysToExpiration(ExpMonth: Integer; ExpYear: Integer): Integer;
```

**Parâmetros**

ExpMonth: Integer; Determina o mês que se deseja a informação.

ExpYear: Integer; Determina o ano desejado para análise, onde deverá estar no formato: 1AnoDesejado.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico quantidade de dias úteis até a terceira sexta-feira de dezembro/2025.

```ntsl
begin
Plot(DaysToExpiration(12, 125));
end;
```

### Função ELDate
*Manual NTSL v4.7 (14/10/2026) — p. 137*

_A função ELDate() possui como finalidade retornar uma data em EasyLanguage format (YYYMMDD). Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função ELDate(Year: Integer; Month: Integer; Day: Integer): Integer;
```

**Parâmetros**

Year: Integer; Determina o ano no formato YYYY.

Month: Integer; Determina mês no formato MM.

Day: Integer; Determina o dia no formato DD.

```ntsl
No exemplo a seguir, será plotado no gráfico a data de 25/12/2024 no formato: 1241225.
begin
Plot(ELDate(2024, 12, 25));
end;
```

### Função ELDate_Consol
*Manual NTSL v4.7 (14/10/2026) — p. 138*

_A função ELDate_Consol() possui como finalidade converter uma data YYYYMMDD em formato EasyLanguage (YYYM-
MDD)._

**Sintaxe**

```ntsl
Função ELDate_Consol(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data no formato YYYYMMDD.

```ntsl
No exemplo a seguir, será plotado no gráfico a data de 25/12/2024 no formato: 20241225.
begin
Plot(ELDate_Consol(20241225));
end;
```

### Função FindBar
*Manual NTSL v4.7 (14/10/2026) — p. 139*

_A função FindBar() retorna o índice de uma barra através de uma data e hora, onde a contagem é iniciada a partir do candle atual (índice 0). Datas e horas são representadas, respectivamente, pelo tipo de dado Integer, no formato:
1AnoMêsDia e HHMM._

**Sintaxe**

```ntsl
Função FindBar(TargetDate: Integer; TargetTime: Integer): Integer;
```

**Parâmetros**

TargetDate: Integer; Data do candle.

TargetTime: Integer; Hora do candle específico.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o índice do candle relacionado com o horário 11h00 do dia atual.

```ntsl
begin
Plot(FindBar(CurrentDate, 1100));
end;
```

### Função FirstWorkingDayOfMonth
*Manual NTSL v4.7 (14/10/2026) — p. 140*

_A função FirstWorkingDayOfMonth() retorna a data correspondente ao primeiro dia útil do mês da data informada ou da data atual._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil do mês. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil do mês e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfMonth() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função FirstWorkingDayOfWeek
*Manual NTSL v4.7 (14/10/2026) — p. 142*

_A função FirstWorkingDayOfWeek() retorna a data correspondente ao primeiro dia útil da semana._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil da semana. Valor padrão é Today
(data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil da semana e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfWeek() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função FirstWorkingDayOfYear
*Manual NTSL v4.7 (14/10/2026) — p. 144*

_A função FirstWorkingDayOfYear() retorna a data correspondente ao primeiro dia útil do ano._

**Sintaxe**

```ntsl
Função FirstWorkingDayOfYear(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do primeiro dia útil do ano. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao primeiro dia útil do ano e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = FirstWorkingDayOfYear() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função Friday
*Manual NTSL v4.7 (14/10/2026) — p. 146*

_A função Friday() retorna o número 5, representando o dia da semana: sexta-feira._

**Sintaxe**

```ntsl
Função Friday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 5, referente ao dia específico da semana.

```ntsl
begin
Plot(Friday);
end;
```

### Função HighD
*Manual NTSL v4.7 (14/10/2026) — p. 147*

_A função HighD() tem como finalidade retornar o valor de máxima de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função HighD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de dois dias anteriores ao dia atual.

```ntsl
begin
Plot(HighD(2));
end;
```

### Função HighM
*Manual NTSL v4.7 (14/10/2026) — p. 148*

_A função HighM() tem como finalidade retornar o valor de máxima de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função HighM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de cinco meses anteriores ao mês atual.

```ntsl
begin
Plot(HighM(5));
end;
```

### Função HighW
*Manual NTSL v4.7 (14/10/2026) — p. 149*

_A função HighW() tem como finalidade retornar o valor de máxima de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função HighW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de sete semanas anteriores à semana atual.

```ntsl
begin
Plot(HighW(7));
end;
```

### Função HighY
*Manual NTSL v4.7 (14/10/2026) — p. 150*

_A função HighY() tem como finalidade retornar o valor de máxima de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função HighY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de máxima de dois anos anteriores ao atual.

```ntsl
begin
Plot(HighY(2));
end;
```

### Função IsWorkingDay
*Manual NTSL v4.7 (14/10/2026) — p. 151*

_A função IsWorkingDay() retorna True caso a data informada seja um dia útil._

**Sintaxe**

```ntsl
Função IsWorkingDay(Date: Integer): Boolean;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para verificar se é um dia útil. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde a um dia útil, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if IsWorkingDay() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função LastCalcDate
*Manual NTSL v4.7 (14/10/2026) — p. 152*

_A função LastCalcDate() retorna a data do último candle completo formado dentro do gráfico. Datas são repre- sentadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função LastCalcDate(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data dos candles de acordo com o andamento do mercado.

```ntsl
begin
Plot(LastCalcDate);
end;
```

### Função LastCalcTime
*Manual NTSL v4.7 (14/10/2026) — p. 153*

_A função LastCalcTime() retorna a hora do último candle completo formado dentro do gráfico, no formato 24h
(HHMM)._

**Sintaxe**

```ntsl
Função LastCalcTime(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora de fechamento dos candles, de acordo com o andamento do mercado.

```ntsl
begin
Plot(LastCalcTime);
end;
```

### Função LastDayOfMonth
*Manual NTSL v4.7 (14/10/2026) — p. 154*

_A função LastDayOfMonth() retorna o último dia do mês de referência._

**Sintaxe**

```ntsl
Função LastDayOfMonth(Month: Integer): Integer;
```

**Parâmetros**

Month: Integer; Determina o mês de referência, de Janeiro (1) a Dezembro (12).

```ntsl
No exemplo a seguir, será plotado no gráfico o último dia (30) do mês de abril.
begin
Plot(LastDayOfMonth(4));
end;
```

### Função LastWorkingDayOfMonth
*Manual NTSL v4.7 (14/10/2026) — p. 155*

_A função LastWorkingDayOfMonth() retorna a data correspondente ao último dia útil do mês._

**Sintaxe**

```ntsl
Função LastWorkingDayOfMonth(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil do mês. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil do mês e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfMonth() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função LastWorkingDayOfWeek
*Manual NTSL v4.7 (14/10/2026) — p. 157*

_A função LastWorkingDayOfWeek() retorna a data correspondente ao último dia útil da semana._

**Sintaxe**

```ntsl
Função LastWorkingDayOfWeek(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil da semana. Valor padrão é Today
(data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil da semana e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfWeek() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função LastWorkingDayOfYear
*Manual NTSL v4.7 (14/10/2026) — p. 159*

_A função LastWorkingDayOfYear() retorna a data correspondente ao último dia útil do ano._

**Sintaxe**

```ntsl
Função LastWorkingDayOfYear(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer [Opcional]; Data base para o cálculo do último dia útil do ano. Valor padrão é Today (data atual).

**Exemplo de uso:** No exemplo abaixo, o código verifica se o candle atual corresponde ao último dia útil do ano e, em caso positivo, plota os valores mínimo e máximo do dia.

```ntsl
var
nMin : Float;
nMax : Float;
begin
if Date = LastWorkingDayOfYear() then
begin
nMin := lowD(0);
nMax := highD(0);
end;
Plot(nMin);
Plot2(nMax);
end;
```

### Função LowD
*Manual NTSL v4.7 (14/10/2026) — p. 161*

_A função LowD() tem como finalidade retornar o valor de mínima de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função LowD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de três dias anteriores ao dia atual.

```ntsl
begin
Plot(LowD(3));
end;
```

### Função LowM
*Manual NTSL v4.7 (14/10/2026) — p. 162*

_A função LowM() tem como finalidade retornar o valor de mínima de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função LowM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

```ntsl
No exemplo a seguir, será plotado no gráfico o valor de mínima de três meses (3) atrás.
begin
Plot(LowM(3));
end;
```

### Função LowW
*Manual NTSL v4.7 (14/10/2026) — p. 163*

_A função LowW() tem como finalidade retornar o valor de mínima de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função LowW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de sete semanas anteriores à semana atual.

```ntsl
begin
Plot(LowW(7));
end;
```

### Função LowY
*Manual NTSL v4.7 (14/10/2026) — p. 164*

_A função LowY() tem como finalidade retornar o valor de mínima de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função LowY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de mínima de dois anos anteriores ao atual.

```ntsl
begin
Plot(LowY(2));
end;
```

### Função MinutesIntoWeek
*Manual NTSL v4.7 (14/10/2026) — p. 165*

A função MinutesIntoWeek() retorna o número de minutos entre domingo (Dia: 0 – Hora: 0h00) até o dia e hora determinados por parâmetro.

**Sintaxe**

```ntsl
Função MinutesIntoWeek(XDay: Integer; XTime: Integer): Integer;
```

**Parâmetros**

XDay: Integer; Dia de limite para a conversão em minutos.

– 0: Domingo;

– 1: Segunda;

– 2: Terça;

– 3: Quarta;

– 4: Quinta;

– 5: Sexta;

– 6: Sábado.

XTime: Integer; Hora de limite para a conversão.

```ntsl
No exemplo a seguir, será atribuído à variável tMin o total de 8640 minutos entre domingo (Dia 0, 00h00) e
sábado (Dia 6, 00h00).
var
tMin : Integer;
begin
tMin := MinutesIntoWeek(6 , 0000);
Plot(tMin);
end;
```

### Função Monday
*Manual NTSL v4.7 (14/10/2026) — p. 167*

A função Monday() retorna o número 1, representando o dia da semana: segunda-feira.

**Sintaxe**

```ntsl
Função Monday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor 1, referente ao dia específico da semana.

```ntsl
begin
Plot(Monday);
end;
```

### Função Month
*Manual NTSL v4.7 (14/10/2026) — p. 168*

_A função Month() retorna o mês de uma data específica. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Month(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o mês.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o mês atual.

```ntsl
begin
Plot(Month(CurrentDate));
end;
```

### Função Next3rdFriday
*Manual NTSL v4.7 (14/10/2026) — p. 169*

_A função Next3rdFriday() retorna a quantidade de dias úteis restantes até a terceira sexta-feira de determinado mês subsequente._

**Sintaxe**

```ntsl
Função Next3rdFriday(Series: Integer): Integer;
```

**Parâmetros**

Series: Integer; Determina o mês que se deseja a informação, onde a contagem inicia-se a partir do mês atual (0).

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a quantidade de dias úteis até a terceira sexta-feira do mês seguinte.

```ntsl
begin
Plot(Next3rdFriday(1));
end;
```

### Função OpenD
*Manual NTSL v4.7 (14/10/2026) — p. 170*

_A função OpenD() tem como finalidade retornar o valor de abertura de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função OpenD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura de seis dias anteriores ao dia atual.

```ntsl
begin
Plot(OpenD(6));
end;
```

### Função OpenM
*Manual NTSL v4.7 (14/10/2026) — p. 171*

_A função OpenM() tem como finalidade retornar o valor de abertura de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função OpenM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura do mês anterior ao atual.

```ntsl
begin
Plot(OpenM(1));
end;
```

### Função OpenW
*Manual NTSL v4.7 (14/10/2026) — p. 172*

_A função OpenW() tem como finalidade retornar o valor de abertura de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função OpenW(PeriodsAgo: Integer): Float;
```

**Parâmetros**

PeriodsAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura de cinco semanas anteriores à semana atual.

```ntsl
begin
Plot(OpenW(5));
end;
```

### Função OpenY
*Manual NTSL v4.7 (14/10/2026) — p. 173*

_A função OpenY() tem como finalidade retornar o valor de abertura de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função OpenY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor de abertura do ano anterior ao atual.

```ntsl
begin
Plot(OpenY(1));
end;
```

### Função QuarterEnd
*Manual NTSL v4.7 (14/10/2026) — p. 174*

_A função QuarterEnd() recebe uma data e retorna a data correspondente ao último dia do trimestre ao qual ela pertence._

**Sintaxe**

```ntsl
Função QuarterEnd(Data: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para identificar o trimestre.

**Exemplo de uso:** No exemplo abaixo, o código calcula o último dia do trimestre para uma data informada e destaca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,09,01);
nNewDate := QuarterEnd(nDate);
if (Date = nNewDate) then
VerticalLineCustom(clRed, 2.5, psDash, "Fim", 8, 0, 33, 27);
end;
```

### Função QuarterStart
*Manual NTSL v4.7 (14/10/2026) — p. 175*

_A função QuarterStart() recebe uma data e retorna a data correspondente ao primeiro dia do trimestre ao qual ela pertence._

**Sintaxe**

```ntsl
Função QuarterStart(Data: Integer): Integer;
```

**Parâmetros**

Data: Integer; Data base utilizada para identificar o trimestre.

**Exemplo de uso:** No exemplo abaixo, o código calcula o primeiro dia do trimestre para uma data informada e destaca o candle correspondente no gráfico.
nDate

```ntsl
var
: Integer;
nNewDate : Integer;
begin
nDate := ELDate(2025,09,01);
nNewDate := QuarterStart(nDate);
if (Date = nNewDate) then
VerticalLineCustom(clGreen, 2.5, psDash, "Inicio", 8, 0, 33, 27);
end;
```

### Função RS_BarsPerDay
*Manual NTSL v4.7 (14/10/2026) — p. 176*

_A função RS_BarsPerDay() retorna o número estimado de candles de determinada periodicidade (em minutos).
Caso o periodo seja diário, será obtido 1 como retorno, e, para períodos em minutos, ocorrerá a divisão do número total de minutos em um dia (1440) pela periodicidade selecionada._

**Sintaxe**

```ntsl
Função RS_BarsPerDay(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o retorno da chamada de função.

```ntsl
begin
Plot(RS_BarsPerDay);
end;
```

### Função Saturday
*Manual NTSL v4.7 (14/10/2026) — p. 177*

_A função Saturday() retorna o número 6, representando o dia da semana: sábado._

**Sintaxe**

```ntsl
Função Saturday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 6, referente ao dia específico da semana.

```ntsl
begin
Plot(Saturday);
end;
```

### Função Sunday
*Manual NTSL v4.7 (14/10/2026) — p. 178*

_A função Sunday() retorna o número 0, representando o dia da semana: domingo._

**Sintaxe**

```ntsl
Função Sunday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 0, referente ao dia específico da semana.

```ntsl
begin
Plot(Sunday);
end;
```

### Função Thursday
*Manual NTSL v4.7 (14/10/2026) — p. 179*

_A função Thursday() retorna o número 4, representando o dia da semana: quinta-feira._

**Sintaxe**

```ntsl
Função Thursday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 4, referente ao dia específico da semana.

```ntsl
begin
Plot(Thursday);
end;
```

### Função Time
*Manual NTSL v4.7 (14/10/2026) — p. 180*

_A função Time() possui como finalidade retornar a hora de abertura do candle atual._

**Sintaxe**

```ntsl
Função Time(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a hora de abertura do candle.

```ntsl
begin
Plot(Time);
end;
```

### Função TimeExchange
*Manual NTSL v4.7 (14/10/2026) — p. 181*

_A função TimeExchange() retorna o tempo do candle de acordo com o timezone da bolsa._

**Sintaxe**

```ntsl
Função TimeExchange(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data de acordo com o timezone da bolsa.

```ntsl
begin
Plot(TimeExchange);
end;
```

### Função TimeToMinutes
*Manual NTSL v4.7 (14/10/2026) — p. 182*

_A função TimeToMinutes() tem como propósito converter um valor de hora no formato inteiro (HHMM) para a sua representação correspondente em minutos decorridos desde 00h00._

**Sintaxe**

```ntsl
Função TimeToMinutes(XTime: Integer): Integer;
```

**Parâmetros**

XTime: Integer; Hora para a conversão.

```ntsl
No exemplo a seguir, será plotado no gráfico a conversão em minutos da hora: 12h30 (750 minutos).
begin
Plot(TimeToMinutes(1230));
end;
```

### Função Today
*Manual NTSL v4.7 (14/10/2026) — p. 183*

_A função Today() possui como finalidade retornar a data atual do sistema. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Today(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data do dia atual.

```ntsl
begin
Plot(Today);
end;
```

### Função Tuesday
*Manual NTSL v4.7 (14/10/2026) — p. 184*

_A função Tuesday() retorna o número 2, representando o dia da semana: terça-feira._

**Sintaxe**

```ntsl
Função Tuesday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 2, referente ao dia específico da semana.

```ntsl
begin
Plot(Tuesday);
end;
```

### Função VolumeD
*Manual NTSL v4.7 (14/10/2026) — p. 185*

_A função VolumeD() tem como finalidade retornar o volume financeiro de um número determinado de dias atrás._

**Sintaxe**

```ntsl
Função VolumeD(DaysAgo: Integer): Float;
```

**Parâmetros**

DaysAgo: Integer; Determina a quantidade desejada de dias anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume de 6 dias anteriores ao dia atual.

```ntsl
begin
Plot(VolumeD(6));
end;
```

### Função VolumeM
*Manual NTSL v4.7 (14/10/2026) — p. 186*

_A função VolumeM() tem como finalidade retornar o volume financeiro de um número determinado de meses atrás._

**Sintaxe**

```ntsl
Função VolumeM(MonthsAgo: Integer): Float;
```

**Parâmetros**

MonthsAgo: Integer; Determina a quantidade desejada de meses anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume do mês anterior ao atual.

```ntsl
begin
Plot(VolumeM(1));
end;
```

### Função VolumeW
*Manual NTSL v4.7 (14/10/2026) — p. 187*

_A função VolumeW() tem como finalidade retornar o volume financeiro de um número determinado de semanas atrás._

**Sintaxe**

```ntsl
Função VolumeW(WeeksAgo: Integer): Float;
```

**Parâmetros**

WeeksAgo: Integer; Determina a quantidade desejada de semanas anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o valor volume de cinco semanas anteriores à semana atual.

```ntsl
begin
Plot(VolumeW(5));
end;
```

### Função VolumeY
*Manual NTSL v4.7 (14/10/2026) — p. 188*

_A função VolumeY() tem como finalidade retornar o volume financeiro de um número determinado de anos atrás._

**Sintaxe**

```ntsl
Função VolumeY(YearsAgo: Integer): Float;
```

**Parâmetros**

YearsAgo: Integer; Determina a quantidade desejada de anos anteriores.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o volume do ano anterior ao atual.

```ntsl
begin
Plot(VolumeY(1));
end;
```

### Função Wednesday
*Manual NTSL v4.7 (14/10/2026) — p. 189*

_A função Wednesday() retorna o número 3, representando o dia da semana: quarta-feira._

**Sintaxe**

```ntsl
Função Wednesday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o número 3, referente ao dia específico da semana.

```ntsl
begin
Plot(Wednesday);
end;
```

### Função Year
*Manual NTSL v4.7 (14/10/2026) — p. 190*

_A função Year() retorna o ano de uma data específica. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Year(Date: Integer): Integer;
```

**Parâmetros**

Date: Integer; Data para obter o ano.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico o ano atual.

```ntsl
begin
Plot(Year(CurrentDate));
end;
```

### Função Yesterday
*Manual NTSL v4.7 (14/10/2026) — p. 191*

_A função Yesterday() retorna a data do dia de ontem. Datas são representadas pelo tipo de dado Integer, no formato: 1AnoMêsDia._

**Sintaxe**

```ntsl
Função Yesterday(): Integer;
```

**Parâmetros**

Sem parâmetros.

**Exemplo de uso:** No exemplo a seguir, será plotado no gráfico a data de ontem.

```ntsl
begin
Plot(Yesterday);
end;
```

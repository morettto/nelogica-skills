---
name: ntsl-calendario-e-tempo
description: Funções de data e hora do NTSL — pregão, dia útil, feriado, vencimento, semana/mês/ano, primeira e última barra do dia, OHLC de períodos maiores (OpenD/HighW/CloseM), minutos e segundos. Use quando a estratégia ou indicador depender de tempo, data, dia da semana, vencimento de opção ou de agregar por dia/semana/mês/ano.
---

# Calendário, pregão e tempo no NTSL

Fonte: Manual NTSL — Módulo Estratégias, versão 4.7, 14/10/2026, capítulo 16 (p. 118). Conteúdo verbatim em `refs/01-calendario.md`.

## Regras que não se negociam

1. **Barra ≠ dia.** `CloseD` é o fechamento do dia; `Close` é o fechamento da barra atual. Em gráfico de 5 minutos os dois são diferentes — escolher errado estraga a lógica.
2. **Dia útil só com `IsWorkingDay`** (e as `*WorkingDay*`). Comparar `DayOfWeek` com 1..5 ignora feriado e vira bug silencioso.
3. **Vencimento de opção é `DaysToExpiration` e `Next3rdFriday`**, não conta feita na mão.
4. **`TimeExchange()` devolve o tempo do candle no timezone da bolsa** — é essa que se usa para horário de pregão. `CurrentTime`/`CurrentDate` são outros (relógio do servidor) e o manual trata em tópicos separados: diga qual está usando.
5. **`Date`/`Time` são a data e o horário da barra** (não do relógio).
6. **Data é Integer no formato AnoMêsDia**, como o manual escreve: `1250416` é 16/04/2025 — o primeiro dígito não é milênio, é prefixo. Para deslocar dias use `CalcDate(RefDate, DaysChange)` (ou `CalcWorkingDate`, que pula dia não útil), nunca `data + 1`, que não é aritmética de calendário.

## Assinaturas conferidas

```ntsl
Função CalcDate(RefDate: Integer; DaysChange: Integer): Integer;
Função CalcWorkingDate(Data: Integer, Dias: Integer): Integer;
Função IsWorkingDay(Date: Integer): Boolean;
Função DayOfWeek(Date: Integer): Integer;
Função DaysToExpiration(ExpMonth: Integer; ExpYear: Integer): Integer;
Função CurrentDate(): Integer;
Função CurrentTime(): Integer;
Função TimeExchange(): Integer;
Função CalcTime(RefTime: Integer; MinuteChange: Integer): Integer;
Função Date(): Integer;
Função Time(): Integer;
Função Yesterday(): Integer;
Função Today(): Integer;
Função Month(Date: Integer): Integer;
Função Year(Date: Integer): Integer;
Função OpenD(DaysAgo: Integer): Float;
Função CloseD(DaysAgo: Integer): Float;
Função HighW(PeriodsAgo: Integer): Float;
Função LowM(MonthsAgo: Integer): Float;
```

## Funções cobertas (66)

BarAnnualization, BarDuration, BarDurationF, Bartype, CalcDate, CalcTime, CalcWorkingDate, CloseD, CloseM, CloseW, CloseY, CurrentAssetDate, CurrentDate, CurrentTime, Date, DayOfMonth, DayOfWeek, DaysToExpiration, ELDate, ELDate_Consol, FindBar, FirstWorkingDayOfMonth, FirstWorkingDayOfWeek, FirstWorkingDayOfYear, Friday, HighD, HighM, HighW, HighY, IsWorkingDay, LastCalcDate, LastCalcTime, LastDayOfMonth, LastWorkingDayOfMonth, LastWorkingDayOfWeek, LastWorkingDayOfYear, LowD, LowM, LowW, LowY, MinutesIntoWeek, Monday, Month, Next3rdFriday, OpenD, OpenM, OpenW, OpenY, QuarterEnd, QuarterStart, RS_BarsPerDay, Saturday, Sunday, Thursday, Time, TimeExchange, TimeToMinutes, Today, Tuesday, VolumeD, VolumeM, VolumeW, VolumeY, Wednesday, Year, Yesterday

## Referências

- `refs/01-calendario.md` — todas as 66 funções, com parâmetros, exemplos e página do manual

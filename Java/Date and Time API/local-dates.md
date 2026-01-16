## Local Dates

Two kinds of
human time in Java API,
*local date/time* and
*zoned time*.
___
### Local date/time

Has a
date and/or
time of day,
but no
time zone information.

Example of local date,
`June 14, 1903`,
does not correspond to
precise instant of time.
___
### Zoned date/time

`July 16, 1969, 09:32:00 EDT`
___
### `Period`

Expresses a number of
elapsed years, months, or days.

`birthday.plus(Period.ofYears(1))`
to get birthday next day.

Can also just call
`birthday.plusYears(1)`.

But
`birthday.plus(Period.ofDays(365))`
won't produce
correct result
in leap year.
___
### `datesUtil` method

Yields streams of
`LocalDate` objects.

```java
LocalDate start = LocalDate.of(2000, 1, 1);
LocalDate endExclusive = LocalDate.now();
Stream<LocalDate> allDays = start.datesUntil(endExclusive);
Stream<LocalDate> firstDaysInMonth = start.datesUntil(endExclusive, Period.ofMonths(1));
```
___
### Partial dates

`MonthDay`, `YearMonth`, and `Year`
to describe
partial dates.

Example,
December 25
can be represented
as a `MonthDay`.
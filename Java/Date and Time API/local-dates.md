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
### Construct `LocalDate`

A `LocalDate`
a date with
a year, month, and
day of the month.

```java
LocalDate today = LocalDate.now(); // Today's date
LocalDate alonzosBirthday = LocalDate.of(1903, 6, 14);
alonzosBirthday = LocalDate.of(1903, Month.JUNE, 14);
    // Uses the Month enumeration
```

Example,
256th day of the year:

```java
LocalDate programmersDay = LocalDate.of(2014, 1, 1).plusDays(255);
    // September 13, but in a leap year it would be September 12
```
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
### `until`

Yields the difference
between two
local dates.

`independenceDay.until(christmas)`,
yields
5 months and 21 days.

Not useful bcause
number of days
per month
varies.

To find
number of days:

```java
independenceDay.until(christmas, ChronoUnit.DAYS) // 174 days
```
## Custom patterns formatters

Formats a date
in the form
`Wed 1969-07-16 09:32`.

```java
formatter = DateTimeFormatter
    .ofPattern("E yyyy-MM-dd HH:mm");
```

The number of times
letter is repeated
selects a particular format.
___
### Common formatting symbols
|`ChronoField` or Purpose|Examples|
|-|-|
|`ERA`|`G: AD, GGGG: Anno Domini, GGGGG: A`|
|`YEAR_OF_ERA`|`yy: 69, yyyy: 1969`|
|`MONTH_OF_YEAR`|`M: 7, MM: 07, MMM: Jul, MMMM: July, MMMMM: J`|
|`DAY_OF_MONTH`|`d: 6, dd: 06`|
|`DAY_OF_WEEK`|`e: 3, E: Wed, EEEE: Wednesday, EEEEE: W`|
|`HOUR_OF_DAY`|`H: 9, HH: 09`|
|`CLOCK_HOUR_OF_AM_PM`|`h: 9, hh: 09`|
|`AMPM_OF_DAY`|`a: AM`|
|Period of day (since Java 16)|`B: in the evening, at night, midnight`|
|`MINUTE_OF_HOUR`|`mm: 02`|
|`SECOND_OF_MINUTE`|`ss: 00`|
|`NANO_OF_SECOND`|`nnnnnn: 000000`|
|Time zone ID|`VV: America/New_York`|
|Time zone name|`z: EDT, zzzz: Eastern Daylight Time, v: ET, vvvv: Eastern Time`|
|Zone offset|`x: -04, xx: -0400, xxx: -04:00, XXX:` same, but use `Z` for zero|

`M` = months,
`m` = minutes,
`d` = day of the month,
`D` = day of the year,
`s` = seconds,
`S` = fractions of second
`y` = normal year,
`Y` = "week-numbering year"

[Pattern symbols](https://javadoc.scijava.org/Java21/java.base/java/time/format/DateTimeFormatter.html#ofLocalizedPattern(java.lang.String))
___
### Parse

To parse a
date/time value
from a string.

Uses standard
`ISO_LOCAL_DATE` formatter:

```java
LocalDate churchsBirthday = LocalDate.parse("1903-06-14");
```

Uses custom formatter:

```java
ZonedDateTime apollo11launch =
    ZonedDateTime.parse("1969-07-16 03:32:00-0400",
        DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ssxx"));
```
___
### `ofLocalizedPattern` (Java 19)

Yields a formatter
that assembles
parts of patterns
in locale-specific way.
wtih the appropriate
separators and ordering
of the parts.

```java
ZonedDateTime apollo11launch = ZonedDateTime.of(
    1969, 7, 16, 9, 32, 0, 0,
    ZoneId.of("America/New_York"));

DateTimeFormatter formatter = DateTimeFormatter
    .ofLocalizedPattern("yMMMd");
formatter.withLocale(Locale.US)
    .format(apollo11launch) // Jul 16, 1969
formatter.withLocale(Locale.GERMANY)
    .format(apollo11launch) // 16. Juli 1969
formatter.withLocale(Locale.CHINA)
    .format(apollo11launch) // 1969年7⽉16⽇
        
DateTimeFormatter formatter = DateTimeFormatter
    .ofLocalizedPattern("yMMMEdhmsv");
formatter.withLocale(Locale.US)
    .format(apollo11launch) // Wed, Jul 16, 1969, 9:32:00 AM ET
```

Only specify symbols
for the parts,
in descending size.

For hours,
use `j` for
localized 12- or
14-hour format:

```java
formatter = DateTimeFormatter.ofLocalizedPattern("jm");
formatter.withLocale(Locale.US)
    .format(LocalTime.of(23, 59)) // 11:59 pm
formatter.withLocale(Locale.GERMANY)
    .format(LocalTime.of(23, 59)) // 23:59
```
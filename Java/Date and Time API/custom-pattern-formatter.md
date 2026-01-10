## Custom patterns formatters

Formats a date
in the form
`Wed 1969-07-16 09:32`.

```java
formatter = DateTimeFormatter.ofPattern("E yyyy-MM-dd HH:mm");
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
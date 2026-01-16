## Local Dates - `until`

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
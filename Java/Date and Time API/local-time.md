## Local Time

Represents
time of day,
such as
`15:30:00`.

```java
LocalTime rightNow = LocalTime.now();
LocalTime bedtime = LocalTime.of(22, 30);
    // or LocalTime.of(22, 30, 0)
```

Doesn't concern
with AM/PM.
It is left to
formatter.
___
### Common operations

```java
LocalTime wakeup = bedtime.plusHours(8);
    // wakeup is 6:30:00
```
___
### `LocalDateTime`

Represent
date and time.

Suitable for
storing points
in time
in a fixed time zone.

However,
if calculations
span the
daylight savings time,
or different
time zones,
use `ZonedDateTime` class.
## `Instant`

A point
in the
time line
on UTC timeline.

It starts at
Unix epoch:
`1970-01-01T00:00:00Z (UTC)`

Think of
video timeline,
entire movie = time line,
`00:10:23.456` = one precise frame.
That frame is an
`Instant`.
___
### Between two instants

Use `Duration.between`.

For example,
measure the
running time
of an algorithm.

```java
Instant start = Instant.now();
runAlgorithm();
Instant end = Instant.now();
Duration timeElapsed = Duration.between(start, end);
long millis = timeElapsed.toMillis();
```
A `Duration`
is the
amount of time.

Get the length
if a `Duration`
in conventional units:
`toNanos`, `toMillis`, `toSeconds`, `toMinutes`, `toHours` or `toDays`.
___
### Immutable

`Instant` and `Duration` classes
are immutable.

Methods, such as
`multipliedBy` or `minus`,
return a
new instance.
___
### Usage

Good for machine time:
Logging, event timestamps, auditing, DB timestamps, comparing times, measuring durations.

Not good for human time:
no timezone,
no calender concepts.
___
### Java 8

`getSeconds` instead of `toSeconds`.
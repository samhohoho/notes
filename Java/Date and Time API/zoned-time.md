## Zoned Time

Each time zone has
an ID,
such as
`America/New_York` or
`Europe/Berlin`.

`ZoneId.getAvailableZoneIds`
to get all available
time zones.
___
### Construct `ZonedDateTime`

Static method
`ZoneId.of(id)`
yields
`ZoneId` object.

`local.atZone(zoneId)`
to turn
`LocalDateTime` object
into `ZonedDateTime` object.

Or static method
`ZonedDateTime.of(year, month, day, hour, minute, second, nano, zoneId)`

Example,

```java
ZonedDateTime apollo11launch = ZonedDateTime.of(1969, 7, 16, 9, 32, 0, 0,
    ZoneId.of("America/New_York"));
    // 1969-07-16T09:32-04:00[America/New_York]
```

This is specific
instant in time.

`apollo11launch.toInstant`
to get `Instant`.

`instant.atZone(ZoneId.of("UTC"))`
to get `ZonedDateTime`
at Greenwich Royal Observatory.
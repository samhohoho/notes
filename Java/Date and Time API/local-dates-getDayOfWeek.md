## Local Dates - `getDayOfWeek`

Yields value of
`DayOfWeek` enumeration.

`DayOfWeek.MONDAY` = `1`
`DayOfWeek.SUNDAY` = `7`

```java
LocalDate.of(1900, 1, 1).getDayOfWeek().getValue()
```

`DayOfWeek` enumeration
has convenience methods
`plus` and `minus`.

`DayOfWeek.SATURDAY.plus(3)`
yields
`DayOfWeek.TUESDAY`.

Different from
`java.util.Calendar`
where Sunday
has value 1
and Saturday
value 7.
## Formatting and parsing

`DateTimeFormatter` class
provides three kinds
of formatters.
___
### Predefined standard formatters

Example:

```java
String formatted = DateTimeFormatter.ISO_OFFSET_DATE_TIME.format(apollo11launch);
    // 1969-07-16T09:32:00-04:00"
```

Intended for
machine-readable timestamps.
___
### Locale-specific formatters

To present
dates and times
to human readers.

Four styles:
`SHORT`, `MEDIUM`, `LONG`, and `FULL`.

Static methods
`ofLocalizedDate`, `ofLocalizedTime`, and `ofLocalizedDateTime`
create such formatter.

```java
DateTimeFormatter formatter = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);
String formatted = formatter.format(apollo11launch);
    // July 16, 1969 9:32:00 AM EDT
```

To change to a
different locale:

```java
formatted = formatter.withLocale(Locale.FRENCH).format(apollo11launch);
// 16 juillet 1969 09:32:00 EDT
```

|Style|Date|Time|
|-|-|-|
|`SHORT`|7/16/69|9:32 AM|
|`MEDIUM`|Jul 16, 1969|9:32:00 AM|
|`LONG`|July 16, 1969|9:32:00 AM EDT|
|`FULL`|Wednesday, July 16, 1969|9:32:00 AM EDT|
### Locale-specific formatters

To present
dates and times
to human readers.
___
### Styles

|Style|Date|Time|
|-|-|-|
|`SHORT`|7/16/69|9:32 AM|
|`MEDIUM`|Jul 16, 1969|9:32:00 AM|
|`LONG`|July 16, 1969|9:32:00 AM EDT|
|`FULL`|Wednesday, July 16, 1969|9:32:00 AM EDT|

___
### Create formatters
Static methods
`ofLocalizedDate`, `ofLocalizedTime`, and `ofLocalizedDateTime`
create such formatter.

```java
DateTimeFormatter formatter = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);
String formatted = formatter.format(apollo11launch);
    // July 16, 1969 9:32:00 AM EDT
```
___
### Different locale
To change to a
different locale:

```java
formatted = formatter.withLocale(Locale.FRENCH).format(apollo11launch);
// 16 juillet 1969 09:32:00 EDT
```
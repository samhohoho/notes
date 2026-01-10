## Predefined standard formatters

```java
String formatted = DateTimeFormatter
    .ISO_OFFSET_DATE_TIME.format(apollo11launch);
    // 1969-07-16T09:32:00-04:00"
```

Intended for
machine-readable timestamps.

|Formatter|Desc|Example|
|-|-|-|
|`BASIC_ISO_DATE`|Year, month, day, zone&nbsp;<br>offset without separators|`19690716-0400`|
|`ISO_LOCAL_DATE`,<br>`ISO_LOCAL_TIME`,<br>`ISO_LOCAL_DATE_TIME`|Separators `-`, `:`, `T`|`1969-07-16`,<br>`09:32:00`,<br> `1969-07-16T09:32:00`|
|`ISO_OFFSET_DATE`,<br>`ISO_OFFSET_TIME`,<br>`ISO_OFFSET_DATE_TIME`|Like `ISO_LOCAL_XXX`, <br>but with zone offset|`1969-07-16-04:00`,<br>`09:32:00-04:00`,<br>`1969-07-16T09:32:00-04:00`|
|`ISO_ZONED_DATE_TIME`|With zone offset and zone ID|`1969-07-16T09:32:00-`<br>`04:00[America/New_York]`|
|`ISO_INSTANT`|In UTC, denoted by the<br> `Z` zone ID|`1969-07-16T13:32:00Z`|
|`ISO_DATE`,<br>`ISO_TIME`,<br>`ISO_DATE_TIME`|Like `ISO_OFFSET_DATE`,<br>`ISO_OFFSET_TIME`, and<br>`ISO_ZONED_DATE_TIME`,<br>but the zone information is optional|`1969-07-16-04:00,09:32:00-04:00`,<br>`1969-07-16T09:32:00-04:00[America/New_York]`|
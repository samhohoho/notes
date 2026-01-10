## `DayOfWeek` enum

### `getDisplayName` method

`DayOfWeek` and `DayOfWeek` enums
have `getDisplayName`
in different
locales and formats.

```java
for (DayOfWeek w : DayOfWeek.values())
    System.out.print(w.getDisplayName(TextStyle.SHORT, Locale.ENGLISH) + " ");
    // Prints Mon Tue Wed Thu Fri Sat Sun
```
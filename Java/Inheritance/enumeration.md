## Enumeration class

**Intro**

The type defined by an `enum` declaration is a class.

Not possible to construct new objects.
Use `==` to compare them.
___
**`switch`**

```java
Size s = . . .;
String abbrev = switch (s)
    {
        case SMALL -> "S";
        . . .
    };
```
___
**Static import all**

```java
import com.horstmann.util.Size;
import static com.horstmann.util.Size.*;
. . .
Size s = SMALL;
```
___
**Abstract class `Enum`**

All enumerated types are subclasses of `Enum`.
___
**Name**

`name` method returns name of enumerated constant.

`toString()` method returns `name`
Can be overriden.

```java
Size s = Enum.valueOf(Size.class, "SMALL");
```
___
**Array**

Returns an array of all values of an enumeration.

```java
Size[] values = Size.values();
```
___
**Ordinal**

`ordinal` method yields the position
of an enumerated constant.

Counting from zero.
___
**Constructors, methods, and fields**

```java
public enum Size
{
    SMALL("S"), MEDIUM("M"), LARGE("L"), EXTRA_LARGE("XL");

    private final String abbreviation;

    Size(String abbreviation) { this.abbreviation = abbreviation; }
    // automatically private

    public String getAbbreviation() { return abbreviation; }
}
```

Constructor always private.
Can omit the private modifier.
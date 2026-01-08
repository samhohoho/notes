## Lambda expressions

**Intro**

A block of code to be passed around
and executed later.

Return type is inferred from context.
___
**Example - comparator**

Pass a `Comparator` object to `sort` method:

```java
class LengthComparator implements Comparator<String>
{
    public int compare(String first, String second)
    {
        return first.length() - second.length();
    }
}

Arrays.sort(strings, new LengthComparator());
```

Using lambda expression:

```java
(String first, String second) ->
    first.length() - second.length()
```

Or:

```java
(String first, String second) ->
    {
        if (first.length() < second.length()) return -1;
        else if (first.length() > second.length()) return 1;
        else return 0;
    }
```

Inferred:

```java
Comparator<String> comp =
    // same as (String first, String second)
    (first, second) 
        -> first.length() - second.length();
```
___
**No parameters**

```java
() -> { return 1 + (int)(Math.random() * 6); }
```
**Single parameter**

Can omit parenthesis.

Inferred type:

```java
ActionListener listener = event ->
    System.out.println("The time is " + Instant.ofEpochMilli(event.getWhen()));
```
___
**Annotations**

Use `var` to denote inferred type.

```java
(@NonNull var first, @NonNull var second) ->
    first.length() - second.length()
```
___
**Unused parameter**

Denote it with underscore:

```java
Comparator<String> comp = (_, _) -> 0;
```

A preview feature in Java 21.
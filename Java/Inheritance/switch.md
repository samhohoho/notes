## Pattern matching

**Intro**

Pattern-matching form of `switch`
simplifies the use of `instanceof`.

```java
Employee e = . . .;
String description = switch (e)
    {
        case Executive exec
            -> "An executive with a title of" + exec.getTitle();
        case Manager m
            -> "A manager who deserves a bonus";
        default -> "A lowly employee with a salary of " + e.getSalary();
    };
```

Simpler than `if` statements with `instanceof`.
___
**`null` handling**
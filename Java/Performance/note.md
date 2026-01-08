## `Supplier<T>` - lazy evaluation

**Intro**

```java
public interface Supplier<T>
{
    T get();
}
```

No parameters and yields a value of type `T`.
___
**Problem**

```java
LocalDate hireDay = Objects.requireNonNullElse(day,
    LocalDate.of(1970, 1, 1));
```

This is not optimal.

`day` is rarely `null`,
so construct default `LocalDate` when necessary.
___
**Lazy evaluation**

```java
LocalDate hireDay = Objects.requireNonNullElseGet(day,
    () -> LocalDate.of(1970, 1, 1));
```

Use supplier to defer the computation.
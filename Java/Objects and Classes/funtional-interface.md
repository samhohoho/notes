## Functional interfaces

**Intro**

An interface with a single abstract method.

Can supply a lambda expression.
___
**Behind the scene**

```java
Arrays.sort(words, (first, second)
    -> first.length() - second.length());
```

`Arrays.sort` receives an object of some class that implements `Comparator<String>`.
___
**Redeclare methods**

Some interfaces redeclare `Object` methods in order to attach javadoc comments.
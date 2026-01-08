## `try`-with-resouces statement

**Example**

```java
try (var in = new Scanner(Path.of("in.txt")))
{
    while (in.hasNext())
        System.out.println(in.next());
}
```

When `try` block
exits,
`in.close()`
is called automatically.
___
**Multiple resources**

```java
try (var in = new Scanner(Path.of("in.txt"));
    var out = new PrintWriter("out.txt"))
    {
        while (in.hasNext())
            out.println(in.next().toUpperCase());
}
```

No matter how
the block exits,
both `in` and `out`
are closed.
___
**`AutoCloseable` interface**

The resource
belong to a class
that implements
`AutoCloseable` interface.

Has a single method:

```java
void close() throws Exception
```
___
**`Closeable` interface**

A subinterface of
`AutoCloseable`,
also with
single `close` method.

That method
declared to throw
`IOException`.
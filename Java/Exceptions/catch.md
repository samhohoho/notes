## Catching exceptions

**Exception information**

`e.getMessage()`,
to get
detailed error message,
if there is one.

`e.getClass().getName()`,
to get
actual type
of exception object.
___
**Catch multiple exception types**

In the same
`catch` clause.

```java
catch (FileNotFoundException | UnknownHostException e)
{
    ...
}
```

Only needed when
catching
exception types
that are not
subclasses of one another.

Exception variable
is implicitly
`final`.
Cannot assign
different value
to `e`
in the body.

Make your code
look simpler
and
more efficient.
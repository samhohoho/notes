## Rethrowing and chaining exceptions

Throw an exception
in `catch` clause.

Typically,
do this when
change the
exception type.
___
**Example**

If build a subsystem
that other programmer use,
makes sense to
use exception type
of the subsystem.

```java
try
{
    // access the database
}
catch (SQLException e)
{
    throw new ServletException("database error: " + e.getMessage());
}
```

It is a better idea
to set the
original exception
as the "cause"
of the
new exception:

```java
try
{
    // access the database
}
    catch (SQLException original)
{
    var e = new ServletException("database error", original);
    throw e;
}
```
___
**`initCause()`**

`ServletException` class
has a constructor
you can pass
the cause.

if an exception type
is not the case:

```java
e.initCause(original);
```

When caught,
original exception
can be retrieved:

```java
Throwable original = caughtException.getCause();
```

Recommended.
Allows to throw
high-level exceptions
in subsystems
without losing
the original failure.
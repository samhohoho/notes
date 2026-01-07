## Stack trace elements

A listing of
pending method calls.
___
**printStackTrace**

Access the
text description
of a stack trace,
`printStackTrace` method
of `Throwable` class.

```java
var t = new Throwable();
var out = new StringWriter();
t.printStackTrace(new PrintWriter(out));
String description = out.toString();
```
___
**`StackWAlker`**

A class that
yields a stream of
`StackWalker.StackFrame` instances,
each describing
one stack frame.

Iterate over
stack frames:

```java
StackWalker walker = StackWalker.getInstance();
walker.forEach(frame -> analyze frame)
```

To process 
`Stream<StackWalker.StackFrame>`
lazily:

```java
walker.walk(stream -> process stream)
```
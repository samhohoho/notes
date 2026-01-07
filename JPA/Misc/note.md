## Process-scoped identity

**Persistence context-scoped identity**

For enterprise application,
persistence context-scoped identity is preferred.

Simpler and more scalable.

Each thread work with a copy of data.
___
**Process-scoped identity**

One in-memory instance in entire process (JVM).

Cost of always synchronizing shared access
in a global identity map
is too high,
in multithreaded application.
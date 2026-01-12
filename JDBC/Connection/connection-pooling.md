## Connection pooling

Opening and closing
DB connections,
very expensive operation.
___
### Advantages

Avoids both
DB and driver
overhead
for establishing
TCP connection.

Prevents destroying
temporary memory buffers.

Reduce client-side
JVM object garbage.
___
### Mechanism

1
When connection
is being requested,
pool looks for
unallocated connections.

2
If finds free one,
to client.

3
If no free,
pool will grow
to its maximum
allowed size.

4
If already reached
maximum size,
retry several times
before giving up with
connection acquisition
failure exception.

5
When client closes
the logical connection,
connection returns to
the pool
without closing
underlying physical connection.
___
### DataSource

Most connection pooling
expose a
`DataSource` implementation
that either wraps
an actual database-specific `DataSource`
or
underlying `DriverManager` utility.
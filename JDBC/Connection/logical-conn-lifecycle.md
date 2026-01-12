## Logical connection lifecycle

### Reduce connection acquisition time

Connection pool
does not return
physical connection
to client,
instead
it offers a
proxy or a handle.

Pool changes
its state
to *allocated*
to prevent
two concurrent threads
from using
same DB connection.

Proxy intercepts
connection close
method call,
notifies pool
to change
connection state
to *unallocated*.
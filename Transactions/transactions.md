## Transactions

Shared data
means
read and write operations
must be
synchronized
to ensure
data integrity
is not compromised.
___
### Java `synchronized` keyword

To control
concurrent modifications:

1
It restricts
access
to shared object,
only a
single `Thread`
can execute
a routine
at any given time.

2
It propagates changes
from
current `Thread`
local memory
to
global memory.

Database systems
are no different.
___
### As a unit

A transaction
is a
collection of
read and write operations
either
succeed or fail
together,
as a unit.

All DB statements
must execute
within a
transactional context.
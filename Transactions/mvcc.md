## Multi-version concurrency control (MVCC)

### Locking shortcomings

Although
locking provide
serializable transaction schedule,
the cost of
lock contention
can undermine
both transaction
response time
and
scalability.

Response time increase
because
transactions
must wait for
locks
to be released.

Long-running transactions
slow down
progress of other
concurrent transactions.
___
### Using MVCC

DB vendors
have opted for
optimistic concurrency control
mechanism.

2PL
prevents conflicts,
MVCC
uses
conflict detection strategy.
___
### The promise of MVCC

Readers
do not block
writers.

Writers
do not block
readers.

The only
source of contention,
writers
blocking other
concurrent writers,
which otherwise
compromise transaction
rollback and atomicity.
___
### To prevent blocking

DB
rebuild
previous versions of
DB record
so
an uncommitted change
hidden away from
incoming concurrent readers.
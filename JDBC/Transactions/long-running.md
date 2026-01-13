## Long-running transaction

Processing
too much data
in single transaction,
degrade app performance,
especially in
highly concurrent environment.

Whether using
2PL (Two-Phase Locking) or
MVCC (Multiversion Concurrency Control),
writers always
block other
conflicting writers.

More practical to
break a
large batch processing task
into
smaller ones,
release locks
in a timely fashion.
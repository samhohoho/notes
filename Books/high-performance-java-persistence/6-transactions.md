# 5

## 6.3.1.1 Two-phase locking...

deadlocks

Transaction schedule
...cascading aborts 

2PL protocol defines a lock management strategy 

Locks alone are not sufficient for preventing conflicts

Locking on lower levels
...lock escalation

Database objects are hierarchical in nature

relational database
systems use Multiple granularity locking3.

SQL Server still uses locking 

many vendors have moved towards an MVCC 

## 6.3 isolation

isolation level that does not
compromise data integrity 

transaction
operations is said to be serializable

parallelization imposes addi-
tional challenges 

Universal Scalability Law

## 6.2 consistency

Consistency as in CAP Theorem

## 6.1 atomicity

Postgres
VACUUMING
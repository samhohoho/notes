## Atomicity

Grouping
multiple operations
into
all-or-nothing
unit of work.
___
### Write-write conflicts

Ideally,
every transaction
have
isolated branch
easily discarded
in case of
rollback.

Similar to
Version Control System (git)
implements branching.

In conflicts,
VCS aborts
commit operation,
and
client manually
resolve conflict.

Unlike VCS,
DB engine
must
manage conflicts
without
human intervention.

For this reason,
DB prevents
write-write conflict,
only one
transaction
can write a record
at any given time.
## Persistence context

**Intro**

It captures entity state changes.

During flushing,
translate them into SQL statements.

Cannot be shared
by multiple concurrent transactions.
___
**Write-behind cache**
Act as a transactional write-behind cache.

Deferring flushing until last moment.
___
**First-level cache**

It remembers all entity instances handled in a particular unit of work.

To load an entity using PK,
Hibernate first check the PC.

If found, no DB hit occurs,
repeatable read.
___
**Lifetime**

Bound to that logical transaction.
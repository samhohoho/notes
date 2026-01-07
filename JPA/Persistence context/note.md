## Arbitrary queries

**Intro**

This cache also affects
the results of arbitrary queries.

Such as `javax.persistence.Query` API.

Hibernate reads the SQL result set
and transforms it
into entity instances.

First tries to resolve
every entity
in the PC
by identifier lookup.

If can't be found,
read the rest of the data
from the result-set row.
(How does hibernate deal with outdated data?)
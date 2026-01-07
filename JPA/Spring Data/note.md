## Spring Data JDBC

**Intro**

A simpler and
more limited
ORM.
However,
it is introducing
new features.

Does not offer
all JPA capabilities,
such as,
caching or lazy loading.

Uses
entities,
repositories, and
`@Query` annotations.

Does not use
JPQL and
no portability.

Queries
must be written in
plain SQL.

Entity loading
done through
SQL queries.

Sessions and
dirty tracking
do not exist.

At the time of writing,
does not support
schema generation.
we can
declare entities,
but
DDL commands
need to be written.
___
**Why we need it**

Object/relational mapping (ORM)
makes projects
complex.

There are situations
to eliminate
this complexity
and take the
benefits of working
with Spring.

Old-style JDBC,
shortcomings, such as
opening and closing
connections
or manually handling
exceptions.

Spring Data JDBC
allows
create our own
queries,
has its own
ORM.
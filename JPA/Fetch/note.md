## Prefetching data in batches

**Intro**

With lazy loading,
many additional
SQL `SELECT`
may be needed.

If hibernate must
initialize
one proxy,
go ahead and
initialize several
with same `SELECT`.

Instead of
`n+1` SQL queries,
we will have
reduction in queries.
___
**Blind-guess optimization**

Reasonable values
are usually
small
because don't want
to load
too much data,
if aren't sure.
___
**Memory is cheap**

Batch fetching
reduce number of
SQL statements.

Although we may
prefetch data
we won't need,
and consume
more memory,
reduction in
DB round trips
make a huge difference.

Memory is cheap,
but scaling
DB servers
isn't.
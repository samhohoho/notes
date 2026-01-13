## Statement lifecycle

The main DB modules
for processing
a SQL statement
are
Parser, Optimizer,
and Executor.
___
### Parser

Checks SQL statement
and validity.
Both syntactically and
semantically.

SQL statement is
transformed into
DB-internal representation,
called *syntax tree*.
___
### Optimizer

Given syntax tree,
decide most efficient
data fetching algorithm.

Evaluate multiple
data traversing options:

1
Table scan or
index scan.

2
Which index
is better.

3
Choose the
best-performing
join type
(e.g. Nested loop joins, Hash Joins, Sort Merge Joins).

4
Joining order.

#### Access path

Data is retrieved
by following
an *access path*.

The list of access path,
is assembled
into execution plan.
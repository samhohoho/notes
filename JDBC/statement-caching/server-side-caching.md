## Server-side statement caching

Statement parsing and
execution plan generation
are resource intensive operations.

Some DB providers
offer execution plan
cache.

Statement string value
is used
as input
to hashing function,
the resulting value
becomes the
execution plan cache
entry key.

If statement string value
changes to other,
DB cannot reuse
already generated
execution plan.

Dynamic generated
JDBC `Statement`
not suitable
for reusing
execution plans.
___
### PreparedStatement

Server-side
prepared statements
allow to reuse
same execution plan
for multiple executions.

A `PreparedStatement`
always associated with
a single
SQL statement,
bind parameters
are used to vary
runtime execution context.

`PreparedStatement`
take SQL query
at creation time,
DB precompile
SQL statement.

During precompilation,
validates and
parse it into
a syntax tree.

When executing
`PreparedStatement`,
driver sends
actual parameter values,
compile and run
actual execution plan.
___
### Roundtrips

Prepare and execution
phases
happen in
separate database roundtrips.

Some DB
optimize this process,
multiplexing two phases
into a single
database roundtrip.
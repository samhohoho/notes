## Consistency

It is about
validating
transaction state change.

If only
one constraint
gets violated,
entire transaction
will be
rolled back.

Although
application must validate
user input
prior to
crafting
DB statements,
application-level checks
cannot
span over other
concurrent requests,
possibly
coming from
different
web servers.
___
### Rules

- Column types
- Column length
- Column nullability
- Foreign key constraints
- Unique key constraints
- Custom check constraints
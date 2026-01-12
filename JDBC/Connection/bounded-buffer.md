## Bounded buffer

Connection pool
can also
limit
number of connections
an app can use
at once.

Think of pool
as a waiting room.

It act as a
bounded buffer.

If traffic spike,
level it,
instead of
saturating all
available DB resources.

DB only ever see
10 steady connections,
even though
50 people are waiting.
___
### System overloading

Two options
to avoid
system overloading:

1
Queuing requests,
increasing
response time.

2
Discarding
overflowing traffic,
affecting availability.

Connection pooling
first attempt
to enqueue
overflowing requests.

Discarding
surplus traffic
is a last resort measure.
___
### Wait time

Putting an
upper bound on
connection request
wait time,
queue is
prevented from
growing indefinitely
and saturating
application server resources.
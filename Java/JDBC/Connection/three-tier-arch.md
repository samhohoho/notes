## Three-tier architecture

In enterprise application,
user request throughput
greater than
available DB
connection capacity.

As long as
connection acquisition time
is tolerable,
user request
can wait for
DB connection
to become available.
___
### Middle layer
The middle layer
acts as a
DB connection buffer,
mitigate
user request traffic spike
by increasing
request response time,
without
depleting DB connections
or
discarding incoming traffic.

Can also
monitor
connection usage
and
provide statistics.
___
### Logical connections

Instead of
serving
physical DB connections,
provides only
logical connections (proxies/handlers),
so it can
intercept and register
how client API
interacts with
connection object.
# 5

## 5.5.2 Too many columns

more prevalent among ORM tools

## 5.5.1.3 Less is more

Fetching a large result set puts much pressure on database resources

maxRows driver implementation yields a
surprisingly good result

either by using
SQL or the JDBC maxRows setting

limiting the
result set size

## 5.5.1.2 JDBC max rows

dropping extra rows is a poor strategy

portable across all driver implementations.

statement.setMaxRows(maxRows);

## 5.5.1 Too many rows

LIMIT keyword

only hints the database engine to use a database cursor

batch processor divides the current workload

pressure on the database undo/redo logs

## 5.4 Fetching size

statement.setFetchSize(fetchSize);

## 5.2 ResultSet changeability

updatable result set is of
little use,...

Mixing reading and writing logic into a single database transaction...

## 5.1 scrollability

application-level cursor

JDBC resultset properties.

## 5...
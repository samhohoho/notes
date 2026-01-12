## DataSource interface

If `DriverManager` is
physical connection factory,
`javax.sql.DataSource` interface is
logical connection provider.

```java
Connection getConnection() throws SQLException;
Connection getConnection(String username, String password) throws SQLException;
```

Simplest `DataSource` implementation
delegate
connection acquisition request
to underlying
`DriverManager`.
___
### Connection request workflow (without connection pooling)

1
Application data layer
asks `DataSource`
for a
DB connection.

2
`DataSource` uses
underlying driver to
open a
physical connection.

3
A physical connection
is created,
TCP socket is opened.

4
`DataSource`
lends to
application layer.

5
Application executes
statements
using acquired
DB connection.

6
When connection
is no longer needed,
application closes
physical connection
along with
underlying TCP socket.
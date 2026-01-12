## DriverManager

To communicate with DB server,
obtain a
`java.sql.Connection`.

`java.sql.Driver`
actual DB connection
provider.

`java.sql.DriverManager`
resolve JDBC driver
associated with
current DB
connection URL.
___
### Methods

```java
public static Connection getConnection(
    String url, Properties info) throws SQLException;

public static Connection getConnection(
    String url, String user, String password) throws SQLException;

public static Connection getConnection(
    String url) throws SQLException;
```

When `getConnection()`,
`DriverManager` requests a
new physical connection
from the underlying
`Driver`.
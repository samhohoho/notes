## Batching PreparedStatements

### JDBC `Statement`

For parameterized statements,
JDBC `Statement`
poor fit
because
executing SQL statement
is through
`String` manipulation.

Vulnerable to
SQL injection attacks.
___

### JDBC `PreparedStatement` interface

For binding parameters
in a safe manner.

Because a `PreparedStatement`
is associated with a
single DML statement,
batch update
group multiple
parameter values
belonging to
same prepared statement.

```java
PreparedStatement postStatement = connection.prepareStatement(
    "INSERT INTO post (title, version, id) " +
    "VALUES (?, ?, ?)");

postStatement.setString(1, String.format("Post no. %1$d", 1));
postStatement.setInt(2, 0);
postStatement.setLong(3, 1);
postStatement.addBatch();

postStatement.setString(1, String.format("Post no. %1$d", 2));
postStatement.setInt(2, 0);
postStatement.setLong(3, 2);
postStatement.addBatch();

int[] updateCounts = postStatement.executeBatch();
```
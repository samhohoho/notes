## Sequences

As opposed to
identity columns,
DB sequences
decouple
identifier generation
from
actual row insert.
___
### Batch inserts

To batch inserts,
identifier
must be fetched
prior to
setting statement
parameter values.

```java
private long getNextSequenceValue(Connection connection)
    throws SQLException {
    try(Statement statement = connection.createStatement()) {
        try(ResultSet resultSet = statement.executeQuery(
            callSequenceSyntax())) {
            resultSet.next();
            return resultSet.getLong(1);
        }
    }
}
```

```java
try(PreparedStatement postStatement = connection.prepareStatement(
    "INSERT INTO post (id, title, version) VALUES (?, ?, ?)")) {
    for (int i = 0; i < postCount; i++) {
        if(i > 0 && i % batchSize == 0) {
            postStatement.executeBatch();
        }
        postStatement.setLong(1, getNextSequenceValue(connection));
        postStatement.setString(2, String.format("Post no. %1$d", i));
        postStatement.setInt(3, 0);
        postStatement.addBatch();
    }
    postStatement.executeBatch();
}
```
___
### Syntax

Every DB offers
a specific syntax.

PostgreSQL:

```sql
SELECT NEXTVAL('post_seq');
```
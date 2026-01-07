## Implementing Hibernate interceptors

**Create marker interface**

```java
public interface Auditable {
    Long getId();
}
```

This interface
requires that
a persistent entity class
exposes
its identifier
with a
getter;
to log with
audit trail.
___
**Enabling audit logging for a persistent class**

```java
@Entity
public class Item implements Auditable {
    // . . .
}
```
___
**Audit database table**

```java
@Entity
public class AuditLogRecord {
    @Id
    @GeneratedValue(generator = Constants.ID_GENERATOR)
    private Long id;
    @NotNull
    private String message;
    @NotNull
    private Long entityId;
    @NotNull
    private Class<? extends Auditable> entityClass;
    @NotNull
    private Long userId;
    @NotNull
    private LocalDateTime createdOn = LocalDateTime.now();
    // . . .
}
```

To store
an instance of
`AuditLogRecord`
whenever
Hibernate inserts/updates
an `Item`
in DB.

A Hibernate interceptor
can handle this
automatically.
___
**`EmptyInterceptor`**

Instead of
implementing all
methods
in `org.hibernate.Interceptor`,
extend
the `EmptyInterceptor`
and override
only
the methods
we need.

To access
the DB
to write
the audit log,
the interceptor
needs a
Hibernate `Session`.

The `inserts` and `updates`
instance variables
will be
collections
where
interceptor hold
its internal state.

```java
public class AuditLogInterceptor extends EmptyInterceptor {
    private Session currentSession;
    private Long currentUserId;
    private Set<Auditable> inserts = new HashSet<>();
    private Set<Auditable> updates = new HashSet<>();
    public void setCurrentSession(Session session) {
        this.currentSession = session;
    }
    public void setCurrentUserId(Long currentUserId) {
        this.currentUserId = currentUserId;
    }
    public boolean onSave(Object entity, Serializable id,
                        Object[] state, String[] propertyNames,
                        Type[] types)
        throws CallbackException {
        if (entity instanceof Auditable aud) {
            inserts.add(aud);
        }
        return false;
    }
    public boolean onFlushDirty(Object entity, Serializable id,
                        Object[] currentState,
                        Object[] previousState,
                        String[] propertyNames, Type[] types)
        throws CallbackException {
        if (entity instanceof Auditable aud) {
            updates.add(aud);
        }
        return false;
    }
    // . . .
}
```
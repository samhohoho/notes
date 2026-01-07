## Replicating data

**Intro**

Useful when
retrieve data from one DB
and store it in another.

Replication takes
detached instances
loaded in one PC
and makes them persistent
in another PC.

Open these PCs
from two different
`EntityManagerFactory` configurations,
enabling two logical DBs.

`replication()`
only available on
Hibernate Session API.
___
**Example**

```java
EntityManager emA =
    getDatabaseA().createEntityManager();
emA.getTransaction().begin();
Item item = emA.find(Item.class, ITEM_ID);
emA.getTransaction().commit();

EntityManager emB =
    getDatabaseB().createEntityManager();
emB.getTransaction().begin();
emB.unwrap(Session.class)
   .replicate(item, org.hibernate.ReplicationMode.LATEST_VERSION);
Item item1 = emB.find(Item.class, ITEM_ID);
assertEquals("Some Item", item1.getName());
emB.getTransaction().commit();

emA.close();
emB.close();
```
___
**Replication mode**

`IGNORE`:
Ignores the instance
when existing
with same identifier.

`OVERWRITE`:
Overwrites existing.

`EXCEPTION`:
Throws when existing.

`LATEST_VERSION`:
Overwrites if
version is older,
or ignores.
Requires
optimistic concurrency
with entity versioning.
___
**Use case**

Product upgrade.

The new version of app
requires a new DB (schema),
migrate and replicate
the existing data.
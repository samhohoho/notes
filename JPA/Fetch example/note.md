## Prefetching data in batches example

**Intro**

This require
one `SELECT`
to get all `Item`
and `n` more `SELECT`s
for `seller`.
___
**Setup**
```java
@Entity
@org.hibernate.annotations.BatchSize(size = 10)
@Table(name = "USERS")
public class User {
    // . . .
}
```

Tells hibernate to
load up to 10
`User` proxies
if one
has to be loaded.
___
**Example**

```java
List<Item> items = em.createQuery("select i from Item i",
    Item.class).getResultList();
// select * from ITEM
for (Item item : items) {
    assertNotNull(item.getSeller().getUsername());
    // select * from USERS where ID in (?, ?, ?, ?, ?, ?, ?, ?, ?, ?)
}
```

`item.getSeller().getUserName()`
for the first time,
initializes/retrieves
up to 10
`User` instances.

Once access the
eleventh `seller`,
another 10
loaded in
one batch,
until
PC contains
no uninitialized
`User` proxies.
___
**Batch fetching for collections**

```java
@Entity
public class Item {
    @OneToMany(mappedBy = "item")
    @org.hibernate.annotations.BatchSize(size = 5)
    private Set<Bid> bids = new HashSet<>();
    // . . .
}
```

If initialize
one `bids` collection,
up to five more
`Item#bids` collections,
if uninitialized
in current PC,
are loaded.

```java
List<Item> items = em.createQuery("select i from Item i",
    Item.class).getResultList();
// select * from ITEM
for (Item item : items) {
    assertTrue(item.getBids().size() > 0);
    // select * from BID where ITEM_ID in (?, ?, ?, ?, ?)
}
```

`item.getBids().size()`
the first time,
a batch of
`Bid` collections
are preloaded
for other
`Item` instances.
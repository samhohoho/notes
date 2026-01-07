## Generifying a JPA application

**`GenericDao` interface**

```java
public interface GenericDao<T> {
    T getById(long id);
    List<T> getAll();
    void insert(T entity);
    void delete(T entity);
    void update(long id, String propertyName, Object propertyValue);
    List<T> findByProperty(String propertyName, Object propertyValue);
}
```
___
**`AbstractGenericDao` class**

```java
@Repository
@Transactional
public abstract class AbstractGenericDao<T> implements GenericDao<T> {
    @PersistenceContext(type = PersistenceContextType.EXTENDED)
    protected EntityManager em;
    private Class<T> clazz;
    public void setClazz(Class<T> clazz) {
        this.clazz = clazz;
    }
    @Override
    public T getById(long id) {
        return em.createQuery(
        "SELECT e FROM " + clazz.getName() + " e WHERE e.id = :id",
        clazz)
            .setParameter("id", id).getSingleResult();
    }
    @Override
    public List<T> getAll() {
        return em.createQuery("from " +
        clazz.getName(), clazz).getResultList();
    }
    @Override
    public void insert(T entity) {
        em.persist(entity);
    }
    @Override
    public void delete(T entity) {
        em.remove(entity);
    }
    @Override
    public void update(long id, String propertyName, Object propertyValue) {
        em.createQuery("UPDATE " + clazz.getName() + " e SET e." +
        propertyName + " = :propertyValue WHERE e.id = :id")
            .setParameter("propertyValue", propertyValue)
            .setParameter("id", id).executeUpdate();
    }
    @Override
    public List<T> findByProperty(String propertyName,
    Object propertyValue) {
        return em.createQuery(
            "SELECT e FROM " + clazz.getName() + " e WHERE e." +
            propertyName + " = :propertyValue", clazz)
                .setParameter("propertyValue", propertyValue)
                .getResultList();
    }
}
```

`clazz`
is the effective
`Class` field
DAO will work.
___
**`ItemDaoImpl` class**

```java
public class ItemDaoImpl extends AbstractGenericDao<Item> {
    public ItemDaoImpl() {
        setClazz(Item.class);
    }
    @Override
    public void insert(Item item) {
        em.persist(item);
        for (Bid bid : item.getBids()) {
            em.persist(bid);
        }
    }
    @Override
    public void delete(Item item) {
        for (Bid bid: item.getBids()) {
            em.remove(bid);
        }
        em.remove(item);
    }
}
```
___
**`BidDaoImpl` class**

```java
public class BidDaoImpl extends AbstractGenericDao<Bid> {
    public BidDaoImpl() {
        setClazz(Bid.class);
    }
}
```
___
**`SpringConfiguration` class**

```java
@Bean
public GenericDao<Item> itemDao() {
    return new ItemDaoImpl();
}
@Bean
public GenericDao<Bid> bidDao() {
    return new BidDaoImpl();
}
```
___
**`SpringJpaTest` class**

```java
@Autowired
private GenericDao<Item> itemDao;

@Autowired
private GenericDao<Bid> bidDao;
```
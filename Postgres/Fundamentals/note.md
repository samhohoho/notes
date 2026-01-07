## *Check* constraint

**Intro**

Verifies the
column value
satisfies
a custom condition.
___
**Example**

```sql
CREATE TABLE products.catalog (
    ...
    category TEXT CHECK (category IN ('coffee', 'mug', 't-shirt')),
    stock_quantity INT CHECK (stock_quantity >= 0)
    ...
);
```
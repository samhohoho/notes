## Bulk processing

Bulk update/delete statements
can benefit from
indexing.

```sql
UPDATE post SET version = version + 1;
UPDATE post_comment SET version = version + 1;
```
___
### Batch update

Bulk is faster.

However,
batch updates
can benefit from
application-level
optimistic locking mechanisms,
suitable for
preventing
*lost updates*.
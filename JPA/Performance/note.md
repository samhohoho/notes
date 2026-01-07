## `OutOfMemoryError`

**Problem**

Hibernate creates snapshot of each instance,
can lead to memory exhaustion.
___
**Solutions**

`EntityManager#detach(i)`
to evict a persistent instance.

`EntityManager#clear()`
to detach all persistent entity instances
and empty persistence context.

Set persistence context to read-only mode.
To disables state snapshots and dirty checking.
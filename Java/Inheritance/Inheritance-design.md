## Inheritance design

**superclass**

Place common operations and fields in superclass,
instead of replicating it.
___
**`protected` fields**

Doesn't give much protection/

Subclasses is unbounded,
anyone can directly access the fields.

All same package classes can access.

But `protected` methods useful for subclasses to redefine.
___
## `HashSet`

`HashSet` class
implements
a set
based on
a hash table.
___
**`contains`**

Checks only in
one bucket
and not
all elements
in the collection.
___
**Iterator**

Visits
all buckets
in a random order.
___
**Mutating set element**

When mutate set elements,
hash code change,
element no longer
in the
correct position.

```java
var rects = new HashSet<Rectangle>();
var rect = new Rectangle(5, 10, 20, 30);
rects.add(rect);
rect.setLocation(0, 0);
// rects is now [java.awt.Rectangle[x=0,y=0,width=20,height=30]]
```
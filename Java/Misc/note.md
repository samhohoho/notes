## `Arrays.sort` - clumsy cast

**Clumsy cast**

`Arrays.sort` method accepts an `Object[]` array and uses a cast.

```java
// approach used in the standard library--not recommended
if (((Comparable) a[i]).compareTo(a[j]) > 0)
{
    // rearrange a[i] and a[j]
    . . .
}
```

If `a[i]` does not belong to a class that implements `Comparable`,
virtual machine throws an exception.
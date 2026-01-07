## Object wrappers

**Intro**

Wrapper classes are immutable.

They are `final`, cannot subclass.

Can be `null`.

Convenient to put basic methods,
such as `Integer.parseInt(s)`.
___
**`Number`**

`Integer`, `Long`, `Float`, `Double`, `Short`, and `Byte`
inherits from superclass `Number`.
___
**`ArrayList<Integer>`**

`ArrayList<Integer>` is less efficient than `int[]`.

Because each value is wrapped inside an object.

Only good for small collections.
___
**Autoboxing & unboxing**

`list.add(3);`
is automatically translated to
`list.add(Integer.valueOf(3));`

`int n = list.get(i);`
into
`int n = list.get(i).intValue();`

Compiler inserts calls when generates bytecodes.
Virtual machine executes those bytecodes.
___
**Autoboxing & unboxing arithmetic expressions**

```java
Integer n = 3;
n++;
```

Compiler unbox, increment the value, and box it.

```java
Integer n = 1;
Double x = 2.0;
System.out.println(true ? n : x); // prints 1.0
```

`Integer` is unboxed, promoted to `double`,
and boxed into `Double`.
___
**`==` operator**

To wrapper objects,
only test identical memory locations.
___
**Immutable**

```java
// won't work
public static void triple(Integer x)
{
    . . .
}
```

`Integer` objects are immutable.

Information inside wrapper can't be changed.
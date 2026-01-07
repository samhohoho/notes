## Interfaces

**Intro**

Not a class but a set of requirements.

Describe what classes should do,
without specifying how to do it.

A class can implement more than one interfaces.

All methods automatically `public`.

Can define constants.

Never have instance fields.
___
**Why**

Why can't the `Employee` class provide a `compareTo`
without implementing `Comparable` interface?

Reason is that Java is strongly typed.

Compiler needs to be able to check that the method exists.

If it is an array of `Comparable` objects,
then the existence of the method is assured.

Every class that implements `Comparable` must supply the method.
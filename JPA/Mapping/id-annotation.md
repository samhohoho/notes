## `@Id`

Every entity class
has to have an
`@Id` property;
it's how
JPA
exposes
database identity
to the application.

If specify
nothing else,
this property
maps to
a primary key column
named `ID`.
___
### Field access

Hibernate and Spring Data Jpa
use field
to access
identifier property value
when
loading and storingm
not
getter/setter.

Field access
is better
because
more freedom
for
accessor method design.
___
### Persistent property

Beacause `@Id`
is on
a field,
Hibernate
enable
every field
as persistent property
by default.
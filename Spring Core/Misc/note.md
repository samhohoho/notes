## `@Qualifier`

Spring
needs to
inject a value
but has
multiple beans
of same type.
___
**Matching bean name**

```java
@Configuration
public class ProjectConfig {
    @Bean
    public Parrot parrot1() {
        Parrot p = new Parrot();
        p.setName("Koko");
        return p;
    }
    @Bean
    public Parrot parrot2() {
        Parrot p = new Parrot();
        p.setName("Miki");
        return p;
    }
    @Bean
    public Person person(Parrot parrot2) {
        Person p = new Person();
        p.setName("Ella");
        p.setParrot(parrot2);
        return p;
    }
}
```

If multiple beans
of same type
are available,
Spring choose bean
with same
parameter name.
___
**Using `@Qualifier`**

Prefer to
avoid
name of the parameter,
easily refactored
and
changed by mistake.

```java
@Configuration
public class ProjectConfig {
    @Bean
    public Parrot parrot1() {
        Parrot p = new Parrot();
        p.setName("Koko");
        return p;
    }
    @Bean
    public Parrot parrot2() {
        Parrot p = new Parrot();
        p.setName("Miki");
        return p;
    }
    @Bean
    public Person person(
        @Qualifier("parrot2") Parrot parrot) {
        
        Person p = new Person();
        p.setName("Ella");
        p.setParrot(parrot);
        return p;
    }
}
```
## `@SpringBootApplication`

```java
package tacos;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class TacoCloudApplication {
    public static void main(String[] args) {
        SpringApplication.run(TacoCloudApplication.class, args);
    }
}
```

A composite annotation
combines
following three
annotations.
___
**`@SpringBootConfiguration`**

Designates this class
as configuration class.

A specialized form of
`@Configuration` annotation.
___
**`@EnableAutoConfiguration`**

Enables
Spring Boot
automatic configuration.
___
**`@ComponentScan`**

Lets you
declare classes
with annotations
`@Component`,
`@Controller`,
and `@Service`
to have Spring
automatically discover
and register them
as components
in AC.
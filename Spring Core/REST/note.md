## Controller advice

An aspect
that intercepts
exceptions
thrown by
controller's actions
and applies
custom logic
you define.
___
**REST controller advice**

```java
@RestControllerAdvice
public class ExceptionControllerAdvice {
    @ExceptionHandler(NotEnoughMoneyException.class)
    public ResponseEntity<ErrorDetails> exceptionNotEnoughMoneyHandler() {
        ErrorDetails errorDetails = new ErrorDetails();
        errorDetails.setMessage("Not enough money to make the payment.");
        return ResponseEntity
            .badRequest()
            .body(errorDetails);
    }
}
```
`ExceptionControllerAdvice` class
is a
REST controller advice.

The method
an exception handler.
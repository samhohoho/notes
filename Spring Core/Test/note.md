## Test return value

**Example**

```java
@PostMapping("/")
public String loginPost(
    @RequestParam String username,
    @RequestParam String password,
    Model model
) {
    loginProcessor.setUsername(username);
    loginProcessor.setPassword(password);
    boolean loggedIn = loginProcessor.login();

    if (loggedIn) {
        model.addAttribute("message", "You are now logged in.");
    } else {
        model.addAttribute("message", "Login failed!");
    }

    return "login.html";
}
```

```java
@ExtendWith(MockitoExtension.class)
class LoginControllerUnitTests {
    @Mock
    private Model model;
    @Mock
    private LoginProcessor loginProcessor;
    @InjectMocks
    private LoginController loginController;

    @Test
    public void loginPostLoginSucceedsTest() {
        given(loginProcessor.login())
            .willReturn(true);

        String result =
            loginController.loginPost("username", "password", model);

        assertEquals("login.html", result);

        verify(model)
            .addAttribute("message", "You are now logged in.");
    }
    
    @Test
    public void loginPostLoginFailsTest() {
        given(loginProcessor.login())
            .willReturn(false);

        String result =
            loginController.loginPost("username", "password", model);

        assertEquals("login.html", result);

        verify(model)
            .addAttribute("message", "Login failed!");
    }
}
```
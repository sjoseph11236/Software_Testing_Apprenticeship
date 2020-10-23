# MVC MOCKITO 🍹

Create a Spring Boot Application with a focus on TDD and mocking. This project will be full CRUD with RESTful endpoints. For this application we would ask of you the following:

- Have the following dependencies:
  - Mockito (Spring Boot Projects should have this by default)
  - JUnit 5 (Spring Boot Projects should have this by default)
  - Spring Web
  - Spring Data JPA
  - H2
- Have five models with all appropiate methods/fields to make it a POJO. Every model should have service implementations and controller implementations.
- Write your tests first before writing your implementation. Mock a service interface that will be implemented by a concrete service class.
- You can directly target any class that relies on the service as a dependency for your tests. Try to test your controllers for example.
- Attempt a test for every method you intend to implement. 

## Notes

This project is somewhat open-ended. Try to think critically about what you would need to implement and mock accordingly. I did not show the class a clean way of implementing Mockito with Spring so here are examples of what I would want to see:

<!-- Service -->
Here is my Service Interface. This is where I am defining my methods:

```Java
public interface TempService {

    Number add(Number x, Number y);
    String sayHi();

}
```

<!-- ServiceImpl -->
Now take a look at my implementation. Note that in this scenario, I am using the keyword *implements*:

```Java

@Service
public class TempServiceImpl implements TempService {

    @Override
    public Number add(Number x, Number y) {
        return x.doubleValue() + y.doubleValue();
    }

    @Override
    public String sayHi() {
        return "hello world";
    }
}
```
<!-- Controller -->
The Controller is next. Note that my Controller is using *Constructor Dependency Injection* while specifying an interface for the type. This is possible due to Spring picking up my implementation bean via the `@Service` tag:

```Java
@RestController
public class TempController {

    private final TempService tempService;
    
    // if you are utilizing one constructor you don't need to use @AutoWired here!
    public TempController(TempService tempService){
        this.tempService = tempService;
    }

    @GetMapping("/sum/{x}/{y}")
    public Number getSum(@PathVariable Number x, @PathVariable Number y){
        return this.tempService.add(x, y);
    }

    @GetMapping("/hello")
    public String getHi(){
        return this.tempService.sayHi();
    }

}
```

<!-- Test --> 
And finally, the test. Notice that we're mocking the interface's implementation. Due to the way we configured our project, testing any class that relies on our Service is a lot easier: 

```java

@ExtendWith(MockitoExtension.class)
class TempControllerTest {

    TempController tempController;

    @Mock
    TempService tempService;

    @BeforeEach
    void setUp(){
        tempController = new TempController(tempService);
    }


    @Test
    void testAdd(){
        Integer x = 6;
        Integer y = 5;
        when(tempService.add(x, y))
                .thenReturn(Math.addExact(x, y));
        Number actual = tempController.getSum(x, y);

        assertEquals(11, actual);
    }
}

```

Please let me know if you have any questions and good luck! 

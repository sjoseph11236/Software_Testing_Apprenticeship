# BeforeAll & AfterAll

```
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Disabled;
import org.junit.jupiter.api.RepeatedTest;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.ValueSource;

import main.User;

class UserTest {
	User user; 
	
	@BeforeAll
	static void setUpBeforeEverything() {
		System.out.println("This prints before everything");
	}
	
	
	@AfterAll
	static void teardDownEverything() {
		System.out.println("This prints after everything");
	}
	
	@BeforeEach
	void setUp() {
		user = new User("Sayeed", "Joseph");
		System.out.println("This prints before each test");
	}
	
	@AfterEach
	void runAfter() {
	  System.out.println("after....");
	}
	
	@RepeatedTest(3) 
	@Disabled
	void test() {
		System.out.println("running sometest");
	}
	
	@ParameterizedTest
	@ValueSource(booleans = {true,  false, true})
	@Disabled
	void paramsTest(boolean greetings) {
		System.out.println(greetings);
	}
	
}

```


# Recap Day 7 
## MathUtil.java
```

package main;

public class MathUtil {
	public double circumference(int radius) {
		return 2 * Math.PI * radius; 
	}
	
	public int add(int a, int b) {
		return a + b;
	}
}

```
## Recap Tests
```
package tests;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import main.MathUtil;


class ReacpTests {
	
	MathUtil calc; 

	@BeforeEach
	void setUp() {
		calc = new MathUtil();
	}
	
	@Test
	void testCircumference() {
		int radius = 4; 
//		expected
		double expect = 2 * Math.PI * radius; 
//		actual 
		double actual = calc.circumference(radius);
//		verify
		assertEquals(actual, expect, "Doesnt give the right circumference");
	}
	
	@Test
	void testAdd() {
		int expect = 2; 
		int actual = calc.add(1,1);
		assertEquals(actual, expect);	
	}
	
	@Test 
	void testSubtract() {
		fail("This test will fail");
	}
}


```
# Using @Nested

```

package tests;

import static org.junit.jupiter.api.Assertions.*;

import java.util.Stack;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Nested;
import org.junit.jupiter.api.Test;

//@Nested can be used to express the relationship among several groups of tests

//Create DisplayName "A Stack" 
@DisplayName("A Stack")
class StackTest {

//	Declare stack
	Stack<String> stack;
	
//	Create DisplayName "When New"
	@Nested
	@DisplayName("When New")
	class WhenNew { 
		@BeforeEach
		void setUp(){
			stack = new Stack<>();
		}
		
		@Test 
		@DisplayName("stack is empty")
		void testIsEmpty() {
			assertTrue(stack.empty());
		}
		
		@Nested
		@DisplayName("After Pushing")
		class AfterPushing { 
			
			String name = "Sayeed";
			
			@BeforeEach
			void addNameToStack() {
				stack.push(name);
			}
			
				
			@Test 
			@DisplayName("stack is not empty")
			void testNotEmpty() {
				assertFalse(stack.empty());
			}
			
			@Test
			@DisplayName("returns name and stack is empty")
			void testPopReturnsName() {
				assertEquals(name, stack.pop());
				assertTrue(stack.isEmpty());
			}
		}
	}	

}

```
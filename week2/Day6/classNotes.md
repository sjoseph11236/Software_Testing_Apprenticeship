# JUnit (Basics): 

## MathUtil.java
```
package test;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;

import main.MathUtil;

@DisplayName("Math Util")
class MathUtilsTest {
	MathUtil calc;
	
//	SET UP
	@BeforeEach
	void setUp() {
//		Create instance of class
		System.out.println("Starting to create object");
		calc = new MathUtil();
		System.out.println("Created object");
	}

//	Annotation
//	identifies what methods are to be run as test.
	@Test
	void testAdd() {
//	Expected
		int expected = 2;
//	Actual 
		int actual = calc.add(1, 1); 
//	Verify
//		assertEquals(actual, expected);
		assertEquals(calc.add(1, 1), 2, "add should return 2");
	}
	
	
	@Test
	@DisplayName("isOdd return true for odd values")
	void testIsOdd() {
//		Create instance of class
//		expected
//		actual 
		boolean actual = calc.isOdd(3);
//		verify
		assertTrue(actual);
	}
}
```

## MathUtil.java
```
package main;

public class MathUtil {
	
	
	public int add(int a, int b) {
		return a + b; 
	}
	
	public boolean isOdd(int a) {
		if(a % 2 == 1) return true; 
		
		return false; 
	}
	
}

```


## Main.java
```
package main;

public class Main {

	public static void main(String[] args) {


	}

}

```
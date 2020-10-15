
# Memory Allocation

```
package memoryAllocation;

public class Memory {

	public static void main(String[] args) { // Line 1
//		int i=1; // Line 2  stack 
//		Object obj = new Object(); // Line 3  heap 
		Memory mem = new Memory(); // Line 4
//		mem.foo(obj); // Line 5 stack
		mem.stringPool();
		
	} // Line 9

	private void foo(Object param) { // Line 6
		String str = param.toString(); //// Line 7
		System.out.println(str);
	} // Line 8

	
	public void stringPool() {
        String s1 = "Cat";
        String s2 = "Cat";
        String s3 = new String("Cat");
        
        System.out.println("s1 == s2 :"+(s1==s2));
        System.out.println("s1 == s3 :"+(s1==s3));
	}
}



/*
 Take Aways
 
 
 
 STACK 
 
 	Stores local varaibles and method excutions
 	Order of stack is LIFO (Last in First Out)
 	The stack size can change as the number methods called.
 	
 
 
 HEAP
 
 	Stores objects and classees at runtime
 	No fixed order heap 
 	Size is bigger than stack. 
 
 
 
 
 
 
 * */



```

# Exception Testing 

```

	@Test 
	void testArithematicException() {
		assertThrows(ArithmeticException.class, () -> calc.divide(1, 0), "divide shoul throw and excpetion for dividing by 0" );
	}
```

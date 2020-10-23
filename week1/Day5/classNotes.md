# Class Notes: 

## Stacks and Queues
 ```
package com.learn.stack;

import java.util.LinkedList;
import java.util.Queue;
import java.util.Stack;

public class Main {

	public static void main(String[] args) {

		
		/*
		 
		 
		 Stack: [ 1,   2, ]
		        ^           ^
		       bottom      top
		       
		 Queue:[2] -> [3] -> [4]
  		^                     ^
  	head                    tail
		  	  
		  	  
		  	  
		  	  {
		  	  	val: 1 
		  	  	next: {
		  	  	       val 2
		  	  	      }
		  	     }
		 */   
// Stack
//		LIFO - Last In First Out
//		constant insert and extract operations 
//		Great for back tracking
		Stack<Integer> stack = new Stack<>(); 

//		.push()
//		Add elements to the top of the stack.
		stack.push(1); 
		stack.push(2); 
		stack.push(3);
		
		System.out.println(stack);
		
		
//		.peek()
//		Returns the element on the top of the stack, but does not remove it.
		System.out.println(stack.peek()); // 3
//		.pop()
		Integer removedElement = stack.pop();
		System.out.println(removedElement);
		System.out.println(stack.pop());
		System.out.println(stack);

		
// LinkedList
//	FIFO - First In First Out
//		Keep track of what is next
//		Creating a queue using a Linked list class
//		linked list are series of nodes that point to one another in linear fashion 
//		A node has information about the value and the address that node is at

		Queue<Integer> queue = new LinkedList<>();
			
		
//		add(val)
		queue.add(1);
		queue.add(2);
		queue.add(3);
		queue.add(4);
//	      Again displaying the elements of Queue
		System.out.println(queue);
	


      /*
       * We can remove element from Queue using remove() method,
       * this would remove the first element from the Queue 
       */
      System.out.println("Removed element: "+queue.remove());
      
	    
      /*
       * element() method - this returns the head of the
       * Queue. Head is the first element of Queue
       */
      System.out.println("Head: "+ queue.element());

  
      /*
       * peek() method - it works same as element() method,
       * however it returns null if the Queue is empty
       */
      System.out.println("peek(): "+queue.peek());
	    
      
      /*
       * poll() method - this removes and returns the 
       * head of the Queue. Returns null if the Queue is empty
       */
      System.out.println("poll(): "+ queue.poll());
      
      
      System.out.println(queue);
	}

}



 ```
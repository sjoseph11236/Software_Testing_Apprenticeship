# lesson

## methods

Take a look at the code below:

```java 

class Main {
    public static void main(String[] args){
        System.out.println("hello from day-2!");
    }
}

```

Looks familiar right? This is our main class with our *main method*. This method will serve as our entrypoint. 

`public` is an *access modifier*. This changes the visibility of the method in the entire program. 

`static` is a keyword denoting that this method belong to the class implementation and not an *instance* of the class. We'll talk more about this at a later date. 

`void` is the return type. Return values denote the type of what the method is giving back.

The parantheses are your parameters. They describe your input. For the main method, the input is an optional set of *command line arguments*. They are arguments that can be fed into the program when starting. 

Let's write a method that return two values. How can we do this? 

First lets determine the access modifier. Let's say its `public`. We can this to be `static` for ease of use in our main method. We know this method will need input so we have to describe two `int` values. Here's our final product:

```java
public static int sum ( int a, int b) {
    return a+b; 
}
```

Since this method is `static`, we can immediately call it in our main method without any special instancing.


```java

class Main {
    public static void main(String[] args){
        System.out.println("hello from day-2!");
        // this prints 29!
        System.out.println(sum(12, 17));
    }
}

```

It's possible to access methods in other classes, let's take a look at this example:

```java

class AnotherClass {
    public int multiply(int a, int b){
        return a * b; 
    }
}

```

If I wanted to use this class's method I would need to *instatiate* an object in my main class.


```java

class Main {

    public static void main(String[] args){

        AnotherClass myObject = new AnotherClass();
        //this prints 20! 
        System.out.println(myObject.multiply(4,5));

        System.out.println("hello from day-2!");
        // this prints 29!
        System.out.println(sum(12, 17));
    }
}


```

Instantiating involves utilizing the `new` keyword. This tells Java that you want to create an *instance* of this class. Classes will represent the *type* of object, just like how `int` or `String` is a type.

Lets write a method that tells us if a number is odd. 

```java

class Main {

    // oddchecking method

    public static boolean isOdd(int x){

        return x % 2 == 0 ? true : false; 

    }

    public static void main(String[] args){

        // returns false!
        System.out.println(isOdd(3));

    }
}


```
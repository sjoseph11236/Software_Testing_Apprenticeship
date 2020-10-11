# Lesson

## What is Java?

Java is a strongly-typed, statically-typed, object-oriented, class-based, general-purpose programming language. It was created to address issues associated with other similar languages during the mid 90s.

The main focus was its object-oriented design. We'll explore object-oriented programming at a later date.

## Getting Started

Below is a *source code* snippet written in Java.

```java
// main class declaration
public class Main {
    // main method declaration
    public static void main(String[] args){
        // call to a print function
        // which will produce text on your terminal

        int myInt = 4;
        System.out.println(myInt);
        System.out.println("Hello from Java-land!");
    }
}
```

What's going on here? Take a look at the first line. Here we're declaring a class. Don't worry too much about this now, just know that classes are where all of our code will reside in Java.

Java as a platform is expecting to handle classes to generate what's known as *bytecode*. We'll touch more on this later!

Do you notice the curly braces? Those denote what's known as a *block*. These blocks will be important later once we touch on what's known as *scope*. For now, just know that code will be placed within these curly braces.

A couple more things: `public static void main` is describing what's known as a *method*. This is a subroutine--more commonly known as a function. Generally speaking, methods describe functions inside of classes.

`int myInt` is describing a *variable*. This variable is assigned -- or rather, references -- a *literal* value. Can you spot the literal value? It's `4`. You can make a variable without giving it a value. This is known as *declaring* a variable. When that variable first is given a value to hold, it is *initialized*.

All variables must be declared before they are used by stating the variable's type and name. This means that that Java is *statically-typed*.

Variables are a part of creating *expressions*, or constructs made up of components of the language that will evaluate to a a single value.

Oh, and every line ending with a semicolon is known as a *statement*. Think of them as the code's *sentences*. Statements will always end with a semicolon.

Remember the block? These are a level higher and are composed of statements! [Learn more here.](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/expressions.html)

```java
//this is legal
int myInt;
//just remember to initialize it before you use it!
myInt = 4;
```

## Naming Best Practice

Java largely follows `camelCase` for variables and methods. However, Java follows `PascalCase` for classes. This may seem like a minor distinction, but it'll be important for when you're using built-in and custom-made classes and methods.

## Data Types

Let's take a look at the basic data types for Java.

```java

public class DataTypes {

    public static void main(String[] args){

        // each data type can hold a certain bit-value
        // 8-bit for representing a small integer value
        byte myByte = 100;
        // 16-bit for representing a small integer value
        short myShort = 1;
        // 32-bit for representing an integer value
        int myInt = 5;
        // 64-bit for representing a large integer value
        long myLong = 100_000_000L;
        // 32-bit for representing floating point values
        float myFloat = 13.4f;
        // 64-bit  for representing an even wider scope of floating point values
        double myDub = 21.12341d
        // 16-bit for representing single Unicode characters
        char myChar = 'c';
        // technically represents one bit of information, true or false
        boolean myBool = false;
    }
}

```

All the data types above are known as *primitive* data types. These data types are predefined and are represented by a *reserved* word. Each primitive has an associated *wrapper* class that allows one to use built-in methods on the defined value. Here are a few wrapper classes:

```java

// wrapper classes can be noted by their PascalCase
// note that some names are distinct from their primitive counterparts

Long myLong = 100_000_000L;
Integer myInteger = 23;
Float myFloat = 12.14f;
Double myDouble;
Boolean myBool;
Character myChar;
Short myShort;
Byte myByte;

```

Wrapper classes will be very important down the line so keep them in mind.

One last thing: did you notice the lack of `String`? Well, what's different about `String` versus a primitive like `int`? `String` is `PascalCase` meaning that it's a class! There's no special reason for `String` to be a class versus a primitive. It's simply what the Java Engineers decided for the data type!

## Operators

Java covers all basic arithmetic including `+`, `-`, `/`, `*`, and `%` or modulus. These are all known as *operators* which perform some sort of operation. There are many operators that do very specific things. [Click here to learn more!](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)

## Conditionals

Java supports what's known as conditionals. They are code blocks that resolve only when a certain condition is met. Take the following example:

```java

int myInt = 3;

if (myInt == 3){
    System.out.println("hello!");
}


```

This is an *`if` statement*. It resolves only once its condition is met. The condition is defined in its parameters -- or everything in the paranthesis.

`if` statements can be extended with `else if` and `else` which define other conditions that can be met. *else* specifically doesn't will resolve if none of the other conditions are met.

```java

int myInt = 5;

if (myInt = 3){
    System.out.println("that number is nice");
} else if (myInt = 5) {
    System.out.println("that number is okay");
} else {
    System.out.println("i don't particularly like that number :^(");
}


```

There are also `switch` statements. Unlike `if` statements, these can have multiple execution paths.

<!-- TODO(): Switch statement example -->
<!-- Loops section and that's it! -->

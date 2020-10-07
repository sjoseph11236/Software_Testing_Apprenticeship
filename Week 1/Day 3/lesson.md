# lesson

## ArrayList

Yesterday we worked with arrays. Arrays are very useful but can be difficult to work with at a certain scale. As such, Java engineers implemented the `ArrayList`. Here is how it's implemented:


```java

ArrayList<Integer> myNumList = new ArrayList<>();


```

That's an interesting declaration! Let's break it down. `ArrayList` is a class in Java. They can contain elements of any type but that type needs to be defined between the `< >`. This is known as a generic type. Generic types will be expanded upon at a late date. As you can you see on the right side, we are using the `new` keyword. This allows us to instantiate a new instance of the class `ArrayList`. `<>()` is denoting the generic and parameters. We can leave these empty when we declare a new `ArrayList`.

Note that we're using the wrapper `Integer`. `ArrayList` does not accept primitive types as a generic, so keep in mind.

So why use this data structure? For one, it's dynamic; you can add elements after the size is generated. Another nice thing is the slew of helper methods on the class. Take a look at the following example:

```java

// adds an element to the array
myNumList.add(1);
myNumList.add(2);

// targets an index and changes the value
// 1 here is the index, 5 is the value to be placed
myNumList.set(1, 5)

// removes the element at index 0;
myNumList.remove(0); 

```

There are many more methods with interesting operations. [Explore the documentation here.](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/ArrayList.html)

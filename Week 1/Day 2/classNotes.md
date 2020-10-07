# Class Notes: 

## Day 1 Exit Tix Notes: 
```
  class Main {
    public static void main(String[] args) {

      // What are the 8 primitive types in Java?
      int childAge = 1; //  -2,147,483,648 to 2,147,483,647
      boolean isAvailable = false;
      short team =  300; // the range is 32, 768 to 32,767
      char letter = 'a';
      long longNumber = 130l; // the rangee -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
      byte players = 36; // the range is  -128 to 127
      float myFloat = 1.37f; //  6 to 7 decimal digits
      double cost = 2.50d; //storing 15 decimal digits
      // System.out.println(childAge);
      // System.out.println(isAvailable);
      // System.out.println(team);
      // System.out.println(letter);
      // System.out.println(longNumber);
      // System.out.println(players);
      // System.out.println(myFloat);
      // System.out.println(cost);

      // What is casting? 
      
        //widening Casting           
        // byte -> short -> char -> int -> long -> float -> double

        int myConvertedChar = (int) letter; //97
        // System.out.println(myConvertedChar);

        //Narrowing Casting
        // double -> float -> long -> int -> char -> short -> byte
        char myConvertedInt = (char) myConvertedChar; 
        // System.out.println(myConvertedInt);
        
        // ---DOES NOT WORK----
        // int myConvertedBoolean = (int) isAvailable;
        // System.out.println(myConvertedBoolean);

        // char convert = (char) isAvailable;
        // System.out.println(convert);


      // What are the terms for each section of a For Loop?
  // initialization condition increment/decremnt
      // for(int i = 0;   i < 5 ;    i++) {
      //   System.out.println(i);
      //   // System.out.println("Looping agian");
      // }

      // Write an example using the ternary operator.
      // isAvailable = true;
      // int oneMore = !!isAvailable ? childAge : 0; 
      // System.out.println(oneMore);
      // System.out.println(isAvailable); // true
      // isAvailable = false;
      // System.out.println(isAvailable); // false

      // Write any variable that holds a primitive type and another that holds a Wrapper type.
        Boolean myBool = false;
        // System.out.println(myBool);

      // Fix any mistakes in the following line: int x = "S"
        // int x = 5;
        // String x = "S";
        // int x =  'S';
        // int x = (int) 'S';
        char x = 's';
        // System.out.println(x);
      // What is the difference between declaring, initializing, and assigning a variable?

      // What is the difference between && and ||?

      int value = (myBool != true ) || (x == 'S') ? 3 : 4;
    //   int value;

    //   if(myBool  && x  == 'S') {
    //     value = 3; 
    //   }
    //   else {
    //     value = 4;
    //   }
      
      System.out.println(value); //4
    }
  }
```

# Arrays 

```
import java.util.*; 

class Main { 
  public static void main(String[] args) {
    // Arrays fixed size 
        //position: 0. 1. 2. 3  4
    int[] myNums = {1, 2, 3, 4, 5}; // [1, 2,3,4,5];
    // System.out.println(Arrays.toString(myNums));
    // System.out.println(myNums.length);
    System.out.println(myNums[3]);

    int[] myNumbers = new int[5]; // [0, 0, 0, 0 ,0 ]
    // int[] myNumbers = new int[]; // doesnt work
    System.out.println(Arrays.toString(myNumbers));
    myNumbers[0] = 1; // [1, 0,0, 0 0]
    System.out.println(Arrays.toString(myNumbers));
    for(int i = 1; i <= myNumbers.length; i++) {
      myNumbers[i] = i + 1; 
    }
  }
}

```
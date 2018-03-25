## Lecture 1: Intro, Hello World Java
      - Introduction
      - Course Logistics
      - Hello World
      
      1. Before Java variables can be used, they must de declared
      
      2. Java variables must have a specific type
      
      3. Java variable types can never change
      
      4. Types are verified before the code even runs!!!
      
      
      
## Lecture 2: Defining and Using Classes

      1. Functions must be declared as part of a class in Java

      A function that is part of a class is called a method

      So in Java, all functions are methods

      2. To define a function in Java, we use "public static". We will see alternative ways of defining functions later

      3. All parameters of a function must have a declared type, and the return value of the function must have a declared type
      functions in java return only one value!
      
 ## Lecture 3: References, Recursion, and Lists
 
#### 3.1 Bits Types: Your computer stores information in “memory”.
      Information is stored in memory as a sequence of ones and zeros.
      Example: 72 stored as 01001000
      Example: 205.75 stored as … 01000011 01001101 11000000 00000000
      Example: The letter H stored as 01001000 (same as the number 72)
      Example: True stored as 00000001

      Each Java type has a different way to interpret the bits:
      8 primitive types in Java: **byte, short, int, long, float, double, boolean, char**
      We won’t discuss the precise representations in much detail in 61B.
      Covered in much more detail in 61C.
      

 #### 3.1 Reference Types
 
- There are 8 primitive types in Java: byte, short, int, long, float, double, boolean, char

- Everything else, including arrays, is a **reference type.**

 #### 3.2 Parameter Passing
 
 ## The Golden Rule of Equals (GRoE)

### There are 9 types of variables in Java:

#### 8 primitive types (byte, short, int, long, float, double, boolean, char).

#### The 9th type is references to Objects (an arrow). References may be null.

http://goo.gl/ngsxkq

 #### 3.3 Instantiation of Arrays
 
      Arrays are also Objects. As we’ve seen, objects are (usually) instantiated using the new keyword. 
      
      Planet p = new Planet(0, 0, 0, 0, 0, “blah.png”);    
      
      int[] a = new int[]{0, 1, 2, 95, 4};
      
      Creates a 64 bit box for storing an int array address. (declaration)
      
      Creates a new Object, in this case an int array. (instantiation)
      
      Puts the address of this new Object into the 64 bit box named a. (assignment)
      
      Note: Instantiated objects can be lost!
      
      If we were to reassign a to something else, we’d never be able to get the original Object back!
      
 #### 3.4 IntList and Linked Data Structures 

 
 ## Lecture 4: SLLists and Avoiding Nakedness (SLLists, Nested Classes, Sentinel Nodes)
 
#### 3.1 From IntList to SLList
            - The private keyword 
            - Nested classes
            - Recursive private helper methods
            - Caching
            - Sentinel nodes
 

 
 
 
 
 
 ## Lecture 5: DLLists, Arrays

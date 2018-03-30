# 1. Week 1 

## Lecture 1: Functions (40min)

add(2, mul(9, mul(add(4, mul(4, 6)), add(3, 5))))

operator; operand

Functions; Objects; Interpreters

## Lecture 2: Names

An environment is a sequence of frames.
A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found.

disc 00 Lost on the Moon

HW 01

# Week 2 

## Lecture 3 control ,(40min) Lab0

Life Cycle of User Defined FUnction

    Def statement:

    Call expression

    Calling/Applying

An environment is a sequence of frames.
• The global frame alone
• A local, then the global frame

Miscellaneous Python Features

## lab 01 expressions and control

## Lecture 4 HIgher-order fucntions

Lambda expressions are not common in Python, but important in general
Lambda expressions in Python cannot contain statements at all!
Disc 01 Convtrol & Environments


## Lecture 5 Environments

Environment diagrams

Environment Diagrams for Nested Def Statements

• Every user-defined function has a parent frame (often global)

• The parent of a function is the frame in which it was defined

• Every local frame has a parent frame (often global)

• The parent of a frame is the parent of the function called

How to draw an environment diagram

1. Add a local frame, titled with the <name> of the function being called.
    
2. Copy the parent of the function to the local frame: [parent=<label>]
    
3. Bind the <formal parameters> to the arguments in the local frame.
    
4. Execute the body of the function in the environment that starts with the local frame.


## Hw2

## Hog

## Lecture 6 Iteration

Return Statements
A return statement completes the evaluation of a call expression and provides its value
f(x) for user-defined function f: switch to a new environment; execute f's body
return statement within f: switch back to the previous environment; f(x) now has a value
Only one return statement is ever executed while executing the body of a function


## Lecture 7 Recursion

Iteration is a special case of recursion:

        def fact_iter(n):
            total, k = 1, i
            while k <= n:
                total, k = total*k, k +1
            return total
            
        def fact(n):
            if n == 0:
                return 1
            else:
                return n*fact(n-1)


The Recursive Leap of Faith

        1. verify the base case
        
        2. treat fact as a functional abstraction
        
 Mutual Recursion:
 
 
 Converting Recursion to Iteration
 
 #### Is fact implemented correctly?
1. Verify the base case
2. Treat fact as a functional abstraction!
3. Assume that fact(n-1) is correct
4. Verify that fact(n) is correct

#### Mutual Recursion

The Luhn Algorithm

    def split(n):
        return n//10, n%10


    def sum_digits(n):
        if n < 10:
            return n
        else:
            all_but_last, last = split(n)
            return sum_digits(all_but_last) + last


    def luhn_sum(n):
        if n < 10:
            return n
        else:
            all_but_last, last = split(n)
            return luhn_sum_double(all_but_last) + last


    def luhn_sum_double(n):
        all_but_last, last = split(n)
        luhn_digit = sum_digits(2 * last)
        if n < 10:
            return luhn_digit
        else:
            return luhn_sum(all_but_last) + luhn_digit


 

## Lecture 8 Tree Recursion

- Each cascade frame is from a different call to cascade.
- Until the Return value appears, that call has not completed.
- Any statement can appear before or after the recursive call.

        def cascade(n):
             print(n)
             if n >= 10:
                 cascade(n//10)
                 print(n)



        def inverscas(n):
            grow(n)
            print(n)
            shrink(n)

        def f_then_g(f,g,n):
            if n:
                f(n)
                g(n)

        grow = lambda n: f_then_g(grow, print, n//10)
        shrink = lambda n: f_then_g(print, shrink, n// 10)
        
        
        def fib(n):
            if n == 0:
                return 0
            if n == 1:
                return 1
            else:
                return fib(n-1) + fib(n-2)

This process is highly repetitive; fib is called on the same argument multiple times

        def count_partitions(n, m):
             if n == 0:
                return 1
             elif n < 0:
                return 0
             elif m == 0:
                return 0
             else:
                 with_m = count_partitions(n-m, m)
                 without_m = count_partitions(n, m-1)
                 return with_m + without_m
 
 
#### COunting Partitions



## Lecture 9 Function Examples

#### 9.1 Test-Driven Development

    Write the test of a function before you write the function.
        A test will clarify the domain, range, & behavior of a function.
        Tests can help identify tricky edge cases.
    Develop incrementally and test each piece before moving on.
        You can't depend upon code that hasn't been tested.
        Run your old tests again after you make new changes.
    Bonus idea: Run your code interactively.
        Don't be afraid to experiment with a function after you write it.
        Interactive sessions can become doctests. Just copy and paste.

#### 9.2 Decorators

    @trace1
    def triple(x):
     return 3 * x 
     
is identical to:

    def triple(x):
     return 3 * x
    triple = trace1(triple)
    
#### 9.3 What would python print

    def delay(arg):
     print('delayed')
     def g():
        return arg
     return g
     
     
     delay(delay)()(6)()
     
## Lecture 10 Data Abstraction

#### 10.1 Concept

    • Compound values combine other values together
    § A date: a year, a month, and a day
    § A geographic position: latitude and longitude
    • Data abstraction lets us manipulate compound values as units
    • Isolate two parts of any program that uses data:
    § How data are represented (as parts)
    § How data are manipulated (as units)
    • Data abstraction: A methodology by which functions enforce an abstraction barrier between representation and use
    
    
#### Rational NUmbers

    •rational(n, d) returns a rational number x
    •numer(x) returns the numerator of x
    •denom(x) returns the denominator of x

    def mul_rational(x, y):
         return rational(numer(x) * numer(y),
         denom(x) * denom(y))
    
#### Pairs ,Abstraction Barriers

#### Data Representations

## Lecture 11 Containers 

#### 




## Lecture 12 Trees



## Lecture 13 Mutable Values




## Lecture 14 Mutable Functions




## Lecture 15 Objects




## Lecture 16 Inheritance


## Lecture 17 Representation



## Lecture 18 Growth


## Lecture 19 Composition




## Lecture 20 Ordered Sets



## Lecture 21 Tree Sets



## Lecture 22 Data Examples 



## Lecture 23 Users


## Lecture 24 Scheme

## Lecture 25 Exceptions



## Lecture 26 Calculator


## Lecture 27 Interpreters



## Lecture 28 Tail Calls


## Lecture 29 Macros

## Lecture 30 Iterators


## Lecture 31 Streams


## Lecture 32 Declarative Programming

## Lecture 33 Tables

## Lecture 34 Aggregation

## Lecture 35 Databases

## Lecture 36 Distributed Data

## Lecture 37 Natural Language



## Lecture 38 Conclusion















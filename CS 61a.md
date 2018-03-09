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
 

## Lecture 8 Tree Recursion

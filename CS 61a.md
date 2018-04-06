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

# 2. Week 2

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

# 3. Week 3

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

# 4. Week 4

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

from operator import getitem
getitem(pair, 0)

#### Data Representations

We need to guarantee that constructor and selector functions work
together to specify the right behavior
• Behavior condition: If we construct rational number x from numerator
n and denominator d, then numer(x)/denom(x) must equal n/d
• Data abstraction uses selectors and constructors to define behavior
• If behavior conditions are met, then the representation is valid


    def rational(n, d):
    def select(name):
        if name == 'n':
            return n
        elif name == 'd':
            return d
    return select
    def numer(x):
        return x('n')
    def denom(x):
        return x('d')
        
    x = rational(2,3)    
    numer(x)
    
# 5. Week 5

## Lecture 11 Containers 

Built-in operators for testing whether an element appears in a compound value

    digits = [2//2, 2+2+2+2, 2, 2*2*2]
    [2,7] + digits*2
    [2, 7, 1, 8, 2, 8, 1, 8, 2, 8]
    
    add([2, 7], mul(digits, 2))
    [2, 7, 1, 8, 2, 8, 1, 8, 2, 8]

#### For Statements

#### Ranges

#### List comprehensions

    [<map exp> for <name> in <iter exp> if <filter exp>]
    Short version: [<map exp> for <name> in <iter exp>]
    A combined expression that evaluates to a list using this evaluation procedure:
    1. Add a new frame with the current frame as its parent
    2. Create an empty result list that is the value of the expression
    3. For each element in the iterable value of <iter exp>:
    A. Bind <name> to that element in the new frame from step 1
    B. If <filter exp> evaluates to a true value, then add the value of <map exp> to the result list

#### Strings

#### Dictionaries

Dictionaries are unordered collections of key-value pairs
Dictionary keys do have two restrictions:
•A key of a dictionary cannot be a list or a dictionary (or any mutable type)
•Two keys cannot be equal; There can be at most one value for a given key
This first restriction is tied to Python's underlying implementation of dictionaries
The second restriction is part of the dictionary abstraction
If you want to associate multiple values with a key, store them all in a sequence value

## Lecture 12 Trees

•A method for combining data values satisfies the closure property if:
 The result of combination can itself be combined using the same method
•Closure is powerful because it permits us to create hierarchical structures
•Hierarchical structures are made up of parts, which themselves are made up
of parts, and so on

#### Box-and-Pointer Notation in Environment Diagrams

Lists are represented as a row of index-labeled adjacent boxes, one per element
Each box either contains a primitive value or points to a compound value

#### Slicing 

#### Processing Container Values

##### Sequence Aggregation

    def divisors(n):
        return [1] + [x for x in range(2, n) if n % x == 0]
        
    [n for n in range(1, 1000) if sum(divisors(n)) == n]

    Several built-in functions take iterable arguments and aggregate them into a value
    • sum(iterable[, start]) -> value
    Return the sum of an iterable of numbers (NOT strings) plus the value of parameter 'start' (which defaults to 0). When the iterable     is empty, return start.

    • max(iterable[, key=func]) -> value
    max(a, b, c, ...[, key=func]) -> value
    With a single iterable argument, return its largest item.
    With two or more arguments, return the largest argument.
    
     all(iterable) -> bool
     Return True if bool(x) is True for all values x in the iterable.
     If the iterable is empty, return True.
     
#### Tree Abstraction

    **Recursive description (wooden trees):**
    A tree has a root and a list of branches
    Each branch is a tree
    A tree with zero branches is called a leaf

    **Relative description (family trees):**
    Each location in a tree is called a node
    Each node has a label value
    One node can be the parent/child of another

    People often refer to values by their locations: "each parent is the sum of its children"

def tree(label, branches=[]):
    for branch in branches:
        assert is_tree(branch)
    return [label] + list(branches)
    
def label(tree):
    return tree[0]

def branches(tree):
    return tree[1:]
    
def is_tree(tree):
     if type(tree) != list or len(tree) < 1:
        return False
     for branch in branches(tree):
        if not is_tree(branch):
            return False
     return True 
     
#### Tree Processing

    odds = [1, 3, 5, 7, 9]
    [x for x in odds if 25 % x == 0]
    
    [1, 5]
    
    
>>> def width(area, height):
        assert area % height == 0
        return area // height
The perimeter of a rectangle is the sum of its side lengths.

>>> def perimeter(width, height):
        return 2 * width + 2 * height
The height of a rectangle with integer side lengths must be a divisor of its area. We can compute the minimum perimeter by considering all heights.

>>> def minimum_perimeter(area):
        heights = divisors(area)
        perimeters = [perimeter(width(area, h), h) for h in heights]
        return min(perimeters)
>>> area = 80
>>> width(area, 5)
16
>>> perimeter(16, 5)
42
>>> perimeter(10, 8)
36
>>> minimum_perimeter(area)
36
>>> [minimum_perimeter(n) for n in range(1, 10)]
[4, 6, 8, 8, 12, 10, 16, 12, 12]


#### Linked Lists ** Important and useful and interesting **

A common representation of a sequence constructed from nested pairs is called a linked list.

four = [1, [2, [3, [4, 'empty']]]]

A linked list is a pair containing the first element of the sequence (in this case 1) and the rest of the sequence (in this case a representation of 2, 3, 4). The second element is also a linked list. The rest of the inner-most linked list containing only 4 is 'empty', a value that represents an empty linked list.

    >>> empty = 'empty'
    >>> def is_link(s):
            """s is a linked list if it is empty or a (first, rest) pair."""
            return s == empty or (len(s) == 2 and is_link(s[1]))
    >>> def link(first, rest):
            """Construct a linked list from its first element and the rest."""
            assert is_link(rest), "rest must be a linked list."
            return [first, rest]
    >>> def first(s):
            """Return the first element of a linked list s."""
            assert is_link(s), "first only applies to linked lists."
            assert s != empty, "empty linked list has no first element."
            return s[0]
    >>> def rest(s):
            """Return the rest of the elements of a linked list s."""
            assert is_link(s), "rest only applies to linked lists."
            assert s != empty, "empty linked list has no rest."
            return s[1]
        
        
        >>> four = link(1, link(2, link(3, link(4, empty))))
        >>> first(four)
        1
        >>> rest(four)
        [2, [3, [4, 'empty']]]
        
        
        >>> def len_link(s):
        """Return the length of linked list s."""
        length = 0
        while s != empty:
            s, length = rest(s), length + 1
        return length
        >>> def getitem_link(s, i):
                """Return the element at index i of linked list s."""
                while i > 0:
                    s, i = rest(s), i - 1
                return first(s)
##### Linked list simplified version

        empty = 'empty'
        def is_link(s):
                """s is a linked list if it is empty or a (first, rest) pair."""
                return s == empty or (len(s) == 2 and is_link(s[1]))
        def link(first, rest):
                """Construct a linked list from its first element and the rest."""
                return [first, rest]
        def first(s):
                """Return the first element of a linked list s."""
                return s[0]
        def rest(s):
                """Return the rest of the elements of a linked list s."""
                return s[1]

        def len_link(s):
                """Return the length of linked list s."""
                length = 0
                while s != empty:
                    s, length = rest(s), length + 1
                return length
        def getitem_link(s, i):
                """Return the element at index i of linked list s."""
                while i > 0:
                    s, i = rest(s), i - 1
                return s[0]
   
#### Recursive manipulation of linked list

        Recursive manipulation. Both len_link and getitem_link are iterative. They peel away each layer of nested pair until the end of         the list (in len_link) or the desired element (in getitem_link) is reached. We can also implement length and element selection           using recursion.

        >>> def len_link_recursive(s):
                """Return the length of a linked list s."""
                if s == empty:
                    return 0
                return 1 + len_link_recursive(rest(s))
        >>> def getitem_link_recursive(s, i):
                """Return the element at index i of linked list s."""
                if i == 0:
                    return first(s)
                return getitem_link_recursive(rest(s), i - 1)
                
#### Recursion is also useful for transforming and combining linked lists.

    >>> def extend_link(s, t):
            """Return a list with the elements of s followed by those of t."""
            assert is_link(s) and is_link(t)
            if s == empty:
                return t
            else:
                return link(first(s), extend_link(rest(s), t))
    >>> extend_link(four, four)
    [1, [2, [3, [4, [1, [2, [3, [4, 'empty']]]]]]]]
    >>> def apply_to_all_link(f, s):
            """Apply f to each element of s."""
            assert is_link(s)
            if s == empty:
                return s
            else:
                return link(f(first(s)), apply_to_all_link(f, rest(s)))
    >>> apply_to_all_link(lambda x: x*x, four)
    [1, [4, [9, [16, 'empty']]]]
    >>> def keep_if_link(f, s):
            """Return a list with elements of s for which f(e) is true."""
            assert is_link(s)
            if s == empty:
                return s
            else:
                kept = keep_if_link(f, rest(s))
                if f(first(s)):
                    return link(first(s), kept)
                else:
                    return kept
    >>> keep_if_link(lambda x: x%2 == 0, four)
    [2, [4, 'empty']]
    >>> def join_link(s, separator):
            """Return a string of all elements in s separated by separator."""
            if s == empty:
                return ""
            elif rest(s) == empty:
                return str(first(s))
            else:
                return str(first(s)) + separator + join_link(rest(s), separator)
    >>> join_link(four, ", ")
    '1, 2, 3, 4'

#### Recursive Construction. 

    Linked lists are particularly useful when constructing sequences incrementally, a situation that arises often in recursive computations.
    
    
    >>> def partitions(n, m):
        """Return a linked list of partitions of n using parts of up to m.
        Each partition is represented as a linked list.
        """
        if n == 0:
            return link(empty, empty) # A list containing the empty partition
        elif n < 0 or m == 0:
            return empty
        else:
            using_m = partitions(n-m, m)
            with_m = apply_to_all_link(lambda s: link(m, s), using_m)
            without_m = partitions(n, m-1)
            return extend_link(with_m, without_m)
            
            
        >>> def print_partitions(n, m):
                lists = partitions(n, m)
                strings = apply_to_all_link(lambda s: join_link(s, " + "), lists)
                print(join_link(strings, "\n"))
                
## Lecture 14 Mutable Functions

**Adding state to data is a central ingredient of a paradigm called object-oriented programming.**

#### The Object Metaphor

In fact, all values in Python are objects. That is, all values have behavior and attributes. They act like the values they represent.

#### Sequence Objects

Instances of primitive built-in values such as numbers are immutable. The values themselves cannot change over the course of program execution. Lists on the other hand are mutable.

>>> chinese = ['coin', 'string', 'myriad']  # A list literal
>>> suits = chinese                         # Two names refer to the same list
As cards migrated to Europe (perhaps through Egypt), only the suit of coins remained in Spanish decks (oro).

>>> suits.pop()             # Remove and return the final element
'myriad'
>>> suits.remove('string')  # Remove the first element that equals the argument

Sharing and Identity. Because we have been changing a single list rather than creating new lists, the object bound to the name chinese has also changed, because it is the same list object that was bound to suits!

#### Deep copy and shallow copy

Lists can be copied using the list constructor function. Changes to one list do not affect another, unless they share structure.

>>> nest = list(suits)  # Bind "nest" to a second list with the same elements
>>> nest[0] = suits     # Create a nested list

Two objects are identical if they are equal in their current value, and any change to one will always be reflected in the other. Identity is a stronger condition than equality.

>>> suits is nest[0]
True
>>> suits is ['heart', 'diamond', 'spade', 'club']
False
>>> suits == ['heart', 'diamond', 'spade', 'club']
True

The final two comparisons illustrate the difference between is and ==. The former checks for identity, while the latter checks for the equality of contents.

#### List comprehensions.

A list comprehension always creates a new list. For example, the unicodedata module tracks the official names of every character in the Unicode alphabet. We can look up the characters corresponding to names, including those for card suits.

    suits = ['heart', 'diamond', 'spade', 'club']
    from unicodedata import lookup
    [lookup('WHITE ' + s.upper() + ' SUIT') for s in suits]

    ['♡', '♢', '♤', '♧']
    
#### Tuples.

A tuple, an instance of the built-in tuple type, is an immutable sequence. Tuples are created using a tuple literal that separates element expressions by commas. Parentheses are optional but used commonly in practice. Any objects can be placed within tuples.

>>> 1, 2 + 3
(1, 5)
>>> ("the", 1, ("and", "only"))
('the', 1, ('and', 'only'))
>>> type( (10, 20) )
<class 'tuple'>

Like lists, tuples have a finite length and support element selection. They also have a few methods that are also available for lists, such as count and index.

Like lists, tuples have a finite length and support element selection. They also have a few methods that are also available for lists, such as count and index.

>>> code = ("up", "up", "down", "down") + ("left", "right") * 2
>>> len(code)
8
>>> code[3]
'down'
>>> code.count("down")
2
>>> code.index("left")
4


Apart from tuples being immutable there is also a semantic distinction that should guide their usage. Tuples are heterogeneous data structures (i.e., their entries have different meanings), while lists are homogeneous sequences. Tuples have structure, lists have order.

https://stackoverflow.com/questions/626759/whats-the-difference-between-lists-and-tuples

However, the methods for manipulating the contents of a list are not available for tuples because tuples are immutable.

While it is not possible to change which elements are in a tuple, it is possible to change the value of a mutable element contained within a tuple.

1	nest = (10, 20, [30, 40])
2	nest[2].pop()

#### Dictionaries

Strings commonly serve as keys, because strings are our conventional representation for names of things. This dictionary literal gives the values of various Roman numerals.

>>> numerals = {'I': 1.0, 'V': 5, 'X': 10}
Looking up values by their keys uses the element selection operator that we previously applied to sequences.

>>> numerals['X']
10

**A dictionary can have at most one value for each key. Adding new key-value pairs and changing the existing value for a key can both be achieved with assignment statements.**

    The dictionary type also supports various methods of iterating over the contents of the dictionary as a whole. The methods keys,        values, and items all return iterable values.

    >>> sum(numerals.values())
    66
    A list of key-value pairs can be converted into a dictionary by calling the dict constructor function.

    >>> dict([(3, 9), (4, 16), (5, 25)])
    {3: 9, 4: 16, 5: 25}
    Dictionaries do have some restrictions:

    A key of a dictionary cannot be or contain a mutable value.
    There can be at most one value for a given key.
    
A useful method implemented by dictionaries is get, which returns either the value for a key, if the key is present, or a default value. The arguments to get are the key and the default value.

>>> numerals.get('A', 0)
0
>>> numerals.get('V', 0)
5
Dictionaries also have a comprehension syntax analogous to those of lists. A key expression and a value expression are separated by a colon. Evaluating a dictionary comprehension creates a new dictionary object.

>>> {x: x*x for x in range(3,6)}
{3: 9, 4: 16, 5: 25}

#### Local State

Lists and dictionaries have local state: they are changing values that have some particular contents at any point in the execution of a program. The word "state" implies an evolving process in which that state may change.

An implementation of make_withdraw requires a new kind of statement: a nonlocal statement. When we call make_withdraw, we bind the name balance to the initial amount. We then define and return a local function, withdraw, which updates and returns the value of balance when called.

>>> def make_withdraw(balance):
        """Return a withdraw function that draws down balance with each call."""
        def withdraw(amount):
            nonlocal balance                 # Declare the name "balance" nonlocal
            if amount > balance:
                return 'Insufficient funds'
            balance = balance - amount       # Re-bind the existing balance name
            return balance
        return withdraw
        

# 6. Week 6

## Lecture 15 Objects

Object-oriented programming (OOP) is a method for organizing programs that brings together many of the ideas introduced in this chapter
The paradigm of object-oriented programming has its own vocabulary that supports the object metaphor. We have seen that an object is a data value that has methods and attributes, accessible via dot notation. Every object also has a type, called its class. To create new types of data, we implement new classes.

#### Objects and Classes

A class serves as a template for all objects whose type is that class. Every object is an instance of some particular class. The objects we have used so far all have built-in classes, but new user-defined classes can be created as well. A class definition specifies the attributes and methods shared among objects of that class. 

An Account class allows us to create multiple instances of bank accounts. The act of creating a new object instance is known as instantiating the class. The syntax in Python for instantiating a class is identical to the syntax of calling a function. In this case, we call Account with the argument 'Kirk', the account holder's name.

>>> a = Account('Kirk')

An attribute of an object is a name-value pair associated with the object, which is accessible via dot notation. The attributes specific to a particular object, as opposed to all objects of a class, are called instance attributes. Each Account has its own balance and account holder name, which are examples of instance attributes. In the broader programming community, instance attributes may also be called fields, properties, or instance variables.

>>> a.holder

'Kirk'

>>> a.balance

0

Functions that operate on the object or perform object-specific computations are called methods. The return values and side effects of a method can depend upon and change other attributes of the object. For example, deposit is a method of our Account object a. It takes one argument, the amount to deposit, changes the balance attribute of the object, and returns the resulting balance.

>>> a.deposit(15)
15
We say that methods are invoked on a particular object. As a result of invoking the withdraw method, either the withdrawal is approved and the amount is deducted, or the request is declined and the method returns an error message.

>>> a.withdraw(10)  # The withdraw method returns the balance after withdrawal
5
>>> a.balance       # The balance attribute has changed
5
>>> a.withdraw(10)
'Insufficient funds'
As illustrated above, the behavior of a method can depend upon the changing attributes of the object. Two calls to withdraw with the same argument return different results.

#### Defining Classes

User-defined classes are created by class statements, which consist of a single clause. A class statement defines the class name, then includes a suite of statements to define the attributes of the class:

class <name>:
    <suite>
        
>>> class Account:
        def __init__(self, account_holder):
            self.balance = 0
            self.holder = account_holder
            
#### Message Passing and Dot Expressions



# 7. Week 7

## Lecture 16 Inheritance


## Lecture 17 Representation



## Lecture 18 Growth

# 8. Week 8

## Lecture 19 Composition




## Lecture 20 Ordered Sets



## Lecture 21 Tree Sets


# 9. Week 9

## Lecture 22 Data Examples 



## Lecture 23 Users

# 10. Week 10

## Lecture 24 Scheme

## Lecture 25 Exceptions



## Lecture 26 Calculator

# 12. Week 12

## Lecture 27 Interpreters



## Lecture 28 Tail Calls


## Lecture 29 Macros

# 13. Week 13

## Lecture 30 Iterators


## Lecture 31 Streams


## Lecture 32 Declarative Programming

# 14. Week 14

## Lecture 33 Tables

## Lecture 34 Aggregation

## Lecture 35 Databases

# 15. Week 15

## Lecture 36 Distributed Data

## Lecture 37 Natural Language



## Lecture 38 Conclusion















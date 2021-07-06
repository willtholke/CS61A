# CS 61A: Structure & Interpretation of Computer Programs

    University of California, Berkeley
    Instructors: Albert Xu, Alex Kassil, Catherine Cang
    albertxu3@berkeley.edu, alexkassil@berkeley.edu,  catherinecang@berkeley.edu
    Office Hours: cs61a.org/office-hours/
    Lecture: Mon/Tues/Thurs/Fri 12:30pm-2:00pm
    Author: Will Tholke

## Table of Contents
- [CS 61A: Structure & Interpretation of Computer Programs](#cs-61a-structure--interpretation-of-computer-programs)
  - [Table of Contents](#table-of-contents)
  - [Lecture 1, 06/22/21: Expressions](#lecture-1-062221-expressions)
    - [Expressions & Statements](#expressions--statements)
    - [Operand vs. Operator](#operand-vs-operator)
    - [Call Expressions](#call-expressions)
  - [Lecture 2, 06/22/21: Functions, Values, Objects, Interpreters, & Data](#lecture-2-062221-functions-values-objects-interpreters--data)
    - [Types of Expressions](#types-of-expressions)
    - [Assignment Statements](#assignment-statements)
    - [Values](#values)
    - [Names](#names)
    - [Discussion Question 1](#discussion-question-1)
    - [Environment Diagrams Preview (not comprehensive)](#environment-diagrams-preview-not-comprehensive)
    - [Defining Functions](#defining-functions)
    - [Calling User-Defined Functions](#calling-user-defined-functions)
    - [Environments](#environments)
  - [Lecture 3, 06/23/21: Control](#lecture-3-062321-control)
    - [None](#none)
    - [Pure Functions & Non-Pure Functions](#pure-functions--non-pure-functions)
    - [Environments](#environments-1)
    - [Demo](#demo)
    - [Compound Statements](#compound-statements)
  - [Lecture 4, 06/24/21: Higher Order Functions](#lecture-4-062421-higher-order-functions)
    - [The Fibonacci Sequence](#the-fibonacci-sequence)
    - [Characteristics of Functions](#characteristics-of-functions)
    - [Higher Order Functions](#higher-order-functions)
    - [A Function That Returns a Function](#a-function-that-returns-a-function)
    - [Lambda Expressions](#lambda-expressions)
  - [Lecture 5, 06/28/21: Environments](#lecture-5-062821-environments)
    - [Environment Diagrams for Higher Order Functions](#environment-diagrams-for-higher-order-functions)
    - [Environments for Nested Definitions](#environments-for-nested-definitions)
    - [Simplified Guide to Draw an Environment Diagram](#simplified-guide-to-draw-an-environment-diagram)
    - [Complete Guide to Environment Diagrams](#complete-guide-to-environment-diagrams)
      - [Assignment Statements](#assignment-statements-1)
      - [Def Statements](#def-statements)
      - [Return Statements](#return-statements)
      - [Primitive Expression](#primitive-expression)
      - [Call Expression](#call-expression)
      - [Make a new frame](#make-a-new-frame)
    - [Currying](#currying)
  - [Lecture 6, 06/29/21: Recursion](#lecture-6-062921-recursion)
    - [Recursive Functions](#recursive-functions)
    - [Sum Digits Without a While Loop](#sum-digits-without-a-while-loop)
    - [The anatomy of a recursive function](#the-anatomy-of-a-recursive-function)
    - [The Recursive Leap of Faith](#the-recursive-leap-of-faith)
    - [Abstraction](#abstraction)
  - [Lecture 7, 06/29/21: Tree Recursion](#lecture-7-062921-tree-recursion)
    - [Tree Recursion](#tree-recursion)
    - [Towers of Hanoi](#towers-of-hanoi)
    - [Counting Partitions](#counting-partitions)
  - [Lecture 8, 06/29/21: Functional Decomposition + Debugging](#lecture-8-062921-functional-decomposition--debugging)
  - [Lecture 9, 07/06/21: Sequences + Data Abstraction](#lecture-9-070621-sequences--data-abstraction)
    - [Subheader 1](#subheader-1)
    - [Subheader 2](#subheader-2)
    - [Subheader 3](#subheader-3)
  - [Lecture 10, 07/07/21: Trees](#lecture-10-070721-trees)
    - [Subheader 1](#subheader-1-1)
    - [Subheader 2](#subheader-2-1)
    - [Subheader 3](#subheader-3-1)
  - [Lecture 11, 07/08/21: Mutable Sequences](#lecture-11-070821-mutable-sequences)
    - [Subheader 1](#subheader-1-2)
    - [Subheader 2](#subheader-2-2)
    - [Subheader 3](#subheader-3-2)
  - [Lecture 12, 07/12/21: Complexity](#lecture-12-071221-complexity)
    - [Subheader 1](#subheader-1-3)
    - [Subheader 2](#subheader-2-3)
    - [Subheader 3](#subheader-3-3)
  - [Lecture 13, 07/13/21: Iterators + Generators](#lecture-13-071321-iterators--generators)
    - [Subheade 1](#subheade-1)
    - [Subheader 2](#subheader-2-4)
    - [Subheader 3](#subheader-3-4)
  - [Lecture 14, 07/14/21: Midterm Review](#lecture-14-071421-midterm-review)
    - [Reminder: Midterm is tomorrow!](#reminder-midterm-is-tomorrow)
    - [Subheader 1](#subheader-1-4)
    - [Subheader 2](#subheader-2-5)
    - [Subheader 3](#subheader-3-5)


## Lecture 1, 06/22/21: Expressions

### Expressions & Statements
  
An expression is a peice of code that describes computation and evaluates to some value while a *statement* is one or more lines of code that make something happen in a program; ex: expression is `1 + 2`, value is `3`

- Expressions are evaluated
- Statements are executed

- all expressions can be written in **f(x)** form; all values are expressions, but not all expressions are values; an expression can also be a function

### Operand vs. Operator
An **operand** are the values that an operator acts on whereas **operators** are special symbols that indicate that a computation should be performed
  
*Example:*
```py
from operator import add, mul
add(1, 2)  
(add(add, 6, mul(4, 6)))  # evaluates a nested expression
add(2, 3)  # add is operator, 2, 3 are operands; operators and operands are expressions
```

### Call Expressions
- Applying a function to some arguments is done with a call expression.

The syntax of a function call:
```py
  add   (    2   ,    3   )
   |         |        |
operator  operand  operand
```

Evaluation Procedure for Call Expressions:

1) Evaluate the operator
2) Evluate the operands from left to right
3) Apply the operator (a function) to the evaluated operands (arguments)

## Lecture 2, 06/22/21: Functions, Values, Objects, Interpreters, & Data

### Types of Expressions

- Primitive expressions
  - Only take one step to evaluate
  - Include numbers and booleans, which evalutate to themselves

- Arithmetic expressions
  - Numbers can be combined with mathematical operators to form compound expressions
  - Operators: `+`, `-`, `*`, `**`, etc.
  - Floating point division `/`: divides the first number by the second and evaluates it to a *float*, a number with a decimal point
  - Floor division `//`: divides the first number by the second, then rounds down
  - Modulo `%`: evaluates to the positive remainder left over from division
    - Arithmetic expressions are evaluated in `PEMDAS` order
  
  *Example:* check whether a integer `x` is divisble by another integer `y`
  ```py
  >>> x = 5
  >>> y = 3
  >>> x % y == 0
  False
  ```

### Assignment Statements
- `a = (100 + 50) // 2 `
  - Consists of a name (`a`) and an expression (`(100 + 50) // 2`)
  

### Values

Integers, strings, floats, booleans; represent different types of data; programs manipulate values

### Names

Values can be assigned to names (variables), which can only be found to a single value; statements affect the program but do not evaluate to values; names are expressions; 

A function call is **not** a name; it re-evaluates

### Discussion Question 1

```py
f = max
g = min
h = max
max = g
result = max(f(2, g(h(1, 5), 3)), 4)
print(result)  #  min(max(2, min(max(1, 5), 3)), 4)
```

### Environment Diagrams Preview (not comprehensive)

- [Online Python Tutor](http://pythontutor.com/composingprograms.html#mode=edit)
- Names are bound to **values** in an *environment*

### Defining Functions

```py
def <name>(<parameters>):  # function signature
    return <return expression>  #body
```
- Note that we don't actually enter inside the function until we call the function; how do we know this? That's why we create environment diagrams, which allow us to "look under the hood."

### Calling User-Defined Functions

1) Create a new *environment frame*
2) Bind the function's parameters to its arguments in that frame
3) Execute the body of the function in the new argument

<img src="images/../../images/environment-diagram.png" alt="drawing" width="300"/>

### Environments
A sequence of frames; so far, we've seen the global frame and a function's local frame

## Lecture 3, 06/23/21: Control

### None

`None` returns nothing in python

A function that does not explicitly return a value will return `None`

`None` is displayed as a value of an expression

### Pure Functions & Non-Pure Functions

- **Pure functions:** just return values
  - `abs(-2)` returns `2`
- **Non-Pure functions:** has a side effect that comes as a result of calling the function
  - `print(-2)` returns `None` but prints `-2`
    - the side effect is `-2` because the function truly evaluates to `None`

### Environments

An environment is a sequence of frames, which could include the *global frame alone* or *a local, then the global frame*. The global frame is the **last frame** of every environment.

Function creation and execution:

1) Function is created
2) Name is bound to that function in the current frame
3) Operator & operands evalauted
4) Function called on arguments

Creation of frames:

1) Start in the global frame
2) Opening frames starts with `f1` for "frame 1"
3) Every time we call a function, we open a new frame

### Demo

- `dir(<directory name>)` allows us to find all the methods in a directory, while `help(<directory name>)` shows help information

Example:
```py
>>> import operator
>>> dir(operator)
['__abs__', '__add__', '__all__', '__and__', '__builtins__', ...]
```

### Compound Statements

- A suite is a sequence of statements
- To "execute" a suite means to execute its sequence of statements, in order

Use `%` and `//` when we iterating through a bigger number

## Lecture 4, 06/24/21: Higher Order Functions

[Prerecorded Lecture Playlist](https://www.youtube.com/playlist?list=PLx38hZJ5RLZeBqIUj6ud1Ly-41dpqKX-L)

### The Fibonacci Sequence

Every element after 0 and 1 are the sum of the previous two elements: `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...`; the position of each number in the sequence is associated with its index, starting at 0

```py
def fib(n)
  """ Compute the nth Fibonacci number, starting with curr 0. """
  pred, curr = 1, 0
  k = 0
  while k < n:
    pred, curr = curr, pred + curr
    k = k + 1
  return curr
```

### Characteristics of Functions

- Domain - set of all inputs a function can take as arguments
- Range - set of output values it might return
- Pure function's behavior is the relationship it creates between input and output

Example:
```py
def square(x):  # domain - x is a real number
  """ Return X * X """
  return x * x # range: returns a non-negative real number
# behavior: return value is the square of the input
  ```

- Each function should have exactly one job but apply to many related situations

### Higher Order Functions

A higher order function is a function that takes in another function as an argument **and/or** returns another function
- they allow us to design functions by expressing general patterns of computation, remove repetition from programs, and separate concerns among functions (each function has one job)


### A Function That Returns a Function

```py
def make_adder(n):
  """ Return a function that takes one argument K and return K + N.

  >>> add_three = make_adder(3)
  >>> add_three(4)
  7
  """
  def adder(k):
    return k + n
  return adder
  ```
  
  - `make_adder()` is a function that returns a function
  - The name `add_three` is bound to `make_adder()`
  - `adder()` is a local function

### Lambda Expressions

Lambda expressions are expressions that evaluate to functions:
- `lambda <formal parameter>: <return expression>`
- In environment diagrams, lambda
- Only the def statement gives the funciton an intrinsic name, which shows up in environment diagrams; in environment diagrams, lambda shows up as $\lambda$ `<line #>`

```py
>>> x = 10
>>> square = x * x
>>> square = lambda x: x & x
```

## Lecture 5, 06/28/21: Environments

[Prerecorded Lecture Playlist](https://www.youtube.com/playlist?list=PLx38hZJ5RLZfbk5-asJKDq8p655M3EIXD)

### Environment Diagrams for Higher Order Functions

When you apply a user-defined function, you create a new frame and bind the formal parameters to arguments

### Environments for Nested Definitions

- **Every** used-defined function has a parent frame (often global)
- **Every** local frame has a parent frame (often global)
- The parent of a function is the frame within which it was created
- When a local frame returns something, it closes

### Simplified Guide to Draw an Environment Diagram

1. **When a function is defined:**
   -  Create a function value: `func <name>(<formal parameters>) [parent=<parent>]`
   - Note that the **parent** is the **current frame**
   - Bind `<name>` to the function value in the current frame
2. **When a function is called:**
   - Add a local frame, titled with the `<name>` of the function being called
   - Copy the parent of the function to the local frame: `[parent=<label>`]
   - Bind the `<formal parameters>` to the arguments in the local frame
   - Execute the body of the function in the environment that starts with the local frame
3. **If we need to look up names in the environment:**
   - Follow the parent of the parent of the parent of the frame until we reach the global frame; the value used is wherever the name is found first

### Complete Guide to Environment Diagrams

[Prerecorded Lecture Playlist](https://www.youtube.com/watch?v=bGD728MVwcc&ab_channel=KevinLin)

#### Assignment Statements

1. Evaluate the expression on the right hand side of the equals sign
2. Bind the value to the name on the left hand side in the current frame

#### Def Statements

1. Create a binding for the name of the function with its value being the function object
   - Parent of the function is **the frame in which the function is defined in**
   - Frames have no duplicate names
2. Squirrel away (skip) the body of the function and go to the next line on the same indentation level

#### Return Statements

1. Evaluate the expression to the right of the return
2. Create a little space for the return value, which is the evaluated expression
   - Not a *binding*

#### Primitive Expression

1. In the current environment (ex. f1, then global in this order) return the value of the name
   - It could evaluate to something like a number or string

#### Call Expression

1. Evaluate the operator
2. Evaluate the operands from left to right
3. Apply the operator  (evaluated as a function) to the operands (evaluated as arguments)
4. Create a new frame in the environment diagram

#### Make a new frame

1. Create a new space for this frame (this will be provided on the exam)
2. Fill out the header with information from the function signature
   - Copy down the intrinsic name of the function
   - Copy down the parent frame
   - Copy down the formal parameter names
3. Bind the arguments to their formal parameters


### Currying

**Currying:** the act of transforming a multi-argument function into a single-argument, higher-order function

The famed `make_adder()` function now comes in $\lambda$ form!

```py
def make_adder(n):
  return lambda k: n + k
```

Check out `curry2()`, that turns two argument functions into higher order functions:
```py
def curry2(f):
  """ Define function g(x) that takes 1 arg that defines a func h that takes 1 arg, which returns f called on x and y.

  >>> m = curry2(add)
  >>> add_three = m(3)
  >>> add_three(2)
  5
  >>> add_three(2018)
  2021
  """
  def g(x):
    def h(y):
      return f(x, y)
    return h
  return g
```
  
  Alternatively, `curry2()` could be defined in terms of $\lambda$ functions:
  ```py
  curry2 = lambda f: lambda x: lambda y: f(x, y)

  m = curry2(add)
  m(2)(3)  # outputs 5
  ```

## Lecture 6, 06/29/21: Recursion

### Recursive Functions

**Defniition:** a function is called recursive if the body of that function calls itself, either directly or indirectly

**Implication:** Executing the body of a recursive function may require evaluating the function

Hide the implementation of a function; all we need to know what the function takes in and returns

### Sum Digits Without a While Loop

```py
def sum_digits(n):
  if n < 10:
    return n
  else:
    all_but_liast, last = split(n)
    return sum_digits(all_but_last) + last
```

### The anatomy of a recursive function

- The def statement header is similar to other functions
- Conditional statements check for **base cases**
- Base cases are evaluated **without recursive calls**
- Recursive cases are evaluated **with recursive calls**
- Ex: each call to a function within a function solves a simpler problem than the last (smaller parameter)

### The Recursive Leap of Faith

Factorial:

```py
def fact(n):
  if n == 0:
    return 1
  else:
    return n * fact(n - 1)
```

1. Verify the base case
2. Treat **fact** as a functional abstraction
3. Verify that fact(n) is correct

### Abstraction

**Functional abstraction** - giving a name to some computational process, then referring to that process without worrying about the details of its implementation

Naming Conventions for Values:

- `n, k, i` - usually integers
- `x, y, z` - usually real numbers
- `f, g, h` - usually functions

## Lecture 7, 06/29/21: Tree Recursion

[Prerecorded Lecture Playlist](https://www.youtube.com/playlist?list=PLx38hZJ5RLZeBe3OhI9jWlpvAUXd_Aie1)

### Tree Recursion

**Tree Recursion** - the tree-shaped processes that arise whenever executing the body of a recursive function makes more than one call to that function

```py
def fib(n):
  if n == 0:  # base case 1
    return 0
  elif n == 1:  # base case 2
    return 1
  else:
    return fib(n-2) + fib(n-1)  # more than one call to fib() in the body of fib()
```

```md
              fib(5)
              /    \
             /      \
            /        \
           /          \
        fib(3)         \
       /    \        fib(4)
      /      \        /    \
     /        \     etc.   etc.
   fib(1)   fib(2)    
     |        /  \
     1   fib(2)  fib(1)
            |       |
            0       1
```

### Towers of Hanoi

The Towers of Hanoi problems shows us two things:

1) the power and beautify of recursion
2) exponential growth


```py
def move_disk(disk_number, from_peg, to_peg):
  print("Move disk " + str(disk_number) + " from peg " \
    + str(from_peg) + " to peg " + str(to_peg) + ".") 
```

```py
def solve_hanoi(n, start_peg, end_peg):  # (3, 1, 2) 3 disks from peg 1 to peg 2
  if n == 1:  # base case is 1 disk
    move_disk(n, start_peg, end_peg)  # print out instruction
  else:
    spare_peg = 6 - start_peg - end_peg
    solve_hanoi(n - 1, start_peg, spare_peg)  # (top, start, spare)
    move_disk(n, start_peg, end_peg)
    solve_hanoi(n - 1, spare_peg, end_peg)
```

### Counting Partitions

Count_partitions(6, 4) - counts the number of ways that 6 can be broken into groups of partitions up to size 4

```py
def count_partitions(n, m):
  if n == 0:
    return 1
  elif n < 0:
    return 0
  elif m == 0:
    return 0
  else:
    with_m = count_partitions(n - m, m)
    without_m = count_partitions(n, m-1)
    return with_m + without_m
```

## Lecture 8, 06/29/21: Functional Decomposition + Debugging

[Prerecorded Lecture Playlist](https://www.youtube.com/watch?v=AI7JJK2_e5c&ab_channel=CS61ADepartmental)


## Lecture 9, 07/06/21: Sequences + Data Abstraction

[Prerecorded Lecture Playlist](https://www.youtube.com/playlist?list=PLx38hZJ5RLZdfTyZcuvzBcJ1raFJtdC-h)

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 10, 07/07/21: Trees

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 11, 07/08/21: Mutable Sequences

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 12, 07/12/21: Complexity

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 13, 07/13/21: Iterators + Generators

### Subheade 1

### Subheader 2

### Subheader 3


## Lecture 14, 07/14/21: Midterm Review

### Reminder: Midterm is tomorrow!

### Subheader 1

### Subheader 2

### Subheader 3
```
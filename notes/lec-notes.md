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
    - [Environment Diagrams](#environment-diagrams)
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
    - [Environment Diagrams](#environment-diagrams-1)
  - [Lecture 5, 06/28/21: Environments](#lecture-5-062821-environments)
    - [Environment Diagrams for Higher Order Functions](#environment-diagrams-for-higher-order-functions)
    - [Environments for Nested Definitions](#environments-for-nested-definitions)
    - [Simplified Guide to Draw an Environment Diagram](#simplified-guide-to-draw-an-environment-diagram)
  - [Lecture 6, 06/29/21: Recursion](#lecture-6-062921-recursion)
    - [Subheader 1](#subheader-1)
    - [Subheader 2](#subheader-2)
    - [Subheader 3](#subheader-3)
  - [Lecture 7, 06/29/21: Tree Recursion](#lecture-7-062921-tree-recursion)
    - [Subheader 1](#subheader-1-1)
    - [Subheader 2](#subheader-2-1)
    - [Subheader 3](#subheader-3-1)
  - [Lecture 8, 06/29/21: Functional Decomposition + Debugging](#lecture-8-062921-functional-decomposition--debugging)
    - [Reminder, Diagnostic test is tomorrow: Friday, July 2nd](#reminder-diagnostic-test-is-tomorrow-friday-july-2nd)
    - [Subheader 1](#subheader-1-2)
    - [Subheader 2](#subheader-2-2)
    - [Subheader 3](#subheader-3-2)


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

### Environment Diagrams

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

### Environment Diagrams

- When a local frame returns something, it closes
- Show the state of the code when it's finished running

## Lecture 5, 06/28/21: Environments

[Prerecorded Lecture Playlist](https://www.youtube.com/playlist?list=PLx38hZJ5RLZfbk5-asJKDq8p655M3EIXD)

### Environment Diagrams for Higher Order Functions

When you apply a user-defined function, you create a new frame and bind the formal parameters to arguments

### Environments for Nested Definitions

- **Every** used-defined function has a parent frame (often global)
- **Every** local frame has a parent frame (often global)
- The parent of a function is the frame within which it was created

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


## Lecture 6, 06/29/21: Recursion

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 7, 06/29/21: Tree Recursion

### Subheader 1

### Subheader 2

### Subheader 3


## Lecture 8, 06/29/21: Functional Decomposition + Debugging

### Reminder, Diagnostic test is tomorrow: Friday, July 2nd

### Subheader 1

### Subheader 2

### Subheader 3
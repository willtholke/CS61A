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
  - [Lecture 4, 06/24/21: .](#lecture-4-062421-)


## Lecture 1, 06/22/21: Expressions

### Expressions & Statements

An expression is a peice of code that describes computation and evaluates to some value while a *statement* is one or more lines of code that make something happen in a program; ex: expression is `1 + 2`, value is `3`

- all expressions can be written in **f(x)** form; all values are expressions, but not all expressions are values

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

<img src="images/environment-diagram.png" alt="drawing" width="300"/>

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

## Lecture 4, 06/24/21: .


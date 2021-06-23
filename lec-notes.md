# CS 61A: Structure & Interpretation of Computer Programs

    University of California, Berkeley
    Instructors: Albert Xu, Alex Kassil, Catherine Cang
    Emails: albertxu3@berkeley.edu, alexkassil@berkeley.edu,  catherinecang@berkeley.edu
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
  - [Lecture 3, 06/23/21: TBD](#lecture-3-062321-tbd)
    - [Control Statements](#control-statements)
    - [Short Circuiting](#short-circuiting)
    - [Interesting While Loop Example](#interesting-while-loop-example)
    - [Subheader 3](#subheader-3)
    - [Subheader 4](#subheader-4)


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

## Lecture 3, 06/23/21: TBD

### Control Statements

Control statements control the flow of a program's execution based on the results of logical comparisons; statements have no value
- Expressions -> evaluated
- Statements -> executed

Python's three boolean operators, `and`, `or`, and `not`, have an order of operation:
- `not` has the highest priority
- `and`
- `or` has the lowest priority

Python's boolean operators work on more than booleans (`True`, `False`): `0`, `None`, `''`, and `[]` are all considered false values; all other values are considered true.

### Short Circuiting

Short-circuiting occurs when the operator arrives an an operand that allows the operator to make a conclusion about the expression. If `and` or `or` do not short-circuit, they return the last thing they evaluate.

Cases:
1) `<left>` **and** `<right>` (remember as "False and")
   - Evaluate `<left>`
   - If result is false value `v`, expression evaluates to `v`
   - Otherwise, expression evalutes to the value of `<right>`
     - `<left>` and `<right>` are subexpressions

2) `<left>` **or** `<right>` (remember as "True or")
   - Evaluate `<left>`
   - If result is true value `v`, expression evaluates to `v`
   - Otherwise, expression evalutes to the value of `<right>`
     - `<left>` and `<right>` are subexpressions
3) Not `<exp>` (remember as "opposite")
   - Evaluate `<exp>`
     - The value is `True` if the result evaluates to `False`
     - The value is `False` if the result evaluates to `True`



Examples:
```py
>>> True and 1 / 5
0.2
>>> True and 1 / 0
ZeroDivisionError: division by zero
>>> False and 1 / 5
False
>>> False and 1 / 0
False
>>> True or 1 / 0
True
>>> True or 1/5
True
```


### Interesting While Loop Example

In the example below, the interpreter exits the function when the condition being evaluated by the while loop is false-y. All non-zero values are truth-y in python, but `0` is false-y, hence why the while loop breaks.

``` py
>>> positive = -9
>>> negative = -12
>>> while negative: # If this loops forever, just type Infinite Loop
...    if positive:
...        print(negative)
...    positive += 3
...    negative += 3
```


### Subheader 3

### Subheader 4
CS61A: Structure & Interpretation of Computer Programs
=====

```md
University of California, Berkeley
Summer Session X
Albert Xu, Alex Kassil, Catherine Cang
Emails: albertxu3@berkeley.edu, alexkassil@berkeley.edu, catherinecang@berkeley.edu
Office Hours: cs61a.org/office-hours/
Mon/Tues/Thurs/Fri 12:30pm-2:00pm
```

## Lecture 1, 06/22/21: Expressions

---

**Expression**: describes computation and evalutes to values; ex: expression is `1 + 2`, value is `3`; all expressions can be written in **f(x)** form; all values are expressions, but not all expressions are values:

```py
from operator import add, mul
add(1, 2)  # identical to  1 + 2, evaluates to a value of 3
(add(add, 6, mul(4, 6)))  # evaluates a nested expression
add(2, 3)  # add is operator, 2, 3 are operands; operators and operands are expressions
```

**Evaluation procedure for call expressions:**

1) evaluate the oeprator
2) Evluate the operands from left to right
3) Apply the operator (a function) to the evaluated operands (arguments)

## Lecture 2, 06/22/21: Functions, Values, Objects, Interpreters, & Data

### *Key concepts for review:* environment diagrams, functions

---

**Types of expressions:** primitive expressions (2, 'hello'), call expressions (add(2, 3)); the operands `2` and `3` can be call expressions

**Values:** integers, strings, floats, booleans; represent different types of data; programs manipulate values

**Names:** values can be assigned to names (variables), which can only be found to a single value; statements affect the program but do not evaluate to values; names are expressions; 

- a function call is **not** a name; it re-evaluates

**Discussion Question 1:**

```py
f = max
g = min
h = max
max = g
result = max(f(2, g(h(1, 5), 3)), 4)
print(result)  #  min(max(2, min(max(1, 5), 3)), 4)
```

**Environment Diagrams:**

- [Online Python Tutor](http://pythontutor.com/composingprograms.html#mode=edit)
- Names are bound to **values** in an *environment*

**Defining Functions:**

```py
def <name>(<parameters>):  # function signature
    return <return expression>  #body
```

We don't enter inside the function until we call the function.

**Calling User-Defined Functions:**

1) Create a new *environment frame*
2) Bind the function's parameters to its arguments in that frame
3) Execute the body of the function in the new argument

<img src="images/environment-diagram.png" alt="drawing" width="200"/>

**Environment:** sequence of frames; so far, we've seen the global frame and a function's local frame


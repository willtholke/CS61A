# CS 61A: Structure & Interpretation of Computer Programs

    University of California, Berkeley
    Instructors: Albert Xu, Alex Kassil, Catherine Cang
    albertxu3@berkeley.edu, alexkassil@berkeley.edu,  catherinecang@berkeley.edu
    Office Hours: cs61a.org/office-hours/
    Lecture: Mon/Tues/Thurs/Fri 12:30pm-2:00pm
    Author: Will Tholke

## Lab 00 Notes

### Commands

- `ls` lsits all the files and folders in the current **directory**, which is another name for a folder
- `cd` changes directory; try `cd Desktop`
- `cd ..` & `cd ~` or `cd` returns to the home directory
- `mkdir` makes a directory
- `mv <source path> <destination path>` moves a flie at the given source to the diven destination

### Lab Workflow

1. cd ~/Downloads
2. unzip lab00.zip
3. mv ~/Downloads/lab00 ~/Desktop/cs61a/lab
4. cd ~/Desktop/cs61a/lab/lab00

## Lab 01 Notes

### Modulo and Floor

- If you floor divide a number by 10, it removes the right digit: `123 // 10 = 10`
- If you mod 10 a number, you get the right digit: `123 % 10 = 3`

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

### Return Values

When a function or expression doesn't return anything, it implicitly returns none:
- `print(print(2))` evaluates `print(2)`, which prints `2` and returns `None`, and then evaluates `print(None)` and prints `None` 

### Debugging Overview

Check out the [cs61a.org article on debugging](https://cs61a.org/articles/debugging/)

Traceback messages print out the chain of functions calls that led up to any given error, with the most recent function call at the bottom (hence the line `Traceback (most recent call last)` that might accompany your error message)

    File "<file name>", line <number>, in <function>

### Debugging Techniques

1. Run doctests, which are lines in the docstring that look like interpreter outputs. Here's an example:

```py
def foo(x):
  """ This function accomplishes some purpose

  >>> foo(100)  # the start of the doctest
  100

  >>> foo(1)
  1
  """
  ```

  Run doctests in terminal with the following line of code, which loads the .py file into the Python interpreter and checks if each doctest is identical to the desired output (`-m` stands for module & `-v` indicates verbose)

  ```
  python3 -m doctest file.py  # tells which doctests failed
  ```

  ```
  python3 -m doctest file.py -v  # verbose option, tells which doctests failed/passed
  ```

  2. Add print statements into your code to spot bugs
  
Make sure to prefix debug statements with the string `'DEBUG:'` since the `ok` autograder might read print statements otherwise (`ok` tests *all* of the output of your code)

```py
def foo(x):
  y = x + 5
  print(f'DEBUG: result is {y}')
  return y
```

3. Long-term debugging

Try adding a global variable `debug = True` along with an if statement in any function you might want to consistently test; if `debug` evalutes to `True`, run the `print('DEBUG: ...')` statement.

```py
debug = True

def foo(x):
  y = x + 5
  if debug:
    print('DEBUG: result is', y)
```

4. Interactive debugging

Use an interactive REPL, a terminal to directly run functions and inspect their outputs; try running

    python3 -i file.py

Jump to the middle of a failing test case with the autograder with

    python3 ok -q <question name> -i

Open up PythonTutor with your code to create an environment diagram to debug

    python3 ok -q <question name> --trace
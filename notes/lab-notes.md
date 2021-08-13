# CS 61A: Structure & Interpretation of Computer Programs

    University of California, Berkeley
    Instructors: Albert Xu, Alex Kassil, Catherine Cang
    albertxu3@berkeley.edu, alexkassil@berkeley.edu, catherinecang@berkeley.edu
    Office Hours: cs61a.org/office-hours/
    Lecture: Mon/Tues/Thurs/Fri 12:30pm-2:00pm
    Author: Will Tholke

### Relevant Terminal Commands

- `ls` lsits all the files and folders in the current **directory**, which is another name for a folder
- `cd` changes directory; try `cd Desktop`
- `cd ..` & `cd ~` or `cd` returns to the home directory
- `mkdir` makes a directory
- `mv <source path> <destination path>` moves a flie at the given source to the diven destination

### Terminal Workflow

1. `cd ~/Downloads`
2. `unzip lab##.zip`
3. `mv ~/Downloads/lab00 ~/Desktop/cs61a/lab`
4. `cd ~/Desktop/cs61a/lab/lab00`

### Overview: Debugging

*Note:* Check out the [cs61a.org article on debugging](https://cs61a.org/articles/debugging/)

Traceback messages print out the chain of functions calls that led up to any given error, with the most recent function call at the bottom (hence the line `Traceback (most recent call last)` that might accompany your error message)

    File "<file name>", line <number>, in <function>

**Debugging Techniques:**

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

Try adding a global variable `debug = True` along with an if statement in any function you might want to consistently test; if `debug` evalutes to `True`, run the `print('DEBUG: ...')` statement

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
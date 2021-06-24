# CS 61A: Structure & Interpretation of Computer Programs

    University of California, Berkeley
    Instructors: Albert Xu, Alex Kassil, Catherine Cang
    albertxu3@berkeley.edu, alexkassil@berkeley.edu,  catherinecang@berkeley.edu
    Office Hours: cs61a.org/office-hours
    Lecture: Mon/Tues/Thurs/Fri 12:30pm-2:00pm
    Author: Will Tholke

    Teaching Assistant: Laryn Qi
    Larynqi@berkeley.edu
    links.cs61a.org/laryn
    links.cs61a.org/laryn-feedback

## Session 1, 06/23/21

### Evaluation order

1. Evaluate operator
2. Evaluate operands
3. Apply operator to operands

### Example problems

1. Write a function that returns true if a number is divisble by 4 and false otherwise
   
```py
def foo(num):
  if num % 4 == 0:
    return True
  else:
    return False

# OR

def bar(num):
  return num % 4 == 0
 ```

2. Write a function, `is_leap_year`, that returns true if a number is a leap year and false otherwise. `leap year` is a year that is divisible by 4 but not divisble by 400.

```py
def is_leap_year(year):
  if (year % 4 == 0) and year % 400 is not True:
    return True
  return False
```

3. Write a function `find.max` that will take in 3 numbers, x, y, z, and return the max value. Assume that

```py
N/A
```
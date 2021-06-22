# CS61A Lecture Notes: 6-21-21

<!-- ## Table of Contents

1. [What is Computer Science?](#what-is-computer-science?)

--- -->

## Overview

### Announcements

1. Lab 00 released
2. Vitamin 00 due Thursday, June 24th, 2021
3. HW 01 released Tuesday, June 22, 2021
4. Discussion & office hours start Tuesday, June 22, 2021
5. Lab party starts Wednesday, June 23, 2021
6. Sign-ups for small group tutoring start Tuesday, June 22, 2021

### Resources

1. cs61a.org; course hub
2. edstem.org; like Piazza
3. okpy.org; submit all coding assignments here
4. howamidoing.cs61a.org; check grades in convenient online interface
5. oh.cs61a.org; get help
6. cs61a.org/office-hours/; office hours

---

## Course Format

- **Course Lecture:** 12:30 - 2:00pm, M-Th on Zoom
- **Duration**: 8 weeks long
- **Textbook:** composingprograms.com, can be used as a lecture recap or to study for exams
- **Assignments:** 8 programming homeworks, 4 programming projects, 1 diagnostic quiz, 1 midterm exam, 1 final exam
- **Discussions:** attendance points, 90 mins 2x/week
- **Lab Party (optional):** 1 hour long, best place to work on labs; M/W, 4-5pm; M/W 5-6pm; T/Th 10-11am; T/Th 11am-12pm
- **Office Hours:** three formats; OH Queue, great for conceptual help, assignment help, and exam prep; Parties, 1 hour each, 2 types (lab/project), work with students & staff; Intructor, meet with the course instructors
- **Small Group Tutoring Sections (optional):** optional, recurring small-group sections (5-8 students) centered around a worksheet, meet Wed/Fri regularly, you must attend if you sign up

## Grading

Not curved; grade is based on how many points you earn over the course of the semester; graded on 300 point scale;

- 5: diagnostic quiz
- 8: extra credit
- 11 (13 in total): vitamins (google forms, reflect the topics covered in lectures preceding discussion, due T 8am & Th 8am, graded on completion)
- 11: participation
- 18: lab (use autograder before submitting to see your score)
- 21: homework (1 per week; released on Th, due Wed; HW 1-7 are graded, HW 8 for extra credit)
- 99: projects
- 55: midterm (Thursday July 15, 5-7 PM)
- 80: final (Thursday, August 12, 5-8 PM)

## Alternatives to CS 61A

**CS10: The Beauty and Joy of Computing** – an introduction to fundamentals (& Python) that sets students up for success in CS 61A

**Data 8: The Foundations of Data Science** – fundamentals of computing, statistical inference, & machine learning applied to real-world data sets

## What is Computer Science?

**Computer science** is the overarching term that describes the mechanism through which we approach problem-solving using computers. Effective solutions might consist of techniques involving *systems, artificial intelligence, graphics, security, networking, programming languages, or theory*.

## What is CS 61A?

- Managing complexity with **abstraction**
- Introduction to programming: full understanding of Python fundamentals, combining ideas in large projects, how computers interpret programming languages

---

## Expressions

**Interpreter** - Enter `python3` in terminal

**Expressions** describe computation and evalute to values:

- Expression: 1 + 2
- Value: 3

**Note:** All expressions can be written in **f(x)** form; all values are expressions, but not all expressions are values:

```py
from operator import add, mul
add(1, 2)  # identical to  1 + 2
(add(add, 6, mul(4, 6)))  # evaluate a nested expression
add(2, 3)  # add is operator, 2, 3 are operands; operators and operands are expressions
```

**Evaluation procedure for call expressions:**

1) evaluate the oeprator
2) Evluate the operands from left to right
3) Apply the operator (a function) to the evaluated operands (arguments)

## Functions, Values, Objects, Interpreters, & Data


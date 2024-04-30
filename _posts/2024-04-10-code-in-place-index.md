---
layout: post
title: Code in Place from Stanford University - Week 1
---
# Introduction
[Student home](https://codeinplace.stanford.edu/cip4/studenthome) - main page for Stanford's Code in Place

[Karel Reader](https://compedu.stanford.edu/karel-reader/docs/python/en/intro.html) - essentially the textbook for Karel

[Karel Helper](https://karelhelper.com) 


[Python docs](https://docs.python.org/3/) - straight from the source

[Python style guide (PEP8)](https://pep8.org/)

[PyCharm Community Edition](https://www.jetbrains.com/pycharm/download) - the main IDE that Stanford suggests

## Notes

**SOFTWARE ENGINEERING PRINCIPLE**: Aim to make programs readable by **humans**.

### for loop
```py
for i in range(count):
    statements
```

```py
def turn_right():
    for i in range(3):
        turn_left()
```

**NOTE**: You need the **postcondition** of a loop to match the **precondition**. 

### while loop
```py
while condition:
    statements
```
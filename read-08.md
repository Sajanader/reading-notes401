# read-08
## List Comprehensions in Python
List comprehensions provide a concise way to create lists.

It consists of brackets containing an expression followed by a for clause, then
zero or more for or if clauses. The expressions can be anything, meaning you can
put in all kinds of objects in lists.


* The result will be a new list resulting from evaluating the expression in the
context of the for and if clauses which follow it.

The list comprehension always returns a result list.

If you used to do it like this:
```
new_list = []
for i in old_list:
    if filter(i):
        new_list.append(expressions(i))
```        

**You can obtain the same thing using list comprehension**.
```
new_list = [expression(i) for i in old_list if filter(i)]
Syntax
```
The list comprehension starts with a ‘[‘ and ‘]’, square brackets, to help you remember that the
result is going to be a list.

The basic syntax uses square brackets.
```
[ expression for item in list if conditional ]
This is equivalent to:

for item in list:
    if conditional:
        expression
```
### Example:
Create a simple list
Let’s start easy by creating a simple list.
```
x = [i for i in range(10)]
print x
```

### This will give the output:
``
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]``

### To Create a list using loops and list comprehension
For the next example, assume we want to create a list of squares. Start with an empty list.

### You can either use loops:
```
squares = []

for x in range(10):
    squares.append(x**2)
 
print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### Or you can use list comprehensions to get the same result:
```
squares = [x**2 for x in range(10)]

print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

```
------------------------
## Primer on Python Decorators
### Returning Functions From Functions
Python also allows you to use functions as return values. The following example returns one of the inner functions from the outer parent() function:

def parent(num):
    def first_child():
        return "Hi, I am Emma"

    def second_child():
        return "Call me Liam"

    if num == 1:
        return first_child
    else:
        return second_child
Note that you are returning first_child without the parentheses. Recall that this means that you are returning a reference to the function first_child. In contrast first_child() with parentheses refers to the result of evaluating the function. This can be seen in the following example:

>>> first = parent(1)
>>> second = parent(2)

>>> first
<function parent.<locals>.first_child at 0x7f599f1e2e18>

>>> second
<function parent.<locals>.second_child at 0x7f599dad5268>
The somewhat cryptic output simply means that the first variable refers to the local first_child() function inside of parent(), while second points to second_child().

You can now use first and second as if they are regular functions, even though the functions they point to can’t be accessed directly:

>>> first()
'Hi, I am Emma'

>>> second()
'Call me Liam'
Finally, note that in the earlier example you executed the inner functions within the parent function, for instance first_child(). However, in this last example, you did not add parentheses to the inner functions—first_child—upon returning. That way, you got a reference to each function that you could call in the future. Make sense?

### Simple Decorators
Now that you’ve seen that functions are just like any other object in Python, you’re ready to move on and see the magical beast that is the Python decorator. Let’s start with an example:
```
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

def say_whee():
    print("Whee!")

say_whee = my_decorator(say_whee)
Can you guess what happens when you call say_whee()? Try it:
```
>>> say_whee()
Something is happening before the function is called.
Whee!
Something is happening after the function is called.
To understand what’s going on here, look back at the previous examples. We are literally just applying everything you have learned so far.

The so-called decoration happens at the following line:

say_whee = my_decorator(say_whee)
In effect, the name say_whee now points to the wrapper() inner function. Remember that you return wrapper as a function when you call my_decorator(say_whee):

>>> say_whee
<function my_decorator.<locals>.wrapper at 0x7f3c5dfd42f0>
However, wrapper() has a reference to the original say_whee() as func, and calls that function between the two calls to print().

### Put simply: decorators wrap a function, modifying its behavior.

Before moving on, let’s have a look at a second example. Because wrapper() is a regular Python function, the way a decorator modifies a function can change dynamically. So as not to disturb your neighbors, the following example will only run the decorated code during the day:
```
from datetime import datetime

def not_during_the_night(func):
    def wrapper():
        if 7 <= datetime.now().hour < 22:
            func()
        else:
            pass  # Hush, the neighbors are asleep
    return wrapper

def say_whee():
    print("Whee!")

say_whee = not_during_the_night(say_whee)
If you try to call say_whee() after bedtime, nothing will happen:
```
>>> say_whee()
>>>
# read-07
## Functions: The Local Scope
The local scope or function scope is a Python scope created at function calls. Every time you call a function, you’re also creating a new local scope. On the other hand, you can think of each def statement and lambda expression as a blueprint for new local scopes. These local scopes will come into existence whenever you call the function at hand.

By default, parameters and names that you assign inside a function exist only within the function or local scope associated with the function call. When the function returns, the local scope is destroyed and the names are forgotten. Here’s how this works:

```
>>> def square(base):
...     result = base ** 2
...     print(f'The square of {base} is: {result}')
...
>>> square(10)
```

The square of 10 is: 100
```
>>> result  # Isn't accessible from outside square()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    result
NameError: name 'result' is not defined
>>> base  # Isn't accessible from 
```
outside square()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    base
NameError: name 'base' is not defined

>>> square(20)
The square of 20 is: 400
square() is a function that computes the square of a given number, base. When you call the function, Python creates a local scope containing the names base (an argument) and result (a local variable). After the first call to square(), base holds a value of 10 and result holds a value of 100. The second time, the local names will not remember the values that were stored in them the first time the function was called. Notice that base now holds the value 20 and result holds 400.

Note: If you try to access result or base after the function call, then you get a NameError, because these only exist in the local scope created by the call to square(). Whenever you try to access a name that isn’t defined in any Python scope, you’ll get a NameError. The error message will include the name that couldn’t be found.

Since you can’t access local names from statements that are outside the function, different functions can define objects with the same name. Check out this example:

>>> def cube(base):
...     result = base ** 3
...     print(f'The cube of {base} is: {result}')
...
>>> cube(30)
The cube of 30 is: 27000
Notice that you define cube() using the same variable and parameter that you used in square(). However, since cube() can’t see the names inside the local scope of square() and vice versa, both functions work as expected without any name collision.

You can avoid name collisions in your programs by properly using the local Python scope. This also makes functions more self-contained and creates maintainable program units. Additionally, since you can’t change local names from remote places in your code, your programs will be easier to debug, read, and modify.

You can inspect the names and parameters of a function using .__code__, which is an attribute that holds information on the function’s internal code. Take a look at the code below:

>>> square.__code__.co_varnames
('base', 'result')
>>> square.__code__.co_argcount
1
>>> square.__code__.co_consts
(None, 2, 'The square of ', ' is: ')
>>> square.__code__.co_name
'square'
In this code example, you inspect .__code__ on square(). This is a special attribute that holds information about the code of a Python function. In this case, you see that .co_varnames holds a tuple containing the names that you define inside square().


 Remove ads
Nested Functions: The Enclosing Scope
Enclosing or nonlocal scope is observed when you nest functions inside other functions. The enclosing scope was added in Python 2.2. It takes the form of the local scope of any enclosing function’s local scopes. Names that you define in the enclosing Python scope are commonly known as nonlocal names. Consider the following code:

>>> def outer_func():
...     # This block is the Local scope of outer_func()
...     var = 100  # A nonlocal var
...     # It's also the enclosing scope of inner_func()
...     def inner_func():
...         # This block is the Local scope of inner_func()
...         print(f"Printing var from inner_func(): {var}")
...
...     inner_func()
...     print(f"Printing var from outer_func(): {var}")
...
>>> outer_func()
Printing var from inner_func(): 100
Printing var from outer_func(): 100
>>> inner_func()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'inner_func' is not defined
When you call outer_func(), you’re also creating a local scope. The local scope of outer_func() is, at the same time, the enclosing scope of inner_func(). From inside inner_func(), this scope is neither the global scope nor the local scope. It’s a special scope that lies in between those two scopes and is known as the enclosing scope.

Note: In a sense, inner_func() is a temporary function that comes to life only during the execution of its enclosing function, outer_func(). Note that inner_func() is only visible to the code in outer_func().

All the names that you create in the enclosing scope are visible from inside inner_func(), except for those created after you call inner_func(). Here’s a new version of outer_fun() that shows this point:

>>> def outer_func():
...     var = 100
...     def inner_func():
...         print(f"Printing var from inner_func(): {var}")
...         print(f"Printing another_var from inner_func(): {another_var}")
...
...     inner_func()
...     another_var = 200  # This is defined after calling inner_func()
...     print(f"Printing var from outer_func(): {var}")
...
>>> outer_func()
Printing var from inner_func(): 100
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    outer_func()
  File "<stdin>", line 7, in outer_func
    inner_func()
  File "<stdin>", line 5, in inner_func
    print(f"Printing another_var from inner_func(): {another_var}")
NameError: free variable 'another_var' referenced before assignment in enclosing
 scope
When you call outer_func() the code runs down to the point in which you call inner_func(). The last statement of inner_func() tries to access another_var. At this point, another_var isn’t defined yet, so Python raises a NameError because it can’t find the name that you’re trying to use.

Last but not least, you can’t modify names in the enclosing scope from inside a nested function unless you declare them as nonlocal in the nested function. You’ll cover how to use nonlocal later in this tutorial.

Modules: The Global Scope
From the moment you start a Python program, you’re in the global Python scope. Internally, Python turns your program’s main script into a module called __main__ to hold the main program’s execution. The namespace of this module is the main global scope of your program.

Note: In Python, the notions of global scope and global names are tightly associated with module files. For example, if you define a name at the top level of any Python module, then that name is considered global to the module. That’s the reason why this kind of scope is also called module scope.

If you’re working in a Python interactive session, then you’ll notice that '__main__' is also the name of its main module. To check that out, open an interactive session and type in the following:

>>> __name__
'__main__'
Whenever you run a Python program or an interactive session like in the above code, the interpreter executes the code in the module or script that serves as an entry point to your program. This module or script is loaded with the special name, __main__. From this point on, you can say that your main global scope is the scope of __main__.

To inspect the names within your main global scope, you can use dir(). If you call dir() without arguments, then you’ll get the list of names that live in your current global scope. Take a look at this code:

>>> dir()
['__annotations__', '__builtins__',..., '__package__', '__spec__']
>>> var = 100  # Assign var at the top level of __main__
>>> dir()
['__annotations__', '__builtins__',..., '__package__', '__spec__', 'var']
When you call dir() with no arguments, you get the list of names available in your main global Python scope. Note that if you assign a new name (like var here) at the top level of the module (which is __main__ here), then that name will be added to the list returned by dir().

Note: You’ll cover dir() in more detail later on in this tutorial.

There’s only one global Python scope per program execution. This scope remains in existence until the program terminates and all its names are forgotten. Otherwise, the next time you were to run the program, the names would remember their values from the previous run.

You can access or reference the value of any global name from any place in your code. This includes functions and classes. Here’s an example that clarifies these points:

>>> var = 100
>>> def func():
...     return var  # You can access var from inside func()
...
>>> func()
100
>>> var  # Remains unchanged
100
Inside func(), you can freely access or reference the value of var. This has no effect on your global name var, but it shows you that var can be freely accessed from within func(). On the other hand, you can’t assign global names inside functions unless you explicitly declare them as global names using a global statement, which you’ll see later on.

Whenever you assign a value to a name in Python, one of two things can happen:

You create a new name
You update an existing name
The concrete behavior will depend on the Python scope in which you’re assigning the name. If you try to assign a value to a global name inside a function, then you’ll be creating that name in the function’s local scope, shadowing or overriding the global name. This means that you won’t be able to change most variables that have been defined outside the function from within the function.

If you follow this logic, then you’ll realize that the following code won’t work as you might expect:

>>> var = 100  # A global variable
>>> def increment():
...     var = var + 1  # Try to update a global variable
...
>>> increment()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    increment()
  File "<stdin>", line 2, in increment
    var = var + 1
UnboundLocalError: local variable 'var' referenced before assignment
Within increment(), you try to increment the global variable, var. Since var isn’t declared global inside increment(), Python creates a new local variable with the same name, var, inside the function. In the process, Python realizes that you’re trying to use the local var before its first assignment (var + 1), so it raises an UnboundLocalError.

Here’s another example:

>>> var = 100  # A global variable
>>> def func():
...     print(var)  # Reference the global variable, var
...     var = 200   # Define a new local variable using the same name, var
...
>>> func()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    func()
  File "<stdin>", line 2, in func
    print(var)
UnboundLocalError: local variable 'var' referenced before assignment
You likely expect to be able to print the global var and be able to update var later, but again you get an UnboundLocalError. What happens here is that when you run the body of func(), Python decides that var is a local variable because it’s assigned within the function scope. This isn’t a bug, but a design choice. Python assumes that names assigned in the body of a function are local to that function.
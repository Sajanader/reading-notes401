# read-03
## Exceptions versus Syntax Errors
### Syntax errors
 occur when the parser detects an incorrect statement. Observe the following example:
 ```
 >>> print( 0 / 0 ))
  File "<stdin>", line 1
    print( 0 / 0 ))
                  ^
SyntaxError: invalid syntax
```
The arrow indicates where the parser ran into the syntax error. In this example, there was one bracket too many. Remove it and run your code again:
 ```
 >>> print( 0 / 0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zero
```
This time, you ran into an exception error. This type of error occurs whenever syntactically correct Python code results in an error. The last line of the message indicated what type of exception error you ran into.

Instead of showing the message exception error, Python details what type of exception error was encountered. In this case, it was a ZeroDivisionError. Python comes with various built-in exceptions as well as the possibility to create self-defined exceptions.

After seeing the difference between syntax errors and exceptions, you learned about various ways to raise, catch, and handle exceptions in Python. In this article, you saw the following options:

* raise allows you to throw an exception at any time.
* assert enables you to verify if a certain condition is met and throw an exception if it isn’t.
* In the try clause, all statements are executed until an exception is encountered.
* except is used to catch and handle the exception(s) that are encountered in the try clause.
else lets you code sections that should run only when no exceptions are encountered in the try clause.
* finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.

![image](https://files.realpython.com/media/try_except_else_finally.a7fac6c36c55.png)

**Have a look at the following example:**
```
try:
    linux_interaction()
except AssertionError as error:
    print(error)
else:
    try:
        with open('file.log') as file:
            read_data = file.read()
    except FileNotFoundError as fnf_error:
        print(fnf_error)
finally:
    print('Cleaning up, irrespective of any exceptions.')
In the previous code, everything in the finally clause will be executed. It does not matter if you encounter an exception somewhere in the try or else clauses. Running the previous code on a Windows machine would output the following:
```
```
Function can only run on Linux systems.
Cleaning up, irrespective of any exceptions.
```

## what is file?
At its core, a file is a contiguous set of bytes used to store data. This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable. In the end, these byte files are then translated into binary 1 and 0 for easier processing by the computer.

Files on most modern file systems are composed of three main parts:

* Header: metadata about the contents of the file (file name, size, type, and so on)
* Data: contents of the file as written by the creator or editor
* End of file (EOF): special character that indicates the end of the file

![image](https://www.pythoninformer.com/img/language/files.png)

### open and close file in python 

**Character**
* 'r'	Open for reading (default)
* 'w'	Open for writing, truncating (overwriting) the file first
* 'rb' or 'wb'	Open in binary mode (read/write using byte data)

**There are three different categories of file objects:**

* Text files
* Buffered binary files
* Raw binary files

## ext File Types
A text file is the most common file that you’ll encounter. Here are some examples of how these files are opened:
```
open('abc.txt')

open('abc.txt', 'r')

open('abc.txt', 'w')
```
With these types of files, open() will return a TextIOWrapper file object:
```
>>> file = open('dog_breeds.txt')
>>> type(file)
<class '_io.TextIOWrapper'>
```
This is the default file object returned by open().

* Buffered Binary File Types
A buffered binary file type is used for reading and writing binary files. Here are some examples of how these files are opened:
```
open('abc.txt', 'rb')

open('abc.txt', 'wb')
```
With these types of files, open() will return either a BufferedReader or BufferedWriter file object:
```
>>> file = open('dog_breeds.txt', 'rb')
>>> type(file)
<class '_io.BufferedReader'>
>>> file = open('dog_breeds.txt', 'wb')
>>> type(file)
<class '_io.BufferedWriter'>
```
* Raw File Types
A raw file type is:

“generally used as a low-level building-block for binary and text streams.” (Source)

It is therefore not typically used.

Here’s an example of how these files are opened:
```
open('abc.txt', 'rb', buffering=0)
With these types of files, open() will return a FileIO file object:

>>> file = open('dog_breeds.txt', 'rb', buffering=0)
>>> type(file)
<class '_io.FileIO'>
```
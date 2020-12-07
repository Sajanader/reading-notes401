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

You can obtain the same thing using list comprehension.

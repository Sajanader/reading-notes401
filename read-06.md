# read-06
### Random functions
The Random module contains some very useful functions.

### Randint
If we wanted a random integer, we can use the randint function Randint accepts two parameters: a lowest and a highest number. Generate integers between 1,5. The first value should be less than the second.
```
import random
print random.randint(0, 5)

```
**This will output either 1, 2, 3, 4 or 5.**

### Random
If you want a larger number, you can multiply it.
 
For example, a random number between 0 and 100:
```
import random
random.random() * 100
```
#### Choice
Generate a random value from the sequence sequence.
```
random.choice( ['red', 'black', 'green'] ).
```

The choice function can often be used for choosing a random element from a list.
```
import random
myList = [2, 109, False, 10, "Lorem", 482, "Ipsum"]
random.choice(myList)
```
### Shuffle
The shuffle function, shuffles the elements in list in place, so they are in a random order.
```
from random import shuffle
x = [[i] for i in range(10)]
shuffle(x)
```
**Output:
 print x  gives  [[9], [2], [7], [0], [4], [5], [3], [1], [8], [6]]
 of course your results will vary**

### Randrange
Generate a randomly selected element from range(start, stop, step)
```
random.randrange(start, stop[, step])
import random
for i in range(3):
    print random.randrange(0, 101, 5)
```
Code Example
Let’s see this example (copied from Doug Hellmann PYMOTW)
```
import random
import itertools

outcomes = { 'heads':0,
             'tails':0,
             }
sides = outcomes.keys()

for i in range(10000):
    outcomes[ random.choice(sides) ] += 1

print 'Heads:', outcomes['heads']
print 'Tails:', outcomes['tails']
```
There are only two outcomes allowed, so rather than use numbers and convert them, the words “heads” and “tails” are used with choice().

The results are tabulated in a dictionary using the outcome names as keys.
```
$ python random_choice.py

Heads: 4984
Tails: 5016
```
----------------------------------
## Why use Risk Analysis?
In any software, using risk analysis at the beginning of a project highlights the potential problem areas. After knowing about the risk areas, it helps the developers and managers to mitigate the risks. When a test plan has been created, risks involved in testing the product are to be taken into consideration along with the possibility of the damage they may cause to your software along with solutions.
![image](https://www.synopsys.com/blogs/software-security/wp-content/uploads/2004/05/sdlc-graphic.jpg)

----------------------------
## dependency injection
Why should I use dependency injection?
Let’s say we have a car class which contains various objects such as wheels, engine, etc.

Here the car class is responsible for creating all the dependency objects. Now, what if we decide to ditch MRFWheels in the future and want to use Yokohama Wheels?

We will need to recreate the car object with a new Yokohama dependency. But when using dependency injection (DI), we can change the Wheels at runtime (because dependencies can be injected at runtime rather than at compile time).

You can think of DI as the middleman in our code who does all the work of creating the preferred wheels object and providing it to the Car class.

It makes our Car class independent from creating the objects of Wheels, Battery, etc.

**There are basically three types of dependency injection:**
1. constructor injection: the dependencies are provided through a class constructor.
2. setter injection: the client exposes a setter method that the injector uses to inject the dependency.
3. interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.
So now its the dependency injection’s responsibility to:
![image](https://cdn-media-1.freecodecamp.org/images/1*0P-1JhnUaZeobDUAajIbhA.jpeg)
#### Create the objects
Know which classes require those objects
And provide them all those objects
If there is any change in objects, then DI looks into it and it should not concern the class using those objects. This way if the objects change in the future, then its DI’s responsibility to provide the appropriate objects to the class.


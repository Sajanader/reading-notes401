# read-02


**let's start by giving example:** 
Just recaping: we have a name as input and we need to return a gender as output. So, the smaller test is: given a name, return a gender.
Input: Ana [name]
Output: female [gender]
 Are we going to write a test just to check if given Anashould return female?

```
Let’s write our first test!
def test_should_return_female_when_the_name_is_from_female_gender():
    detector = GenderDetector()
    expected_gender = detector.run(‘Ana’)
    assert expected_gender == ‘female’
 ```
 The first one is the test name. The tests can be considered as your alive documentation. We need to be descriptive about it and to say what is expected and what we are testing. In this case we explicitly said: ``should return female when the name is from a female.``
The test file name should follow the same name of module name. For instance, if our module is gender.py, our test name should be test_gender.py. It’s ideal to separate the tests folder from production code (the implementation) and to have something like this:
```
mymodule/
 — module.py
 — another_folder/
 — — another_module.py
tests/
 — test_module.py
 — another_folder/
 — — test_another_module.py
 ```
 ### The Cycle
* Write a unit test and make it fail (it needs to fail because the feature isn’t there, right? If this test passes, call the Ghostbusters, really)
* Write the feature and make the test pass! (you can dance after that)
* Refactor the code — the first version doesn’t need to be the beautiful one

*FAIL FAIL .....*
We just need to write the method that returns the right answer: FEMALE!
``def run(self, name):
    return 'female'``

* Let’s write one more test. Besides female names, we need to identify male names as well.
``
def test_should_return_male_when_the_name_is_from_male_gender():
    detector = GenderDetector()
    expected_gender = detector.run(‘Pedro’)
    assert expected_gender == ‘male’
```

But when we run it will fail because we just return female, right? Let’s fix it using our real code.
import requests

```def run(self, name):
    result = requests.get('https://api.genderize.io/?name{}'
.format(name))
    return result['gender']
```

### test is passing 
![test](https://miro.medium.com/max/875/1*gxEKnrQuS7CO3hONTD7_hg.png)


### What is Recursion? 
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function. Using recursive algorithm, certain problems can be solved quite easily. Examples of such problems are Towers of Hanoi (TOH), Inorder/Preorder/Postorder Tree Traversals, DFS of Graph, etc
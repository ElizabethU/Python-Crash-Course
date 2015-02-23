Python Crash Course
===================

###the Zen of Python
```python
import this
```

###Python 2 and 3 both exist
The most recent version of Python is 3.4, but the majority of people still use Python 2.7, because Python 3 is not backwards compatible with Python 2, and so there's a lot of labor involved in updating existing projects. Your Mac ships to with Python 2.7, it's what most people start out with, and it's what most people use in the workplace, so we'll be focus on Python 2.7 in these examples.

To get to an interactive shell of Python 2.7, simply type ```python```

###Installfest!

#####pip

First thing, we're going to need a package manager. This is the equivalent, roughly, to homebrew. ```pip``` is the package manager we'll be using for Python.
Type

```which pip``` into your commandline. If it says ```/usr/local/bin/pip``` you're good to go.

If not, type ```sudo easy_install pip```

easy_install is another package manager, which installs the package manager we actually want to use. It's like package manager inception.  Don't worry.

#####No more rvm, venv instead

Up until now RVM has been handling all your dependencies. You really haven't had to do much, RVM handles it all for you. Now that you're using Python, though, you're going to use virtual environment, or ```venv```.

Now that we have pip, we can just say ```sudo pip install venv```

Virtual environments are like little parallel universes where we can install packages and not have them bleed out into other parts of our computer. As we may work on lots of different projects that need lots of different conflicting libraries, or even different versions of the same libraries. You don't want to install libraries outside your virtual env for the same reason you don't want a million global variables in your program.

To make a virtual environment, type ```venv myvenv```. The name of the environment is ```myenv```. You could put any word there, it's not a special keyword.

Now that we've made a virtual environment, we have to actually enter it.

```source myenv/bin/activate```

Your prompt should change and now look like this

```(myenv) ```

Now you're in the environment and can proceed as normal.

###Basic Syntax example here

#####Make sure to include tuples, namedtuples

#####() on everything

In Python, just saying a method's name is not calling it, doing so will just return information about the method. Even if a method has no arguments, to call it, you have to say method() to call it.

#####return everything

Unlike Ruby, Python needs to be told return something. It doesn't just return the last thing in the function.

#####:

End control flow statements or definitions with a :

#####self

if you are writing a class in Python, you to have to pass ```self``` as the first argument to a method, but only when you are defining it, not when you are calling it:

```class Foo(object):

    def bar(self, nonsense):
        if len(nonsense) % 2 == 0:
            print "Looks like that nonsense is an even number of characters"
        else:
            print "That's an even number of letters"

foo = Foo()

foo.bar('baz')```

#####A or False

From http://docs.python.org/reference/expressions.html#boolean-operations:

In the context of Boolean operations, and also when expressions are used by control flow statements, the following values are interpreted as false: False, None, numeric zero of all types, and empty strings and containers (including strings, tuples, lists, dictionaries, sets and frozensets). All other values are interpreted as true.

###unittest

###Things that are the worst

#####super

#####Floats and Decimals
https://docs.python.org/2/tutorial/floatingpoint.html

TL;DR: Most times floats are awful and you want decimals.

#####Mixins

###Fancy Bits

#####enumerate

A fairly common thing to do is loop over a list while also keeping track of what index we are up to. Now we could use a count variable, but python gives us a nicer syntax for this with the enumerate() function.

```python
students = ('James', 'Andrew', 'Mark')
for i, student in enumerate(students):
    print i, student
```  
#####set

set is a useful little data structure, it is kind of like a list but each value in it is unique. There are some useful operations, besides creating a list of unique items, that we can do with it. For example let try some different ways of validating lists of input.

```python
colours = set(['red', 'green', 'blue', 'yellow', 'orange', 'black', 'white'])
 
# or using the newer syntax
input_values = {'red', 'black', 'pizza'}
 
# get a list off the valid colours
valid_values = input_values.intersection(colours)
 
print valid_values
# output set(['black', 'red'])
 
# get a list of the invalid colours
invalid_values = input_values.difference(colours)
 
print invalid_values
# output set(['pizza'])
 
# throw exception if there is something invalid 
if not input_values.issubset(colours):
    raise ValueError("Invalid colour: " + ", ".join(input_values.difference(colours)))
```

#####Conditional Expressions

Python allows for conditional expressions, so instead of writing an if .. else with just one variable assignment in each branch, you can do the following:

```python
# make number always be odd
number = count if count % 2 else count - 1
 
# call function if object is not None 
name = user.name() if user is not None else 'Guest'
print "Hello", name
```
#####List comprehensions

List comprehensions are supposed to replace building a list by looping and calling append. Compare the following.

```python
numbers = [1, 2, 3, 4, 5, 6, 7]
squares = []
for num in numbers:
    squares.append(num * num)
 
# with a list compression 
squares = [num * num for num in numbers]
```
We can also make this more complicated, by adding in filtering or putting a conditional assignment in:

```pythonpython
numbers = [1, 2, 3, 4, 5, 6, 7]
 
# squares of all the odd numbers
squares = [num * num for num in numbers if num % 2]
 
# times even numbers by 2 and odd numbers by 3
mul = [num * 3 if num % 2 else num * 2 for num in numbers]
```

#####Generators

Generator simplifies creation of iterators. A generator is a function that produces a sequence of results instead of a single value. A generator function is defined like a normal function, but whenever it needs to generate a value, it does so with the 'yield keyword rather than 'return'. 

```python
def simple_generator_function():
    yield 1
    yield 2
    yield 3

for value in simple_generator_function():
     print(value)
```

To get the next value from a generator, we use the same built-in function as for iterators: next()

```python
my_generator = simple_generator_function()
next(my_generator)
# 1
next(my_generator)
# 2
next(my_generator)
# 3
```
#####Dictionary Comprehensions

One use for generators can be to build a dictionary, like in the first example below. Both of these examples swap the keys and values of the dictionary.

```python
teachers = {
    'Andy': 'English',
    'Joan': 'Maths',
    'Alice': 'Computer Science',
}
# using a list comprehension
subjects = dict((subject, teacher) for teacher, subject in teachers.items())
 
# using a dictionary comprehension
subjects = {subject: teacher for teacher, subject in teachers.items()}
```

#####lambdas

###Errors and Exceptions in Python

An exception is an error that happens during execution of a program. When that error occurs Python generates an exception to prevent a program from crashing.

![](http://i.imgur.com/WRuJV6rl.png )

[Python Koans](https://github.com/gregmalcolm/python_koans)

Project Idea: http://programarcadegames.com/index.php?chapter=lab_camel&lang=en

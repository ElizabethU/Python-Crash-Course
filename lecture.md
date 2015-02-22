Python Crash Course
===================

###Python 2.7 and 3.3 both exist
The most recent version of Python is 3.4, but the majority of people still use Python 2.7, because Python 3 is not backwards compatible with Python 2, and so there's a lot of labor involved in updating existing projects. Your Mac ships to with Python 2.7, it's what most people start out with, and it's what most people use in the workplace, so we'll be focus on Python 2.7 in these examples.

###No more rvm, venv instead

###Basic Syntax example here

#####Make sure to include tuples, namedtuples

#####() on everything

#####return everything

#####A or False

###Using pdb

###unittest

###Things that are the worst

#####super

#####Floats and Decimals

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
 
# or using the newer syntax to declare the list.
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

Generators simplifies creation of iterators. A generator is a function that produces a sequence of results instead of a single value. A generator function is defined like a normal function, but whenever it needs to generate a value, it does so with the 'yield keyword rather than 'return'. 

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


if we have time? (I thought Andrew is covering decorators)
#####decorators

#####@classmethod

#####@staticmethod

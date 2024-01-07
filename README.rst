Getting started with Python
===========================

The Python interpreter
----------------------

Type ``python`` or ``python3`` in a terminal window::

    $ python3
    Python 3.7.3 (default, Jun 19 2019, 07:38:49)
    [Clang 10.0.1 (clang-1001.0.46.4)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

As long as the response starts with "Python 3...", that's OK. If you don't get it
by typing ``python`` try doing ``python3`` instead.

You're now in the Python interpreter. To exit, hit ``control d``.

In the interpreter, you type commands and press return::

    >>> 2 + 2
    4
    >>> 23 * 4.3
    98.89999999999999
    >>> hello computer
      File "<stdin>", line 1
        hello computer
                     ^
    SyntaxError: invalid syntax
    >>>


Simple maths
------------

We're using Python *operators*.

::

    >>> 6 - 7
    -1
    >>> 8 / 2
    4.0
    >>> 8 / 3
    2.6666666666666665

Some other useful operators::

    >>> # 3 to the power of 2
    >>> 3 ** 2
    9
    >>> # division, but only into whole numbers
    >>> 19 // 4 
    4
    >>> # and the remainder 
    >>> 19 % 4
    3


https://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator


Variables
---------

::

    >>> a = 3
    >>> b = 27
    >>> b / a
    9.0
    >>> c = a + b
    >>> c
    30

    # errors!
    >>> d
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'd' is not defined


Strings
-------

::

    >>> "hello" + "world"
    'helloworld'
    >>> a = "hello"
    >>> b = "world"
    >>> a + b
    'helloworld'


Comparisons, and True and False
-------------------------------

Python *comparison operators*

::

    >>> # are they equal?
    >>> 1 == 2
    False
    >>> 1 == 1
    True
    >>> a = 10
    >>> b = 10
    >>> a == b
    True
    # are they not equal?
    >>> 1 != 2
    True
    # greater and less than
    >>> 2 > 1
    True
    >>> 1 < 2
    True
    # also <= and >=


Tuples, lists and sets
----------------------

Tuples, lists and sets are all examples of Python *collections*.


Tuples
^^^^^^

::

    >>> elements = ("hydrogen", "helium", "lithium", "beryllium", "boron")
    >>> type(elements)
    <type 'tuple'>

    # slicing a tuple
    >>> elements[0]
    'hydrogen'
    >>> elements[3]
    'beryllium'
    >>> elements[1:4]
    ('helium', 'lithium', 'beryllium')
    >>> elements[-1]
    'boron'


Lists
^^^^^

::

    >>> elements = list(elements)
    >>> type(elements)
    <type 'list'>

Lists can be sliced in the same way as tuples. Unlike tuples, lists can be
maniupulated once created::

    >>> elements.sort()
    >>> elements
    ['beryllium', 'boron', 'helium', 'hydrogen', 'lithium']

``sort()`` is a *method* of the list *class*. Any list is a member of this
class - it's a list *object* - and will have all the abilities that lists can
have.

::

    # the items in collection don't even have to be of the same type
    >>> elements.append(37)
    >>> elements
    ['beryllium', 'boron', 'helium', 'hydrogen', 'lithium', 37]

    # and an item can itself be a collection
    >>> elements.append(["pancakes", "bread"])
    >>> elements
    ['beryllium', 'boron', 'helium', 'hydrogen', 'lithium', 37, ['pancakes',
    'bread']]


http://docs.python.org/3/tutorial/introduction.html#lists


Sets
^^^^

A set is an unordered collection with no duplicate elements.

::

    >>> life = ["fun", "fun", "fun", "boring", "fun"]
    >>> set(life)
    set(['fun', 'boring'])


Dictionaries
------------

::

    >>> legs = {"spider": 6, "dog": 4, "bird": 2, "ant": 6}
    >>> legs["bird"]
    2

    # we don't have humans
    >>> legs["human"]
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    KeyError: 'human'
    >>>

    # a safer way if we're not sure if the key's present
    >>> legs.get("human")
    # or even
    >>> legs.get("human", "no data available")

    # better add human though anyway
    >>> legs["human"] = 2

    # and we'd better correct the entry for spiders
    >>> legs["spider"] = 8


https://docs.python.org/3/tutorial/datastructures.html#dictionaries


Loops
-----

::

    >>> for item in range(100):
    ...     item
    ...
    0
    1
    [etc]for item in elements

    >>> for element in elements:
    ...     element
    ...
    'beryllium'
    'boron'
    'helium'
    'hydrogen'
    'lithium'
    37
    ['pancakes', 'bread']


    # list comprehensions are an excellent way to build lists
    >>> squares = [item * item for item in range(10)]
    >>> squares
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

    # you can add an if clause to filter the results
    # let's get squares of even numbers only
    >>> squares = [item * item for item in range(10) if item % 2 == 0]
    >>> squares
    [0, 4, 16, 36, 64]


Functions
---------

::

    >>> def squares():
    ...     return [item * item for item in range(10)]
    ...
    >>> squares()
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

This function only does one thing, so it's not that useful. So::

    # define squares() with a required argument
    >>> def squares(up_to):
    ...     return [item * item for item in range(up_to)]
    ...
    >>> squares()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: squares() takes exactly 1 argument (0 given)

    # we have to provide the argument
    >>> squares(15)
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196]

    # or we could have defined it with a default argument of 10
    >>> def squares(up_to=10):
    ...     return [item * item for item in range(up_to)]
    ...

We can have multiple arguments::

    >>> def multiples(up_to=10, multiply_by=2):
    ...     return [item * multiply_by for item in range(up_to)]
    ...
    >>> multiples()
    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
    >>> multiples(10, 5)
    [0, 5, 10, 15, 20, 25, 30, 35, 40, 45]

    # using named arguments when calling a function allows you to use
    # them in a different order
    >>> multiples(multiply_by=10, up_to=5)
    [0, 10, 20, 30, 40]


Let's play a game. For this we need to *import* the ``random`` *module*, and
use the ``choice()`` function.

::

    >>> import random


``choice()`` takes an argument, which needs to be a sequence of some sort, and
chooses between them at random::

    >>> random.choice(("black", "white", "red"))

    # strings are sequences too!
    >>> random.choice("Refer to the documentation for details")

::

    >>> def challenge(player_choice=None):
    ...     if player_choice is None:
    ...         print("you have to choose something!")
    ...     elif player_choice is random.choice([True, False]):
    ...         print("You win!")
    ...     else:
    ...         print("You lose!")
    ...

It's not a very interesting::

    >>> challenge()
    you have to choose something!
    >>> challenge(True)
    You win!
    >>> challenge(True)
    You lose!
    >>> challenge(True)
    You lose!

Let's make the computer play the game against itself::

    >>> for r in range(1000):
    ...     challenge(random.choice([True, False]))


Scripts
-------

Put all this in a file called game.py::

    import random

    # define the challenge function
    def challenge(player_choice=None):
        if player_choice is None:
            print("You have to choose something!")
        elif player_choice is random.choice([True, False]):
            print("You win!")
        else:
            print("You lose!")

    for r in range(1000):
        challenge(random.choice([True, False]))

Exit the Python interpreter (``control d``) and run the command::

    python3 game.py

This tells Python to run the script - the program - ``game.py``.

Classes
-------

Things in Python are instances of classes. Some are already defined, with their
own *methods* (methods are functions that belong to a class), such as lists and
dictionaries and so on, but you can also create your own.

::

    >>> class Animal(object):
    ...     def identify(self):
    ...         print("I am an animal")
    ...
    >>> dog = Animal()
    >>> dog.identify()
    I am an animal
    >>> cat = Animal()
    >>> cat.identify()
    I am an animal

We can make this a little more interesting::

    >>> class Animal(object):
    ...     def __init__(self, noise=None):
    ...         self.noise = noise
    ...     def identify(self):
    ...         print("I am an animal, and I go", self.noise)
    ...

    # create an Animal instance, and provide the string "woof" to its
    # initialiser
    >>> dog = Animal("woof")
    >>> dog.identify()
    I am an animal, and I go woof

    # we can modify an object's attribute once it has been created
    >>> dog.noise = "bow wow"
    >>> dog.identify()
    I am an animal, and I go bow wow

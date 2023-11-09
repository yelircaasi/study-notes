# Python Study Notes

## General

[Python Best Practices](https://aglowiditsolutions.com/blog/python-best-practices/)

proper naming conventions: `_protected_method()` vs `__private_method()`

use double underscore as a throwaway variable - just as readable, if not more. Also
avoids amibiguities, for example with gettext.

## Python лучшие инструменты и практики

### 1. Текущее состояние Python

3 функции PEP:

1. A) информирования
2. B) стандартизации
3. C) проектирования

Stackless Python ⟶ need to understand better

PyPy - possible to dynamically change interpretor behavior

Полезные ресурсы

* [Awesome Python](github.com/vinta/awesome-python)
* [r/Python](www.reddit.com/r/Python/)
* [Python Weekly](www.pythonweekly.com)
* [Pycoder’s Weekly](pycoders.com)

TODO: read PEP 0

### 2. Современные среды разработки на Python

* Vagrant
* Docker
* virtualenv
* ipython
* ipdb
* ptpython
* ptdb
* bpython
* bpdb

### 3

### 4

### 5

### 6

## Three Keys to Leveling up Your Python

### 1. Scalability (Here: Generator Functions)

* a generator is only as good as the code inside it: can still be hopelessly
  inefficient and unscalable
* basic idea of scalability: pay attention to what is created and what is
  required when, and program accordingly

terrible code, 'nuff said:

```python
def fetch_squares (max_root):
    squares = []
    for x in range (max_root):
        squares.append (x **2)
    return squares


MAX = 5
for square in fetch_squares(MAX):
 do_something_with (square)
```

another terrible version:

```python
def bad_gen_squares(root_limit):
    squares = []
    for root in range (root_limit):
        squares.append(root * root)
    for square in squares:
        yield squares
```

improved versions:

```python
def gen_squares (root_limit):
    root = 0
    while root < root_limit:
        yield root * root
        root += 1


def gen_squares (root_limit):
    for root in range (root_limit):
        yield root * root
```

### 2. Higher-Level Collections (Here: List and Generator Comprehensions)

* generator comprehension: just like a list comprehension, but with
  lazy evaluation

```python
# Typing all this ...
def gen_squares (root_limit):
    for root in range (root_limit):
        yield root * root


squares = gen_squares (5)

# ... is EXACTLY like typing just this:
squares = (num * num for num in range (5))
```

### 3. Pythonic Design Patterns (Here: Properties and Class Methods)

* `@property` decorator: essentially a way to make a method act like an
  attribute; provides a cleaner interface
* `cls`: actually just a variable holding the object of the current class
  (as opposed to an instance)
* class methods are really just a pythonic implementation of the
  simple factory pattern

```python
class Person:
    def __init__ (self, first, last):
        self.first = first
        self.last = last

    @property
        def full_name (self):
        return self.first + " " + self.last

    @full_name.setter
    def full_name (self, new_name):
        first, last = new_name.split ()
        self.first = first
        self.last = last
```

```python
class Money:
    def __init__ (self, dollars, cents):
        self.total_cents = 100 * dollars + cents

    @property
    def dollars (self):
        return self.total_cents // 100

    @dollars.setter
    def dollars (self, new_dollars):
        self.total_cents = 100 * new_dollars + self.cents

    @property
    def cents (self):
        return self.total_cents % 100

    @cents.setter
    def cents (self, new_cents):
        self.total_cents = 100 * self.dollars + new_cents
```

```python
class Thermometer (object):
    def __init__ (self, kelvin):
        self.kelvin = kelvin

    @property
    def fahrenheit (self):
        return 32 + (9.0/5) * (self.kelvin - 273.15)

    @fahrenheit.setter
    def fahrenheit (self, value):
        self.kelvin = 273.15 + (5.0/9) *(value - 32)

    # Just add the getter and setter for " celsius "
    @property
    def celsius (self):
        return self.kelvin - 273.15

    @celsius.setter
    def celsius (self, value):
        self.kelvin = value + 273.15
```

```python
class Money:
    def __init__ (self, dollars, cents):
    self.dollars = dollars
    self.cents = cents

    @classmethod
    def from_string (cls, amount):
        import re
        match = re. search (r'^\$(?P< dollars >\d+) \.(?P<cents >\d\d)$', amount)
        if match is None:
            raise ValueError ('Invalid amount: {} '. format (amount))
        dollars = int(match.group ('dollars '))
        cents = int(match.group ('cents '))
        return cls(dollars, cents)
```

## The Well-Grounded Python Developer

### 1. Becoming a Pythonista

look at flake8 ⟶

re-read PEP8 ⟶

GUI programs: event-driven (learn more about for gtt)

resources:

* <https://realpython.com> – Real Python is an excellent source of tutorials
  about Python
* <https://pythonbytes.fm> – a Python podcast delivering interesting
  headlines and banter
* <https://talkpython.fm> – The Talk Python To Me podcast has
  interviews with people and
  personalities in the community.
* <https://pythonpodcast.com> – `Podcast.__init__` is another good
  interview podcast
* <https://testandcode.com> – Test and Code, a podcast about software
  testing and Python
* <https://www.pythonweekly.com> – the sign-up page for a weekly
  Python newsletter
  containing links to useful articles and information
* <https://pycoders.com> – The sign-up page for another great
  Python newsletter

"Shipping is a feature that can't be overstated."

### 2. Your Development Environment

VSCode extensions to look at:

* PYTHON DOCSTRING GENERATOR
* CODE RUNNER
* DOTENV
* BETTER JINJA
* AREPL FOR PYTHON

## Advanced Python Programming

.

## Effective Python

.

## Clean Code in Python

.

## Как устроен Python. Гид для разработчиков, программистов и интересующихся

.

## Advanced Guide to Python 3 Programming

.

## Fluent Python

.

## Секреты Python Pro

### 1. Крупный план

Python имеет такой же вес в сложных корпоративных проектах,
как и другие основные языки программирования.

Python имеет одну из самых быстрорастущих пользовательских
баз из всех языков программирования.

Дизайн — это не только внешний вид, а процесс, которому вы следуете,
чтобы добраться до цели.

Дизайн — это инвестиция, которая потом вознаградит вас чистым
и гибким кодом.

Необходимо создавать ПО с учетом разнообразной аудитории.

## Путь Python

[English: Serious Python](https://www.knowledgeisle.com/wp-content/uploads/2019/10/Serious-Python_-2019.pdf)

## Inside the Python Virtual Machine

.

## Чистый Python

.

## Learn Python 3 the Hard Way

.

## Learn More Python 3 the Hard Way

.

- [Built-In Data Types](#built-in-data-types)
  - [Mutable objects](#mutable-objects)
  - [Immutable objects](#immutable-objects)
  - [Mutable vs. Immutable in Python](#mutable-vs-immutable-in-python)
  - [Numbers](#numbers)
    - [Integers](#integers)
    - [Booleans](#booleans)
    - [Float](#float)
    - [Complex numbers](#complex-numbers)
    - [Fractions and decimals](#fractions-and-decimals)
  - [Immutable sequences](#immutable-sequences)
    - [String](#string)
    - [Tuple](#tuple)
  - [Mutable sequences](#mutable-sequences)
- [OOP](#oop)
  - [The `class attributes`](#the-class-attributes)
  - [Attribute shadowing](#attribute-shadowing)
  - [The `self` argument](#the-self-argument)
  - [Initializing an instance](#initializing-an-instance)
  - [`Is-A` relation](#is-a-relation)
  - [The class composition method `Has-A`](#the-class-composition-method-has-a)
  - [Accessing a base class (parent class)](#accessing-a-base-class-parent-class)
  - [Multiple inheritance](#multiple-inheritance)
  - [Method resolution order](#method-resolution-order)
  - [The `@staticmethod` method](#the-staticmethod-method)
  - [The `@classmethod` method](#the-classmethod-method)
  - [Private methods and attributes](#private-methods-and-attributes)
  - [The property decorator](#the-property-decorator)
  - [Name mangling](#name-mangling)
  - [The `__str__` method](#the-__str__-method)
  - [The `__repr__` method](#the-__repr__-method)
  - [The `__eq__()` method](#the-__eq__-method)
  - [The `__lt__()`, `__gt__()` method](#the-__lt__-__gt__-method)
  - [Python Operator Overloading – Magic Methods](#python-operator-overloading--magic-methods)
  - [Don't use mutable defaults parameters](#dont-use-mutable-defaults-parameters)
- [Function](#function)
  - [Argument vs Parameter](#argument-vs-parameter)
  - [Keyword-only arguments](#keyword-only-arguments)
  - [First-class functions](#first-class-functions)
  - [Lambda functions](#lambda-functions)
  - [Destructuring](#destructuring)
  - [Iterable unpacking](#iterable-unpacking)
  - [Dictionary unpacking](#dictionary-unpacking)
  - [A global variable](#a-global-variable)
  - [Arbitrary Positional Arguments](#arbitrary-positional-arguments)
  - [Mixing Positional and Arbitrary Arguments](#mixing-positional-and-arbitrary-arguments)
  - [Arbitrary Keyword Arguments](#arbitrary-keyword-arguments)
  - [Type hint](#type-hint)
- [Decorators](#decorators)
  - [Define function Decorators with `functools.wraps`](#define-function-decorators-with-functoolswraps)
  - [Decorators function with parameter](#decorators-function-with-parameter)
  - [Decorators with parameter - A decorator factory](#decorators-with-parameter---a-decorator-factory)
- [Generator](#generator)
  - [Why Do We Need Generators?](#why-do-we-need-generators)
  - [Iterable vs Iterator](#iterable-vs-iterator)
  - [Yield vs Return](#yield-vs-return)
  - [`next()` function](#next-function)
  - [Generator functions](#generator-functions)
  - [`return` in generator function](#return-in-generator-function)
  - [`send()` in generator function](#send-in-generator-function)
  - [The `yield from` expression](#the-yield-from-expression)
  - [Generator expressions](#generator-expressions)
- [Package and module](#package-and-module)
  - [What is module](#what-is-module)
  - [`__name__` variable](#__name__-variable)
  - [Imports](#imports)
  - [Absolute Imports](#absolute-imports)
  - [Relative Imports](#relative-imports)
  - [Example Relative imports](#example-relative-imports)
  - [`__init__` file](#__init__-file)
  - [Set Up Virtual Environment and Install Dependencies](#set-up-virtual-environment-and-install-dependencies)
- [Other](#other)
  - [Multi-Line Statements](#multi-line-statements)
    - [Implicit](#implicit)
    - [Explicit](#explicit)
  - [Variable names](#variable-names)
    - [Must](#must)
    - [Conventions](#conventions)
    - [Other Naming Conventions](#other-naming-conventions)
  - [Debug in CLI command - without IDE editor](#debug-in-cli-command---without-ide-editor)
    - [Method 1: Start the debugger from the command line on the first line of the file.](#method-1-start-the-debugger-from-the-command-line-on-the-first-line-of-the-file)
    - [Method 2: Start the debugger from the command line and debug at the line where the breakpoint is set.](#method-2-start-the-debugger-from-the-command-line-and-debug-at-the-line-where-the-breakpoint-is-set)
    - [pdb Commands](#pdb-commands)
  - [Format datetime to string](#format-datetime-to-string)
  - [index of the day of the week from a date in Python](#index-of-the-day-of-the-week-from-a-date-in-python)
  - [Add days to a date in Python](#add-days-to-a-date-in-python)
  - [Errors](#errors)
  - [Custom error classes](#custom-error-classes)
  - [Raise an exception](#raise-an-exception)
  - [Using raise with a custom exception.](#using-raise-with-a-custom-exception)
  - [Re-raising an exception](#re-raising-an-exception)
  - [Python Docstrings - `__doc__` or `help()`](#python-docstrings---__doc__-or-help)
  - [API - Application programing interface](#api---application-programing-interface)
  - [HTTP Request](#http-request)
    - [What is an HTTP Request?](#what-is-an-http-request)
    - [Client–Server Model](#clientserver-model)
    - [Structure of an HTTP Request](#structure-of-an-http-request)
    - [Example](#example)
    - [Request Line](#request-line)
    - [HTTP Methods](#http-methods)
    - [HTTP Headers](#http-headers)
    - [Request Body](#request-body)
    - [Query Parameters](#query-parameters)
    - [HTTP Request vs HTTP Response](#http-request-vs-http-response)
  - [Responses HTTP codes](#responses-http-codes)
    - [1xx — Informational](#1xx--informational)
    - [2xx — Success](#2xx--success)
    - [3xx — Redirection](#3xx--redirection)
    - [4xx — Client Errors](#4xx--client-errors)
    - [5xx — Server Errors](#5xx--server-errors)
  - [Universally Unique Identifier (UUID)](#universally-unique-identifier-uuid)
    - [What is a UUID?](#what-is-a-uuid)
    - [Why is it called “Universally Unique”?](#why-is-it-called-universally-unique)
    - [UUIDs ideal for](#uuids-ideal-for)
    - [Common UUID Versions](#common-uuid-versions)
    - [How to use](#how-to-use)
  - [SQLAlchemy Database URL with Special Characters](#sqlalchemy-database-url-with-special-characters)
    - [Connection URL Format](#connection-url-format)
    - [Common Issue with Special Characters](#common-issue-with-special-characters)
    - [Solution: URL Encode Special Characters](#solution-url-encode-special-characters)
    - [Encode Password Programmatically in Python](#encode-password-programmatically-in-python)
- [Python Built-in Functions](#python-built-in-functions)
  - [Basic I/O \& Introspection](#basic-io--introspection)
  - [Sequence \& Iterable Operations](#sequence--iterable-operations)
  - [Functional Programming Tools](#functional-programming-tools)
  - [Type Conversion](#type-conversion)
  - [Numeric Helpers](#numeric-helpers)
  - [File \& Execution](#file--execution)
  - [OOP Helpers](#oop-helpers)
  - [What does in-place mean?](#what-does-in-place-mean)
  - [List Built-in Functions \& Methods](#list-built-in-functions--methods)
  - [Dictionary Built-in Functions \& Methods](#dictionary-built-in-functions--methods)
  - [Merge dictionaries (Python ≥ 3.9)](#merge-dictionaries-python--39)
- [Python Libraries](#python-libraries)
  - [Flask](#flask)
  - [Flask_smorest](#flask_smorest)
  - [python-dotenv](#python-dotenv)
  - [Marshmallow](#marshmallow)
  - [SQLAlchemy](#sqlalchemy)
  - [psycopg2](#psycopg2)
  - [PyJWT](#pyjwt)
  - [flask-jwt-extended](#flask-jwt-extended)
  - [passlib](#passlib)
  - [flask-migrate](#flask-migrate)
  - [Alembic](#alembic)
  - [Selenium](#selenium)
  - [BeautifulSoup](#beautifulsoup)
  - [Mailgun](#mailgun)

# Built-In Data Types

## Mutable objects

- Mutable objects can have their internal state or value changed without creating a new object in memory.

```
a = []
b = a

print(id(a))
print(id(b))

# print(id(a)) and print(id(b)) functions print same results

a.append(35)

print(a)
print(b)

# print(a) and print(b) functions print same results
```

- Mutable objects include `liit`, `dict`, `set`, `bytearray`, custom classes (User-defined classes are generally mutable by default)
- When two variables refer to the same mutable object, modifying the object through one variable will affect the value accessed by the other.

## Immutable objects

- Immutable objects cannot be changed once they are defined. Any operation that seems to modify an immutable object actually results in a new object being created

- Immutable objects include `int`, `float`, `bool`, `string`, `Unicode`, and `tuple` (Similar to lists but once created, their elements cannot be changed. However, a tuple is considered immutable even if it contains mutable objects, as the collection of objects it holds cannot be changed)

## Mutable vs. Immutable in Python

| Aspect                       | Mutable                                            | Immutable                                            |
| ---------------------------- | -------------------------------------------------- | ---------------------------------------------------- |
| **Definition**               | Objects whose value can be changed after creation  | Objects whose value cannot be changed after creation |
| **Behavior on Modification** | Changes affect the same object in memory           | Any “change” creates a new object                    |
| **Memory Address**           | Remains the same after modification                | Changes after modification (new object created)      |
| **Examples**                 | `list`, `dict`, `set`, `bytearray`                 | `int`, `float`, `str`, `tuple`, `frozenset`, `bytes` |
| **Hashability**              | Usually not hashable (cannot be used as dict keys) | Usually hashable (can be dict keys)                  |
| **Suitable For**             | Data structures that need updating                 | Fixed data, dictionary keys, safe sharing            |
| **Thread Safety**            | Less safe (values can be changed unexpectedly)     | More safe (values cannot be changed)                 |
| **Passing to Functions**     | Function can modify in-place                       | Function cannot modify original object               |
| **Common Use Cases**         | Lists of items, mutable configurations             | Strings, numeric constants, dictionary keys          |

## Numbers

### Integers

- Python integers have an unlimited range, subject only to the available virtual memory. This means that it doesn't really matter how big a number you want to store is—as long as it can fit in your computer's memory
- Integer numbers can be positive, negative, or 0 (zero)

### Booleans

- Booleans represent one of two values: `True` or `False`.

### Float

- Float, or "floating point number" is a number, positive or negative, containing one or more decimals.
- Issue -> Python gives you the Decimal type, which doesn't suffer from these issues

```
0.3 - 0.1 * 3 # this should be 0!!!
-5.551115123125783e-17
```

### Complex numbers

- Complex numbers are numbers that can be expressed in the form `a + ib` where `a` and `b` are real numbers, and `i` (or j if you're an engineer) is the imaginary unit
- It is perhaps unlikely that you will use them, unless you're coding something scientifi

### Fractions and decimals

- Fractions hold a rational numerator and denominator in their lowest form

```
from fractions import Fraction

a = Fraction(1, 2)
b = Fraction(3, 4)

print(a + b)   # 5/4
print(a * b)   # 3/8
print(a / b)   # 2/3
```

```
from fractions import Fraction

Fraction(2, 3)          # 2/3
Fraction("7/9")         # 7/9
Fraction(0.75)          # 3/4
```

```
from fractions import Fraction

scores = [Fraction(85, 1), Fraction(90, 1), Fraction(88, 1)]
avg = sum(scores) / len(scores)

print(avg)        # 263/3
print(float(avg)) # 87.66666666666667
```

- Although Fraction objects can be very useful at times, it's not that common to spotthem in commercial software. Instead, it is much more common to see decimal numbers being used in all those contexts where precision is everything

```
from decimal import Decimal as D # rename for brevity
D(3.14) # pi, from float, so approximation issues
# Decimal('3.140000000000000124344978758017532527446746826171875')
D('3.14') # pi, from a string, so no approximation issues
# Decimal('3.14')
D(0.1) * D(3) - D(0.3) # from float, we still have the issue
# Decimal('2.775557561565156540423631668E-17')
D('0.1') * D(3) - D('0.3') # from string, all perfect
# Decimal('0.0')
D('1.4').as_integer_ratio() # 7/5 = 1.4 (isn't this cool?!)
# (7, 5)
```

## Immutable sequences

### String

- Assign String to a Variable

```
a = "Hello"
print(a)
```

- Assign a multiline string to a variable

```
a = """Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua."""
print(a)
```

```
a = '''Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua.'''
print(a)
```

- Strings are Arrays

```
a = "Hello, World!"
print(a[1])
```

- Looping Through a String

```
for x in "banana":
  print(x)
```

- String Length

```
a = "Hello, World!"
print(len(a))
```

- Check String

```
txt = "The best things in life are free!"
print("free" in txt)
```

- Slicing Strings

```
b = "Hello, World!"
print(b[2:5])
```

- Slice From the Start

```
b = "Hello, World!"
print(b[:5])
```

- Slice To the End

```
b = "Hello, World!"
print(b[2:])
```

- Modify string

| Category  | Method           | Description                     | Example                                   |
| --------- | ---------------- | ------------------------------- | ----------------------------------------- |
| Case      | `upper()`        | Convert to uppercase            | `"abc".upper()` → `"ABC"`                 |
| Case      | `lower()`        | Convert to lowercase            | `"ABC".lower()` → `"abc"`                 |
| Case      | `capitalize()`   | Capitalize first character      | `"hello".capitalize()` → `"Hello"`        |
| Case      | `title()`        | Capitalize each word            | `"hello world".title()` → `"Hello World"` |
| Case      | `swapcase()`     | Swap upper/lower case           | `"AbC".swapcase()` → `"aBc"`              |
| Trim      | `strip()`        | Remove leading & trailing chars | `" hi ".strip()` → `"hi"`                 |
| Trim      | `lstrip()`       | Remove leading chars            | `" hi".lstrip()` → `"hi"`                 |
| Trim      | `rstrip()`       | Remove trailing chars           | `"hi ".rstrip()` → `"hi"`                 |
| Replace   | `replace()`      | Replace substring               | `"a-b".replace("-", "_")` → `"a_b"`       |
| Split     | `split()`        | Split string into list          | `"a,b".split(",")` → `["a","b"]`          |
| Join      | `join()`         | Join iterable into string       | `",".join(["a","b"])` → `"a,b"`           |
| Align     | `center()`       | Center with padding             | `"42".center(5,"*")` → `"*42**"`          |
| Align     | `ljust()`        | Left-align with padding         | `"42".ljust(5,"0")` → `"42000"`           |
| Align     | `rjust()`        | Right-align with padding        | `"42".rjust(5,"0")` → `"00042"`           |
| Align     | `zfill()`        | Pad with zeros                  | `"42".zfill(5)` → `"00042"`               |
| Prefix    | `removeprefix()` | Remove prefix (Py 3.9+)         | `"unhappy".removeprefix("un")`            |
| Suffix    | `removesuffix()` | Remove suffix (Py 3.9+)         | `"file.txt".removesuffix(".txt")`         |
| Encode    | `encode()`       | String → bytes                  | `"hi".encode("utf-8")`                    |
| Decode    | `decode()`       | Bytes → string                  | `b"hi".decode("utf-8")`                   |
| Translate | `translate()`    | Replace multiple chars          | `"abc".translate(table)`                  |

- String Concatenation: To concatenate, or combine, two strings you can use the `+` operator.

```
a = "Hello"
b = "World"
c = a + " " + b
print(c)
```

- Format - Strings

| Method             | Syntax                    | Description               | Example                      | Output       |
| ------------------ | ------------------------- | ------------------------- | ---------------------------- | ------------ |
| f-string           | `f"{var}"`                | Modern, fastest, readable | `name="An"; f"Hi {name}"`    | `Hi An`      |
| f-string (expr)    | `f"{a+b}"`                | Inline expressions        | `f"{2+3}"`                   | `5`          |
| f-string (format)  | `f"{n:.2f}"`              | Format numbers            | `f"{3.14159:.2f}"`           | `3.14`       |
| f-string (padding) | `f"{n:05}"`               | Zero padding              | `f"{42:05}"`                 | `00042`      |
| f-string (align)   | `f"{s:^10}"`              | Center text               | `f"{'hi':^10}"`              | `hi `        |
| `format()`         | `"{}".format(x)`          | Classic formatter         | `"Hello {}".format("Bob")`   | `Hello Bob`  |
| `format()`         | `"{0} {1}".format(a,b)`   | Positional args           | `"{0}-{1}".format(1,2)`      | `1-2`        |
| `format()`         | `"{name}".format(name=x)` | Named args                | `"{name}".format(name="An")` | `An`         |
| `%` operator       | `"%s" % x`                | Old-style formatting      | `"%d apples" % 5`            | `5 apples`   |
| `%` float          | `"%.2f" % x`              | Float formatting          | `"%.2f" % 3.1415`            | `3.14`       |
| Format spec        | `{:,.2f}`                 | Thousand separator        | `"{:,.2f}".format(12345.6)`  | `12,345.60`  |
| Date format        | `{:%Y-%m-%d}`             | Datetime formatting       | `f"{dt:%Y-%m-%d}"`           | `2026-01-17` |
| Debug (3.8+)       | `f"{var=}"`               | Show name & value         | `x=10; f"{x=}"`              | `x=10`       |

- Escape Characters: An escape character is a backslash `\` followed by the character you want to insert.

```
txt = "We are the so-called \"Vikings\" from the north."
```

| Escape Character | Name             | Description                | Example                       | Output         |
| ---------------- | ---------------- | -------------------------- | ----------------------------- | -------------- |
| `\n`             | New line         | Moves cursor to next line  | `"Hello\nWorld"`              | Hello<br>World |
| `\t`             | Tab              | Inserts horizontal tab     | `"A\tB"`                      | A B            |
| `\\`             | Backslash        | Inserts `\`                | `"C:\\path"`                  | C:\path        |
| `\'`             | Single quote     | Inserts `'`                | `'It\'s ok'`                  | It's ok        |
| `\"`             | Double quote     | Inserts `"`                | `"She said \"Hi\""`           | She said "Hi"  |
| `\r`             | Carriage return  | Moves cursor to line start | `"Hello\rHi"`                 | Hi             |
| `\b`             | Backspace        | Removes previous char      | `"AB\bC"`                     | AC             |
| `\f`             | Form feed        | Page break (rare)          | `"A\fB"`                      | A B            |
| `\v`             | Vertical tab     | Vertical spacing           | `"A\vB"`                      | A B            |
| `\0`             | Null             | Null character             | `"A\0B"`                      | A B            |
| `\a`             | Bell             | System alert sound         | `"\a"`                        | 🔔             |
| `\xhh`           | Hex value        | Char from hex              | `"\x41"`                      | A              |
| `\ooo`           | Octal value      | Char from octal            | `"\101"`                      | A              |
| `\N{name}`       | Unicode name     | Unicode character          | `"\N{GREEK SMALL LETTER PI}"` | π              |
| `\uXXXX`         | Unicode (16-bit) | Unicode char               | `"\u03C0"`                    | π              |
| `\UXXXXXXXX`     | Unicode (32-bit) | Unicode char               | `"\U0001F600"`                | 😀             |

- Encoding and decoding strings

```
s = "This is üŋíc0de" # unicode string: code points
type(s)
# <class 'str'>
encoded_s = s.encode('utf-8') # utf-8 encoded version of s
encoded_s
# b'This is \xc3\xbc\xc5\x8b\xc3\xadc0de' # result: bytes object
type(encoded_s) # another way to verify it
# <class 'bytes'>
encoded_s.decode('utf-8') # let's revert to the original
# 'This is üŋíc0de'
```

- Sequence repetition operator: Applies to `str`,`list`,`tuple`,`bytes`

```
(1, 2) * 3
# (1, 2, 1, 2, 1, 2)

'abc' * 3
# 'abcabcabc'
```

### Tuple

- Tuples are used to store multiple items in a single variable.
- A tuples are unchangeable, meaning that we cannot change, add or remove items after the tuple has been created.
- Tuple items are indexed, the first item has index `[0]`, the second item has index `[1]` etc.
- Allow Duplicates: Since tuples are indexed, they can have items with the same value
- Declare

```
thistuple = ("apple", "banana", "cherry", "apple", "cherry")
a, b, c = 1, 2, 3
```

- Access

```
thistuple = ("apple", "banana", "cherry")
print(thistuple[1])
```

```
thistuple = ("apple", "banana", "cherry")
print(thistuple[-1])
```

```
thistuple = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(thistuple[2:5])
```

- Change Tuple Values: You can convert the tuple into a list, change the list, and convert the list back into a tuple.

```
x = ("apple", "banana", "cherry")
y = list(x)
y[1] = "kiwi"
x = tuple(y)

print(x)
```

- Unpacking a Tuple

```
fruits = ("apple", "banana", "cherry")

(green, yellow, red) = fruits

print(green)
print(yellow)
print(red)
```

- Loop Through a Tuple

```
thistuple = ("apple", "banana", "cherry")
for x in thistuple:
  print(x)
```

```
thistuple = ("apple", "banana", "cherry")
for i in range(len(thistuple)):
  print(thistuple[i])
```

- Join Tuples: To join two or more tuples you can use the `+` operator:

```
tuple1 = ("a", "b" , "c")
tuple2 = (1, 2, 3)

tuple3 = tuple1 + tuple2
print(tuple3)
```

## Mutable sequences

# OOP

## The `class attributes`

- `class attributes` are variables that belong to the class itself, rather than to any specific instance (object) of that class. They are shared among all instances of the class.
- **Shared across instances**: All objects created from the same class will share the same class attribute and its value.
- **Defined within the class, outside methods:** Class attributes are typically defined directly within the class body, but outside of any methods like **init**().
- **Accessed via class or instance**: You can access a class attribute using either the class name (e.g., ClassName.attribute_name) or an instance of the class (e.g., object_name.attribute_name).
- **Useful for shared data**: They are suitable for storing data that is common to all instances, such as constants, default values, or counters that track class-level information.

```

class Car:
# This is a class attribute
number_of_wheels = 4

    def __init__(self, make, model):
        self.make = make  # This is an instance attribute
        self.model = model # This is an instance attribute

# Create instances of the Car class

car1 = Car("Toyota", "Camry")
car2 = Car("Honda", "Civic")

# Accessing the class attribute

print(f"Car 1 has {car1.number_of_wheels} wheels.")
print(f"Car 2 has {car2.number_of_wheels} wheels.")
print(f"The Car class has {Car.number_of_wheels} wheels defined.")

# Modifying the class attribute through the class

Car.number_of_wheels = 6
print(f"After modification, Car 1 now has {car1.number_of_wheels} wheels.")
print(f"After modification, Car 2 now has {car2.number_of_wheels} wheels.")

```

## Attribute shadowing

- When you search for an attribute on an object, if it is not found, Python extends the search to the attributes on the class that was used to create that object (and keeps searching until it's either found or the end of the inheritance chain is reached)

```
# oop/class.attribute.shadowing.py
class Point:
  x = 10
  y = 7

p = Point()

print(p.x) # 10 (from class attribute)
print(p.y) # 7 (from class attribute)

p.x = 12 # p gets its own `x` attribute

print(p.x) # 12 (now found on the instance)
print(Point.x) # 10 (class attribute still the same)

del p.x # we delete instance attribute
print(p.x) # 10 (now search has to go again to find class attr)

p.z = 3 # let's make it a 3D point

print(p.z) # 3
print(Point.z)
# AttributeError: type object 'Point' has no attribute 'z'
```

## The `self` argument

- From within a class method, we can refer to an instance by means of a special argument, called `self` by convention
- `self` is always the first attribute of an instance method

```
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(the_referenced_object):
        return 2 * (the_referenced_object.width + the_referenced_object.height)

r1 = Rectangle(10, 20)

r1.perimeter()

# 60
# This is why we can use a name other than self, such as in the perimeter method
```

## Initializing an instance

```
class Rectangle:
  def __init__(self, side_a, side_b):
    self.side_a = side_a
    self.side_b = side_b

  def area(self):
    return self.side_a * self.side_b

r1 = Rectangle(10, 4)
```

## `Is-A` relation

- It signifies a hierarchical relationship where a subclass (or derived class) is a specialized version of its superclass (or base class).
- Key characteristics of the `Is-A` relation
  - **Inheritance**: The "Is-A" relationship is established when one class inherits from another. The subclass automatically gains access to the attributes and methods defined in its superclass.
  - **Specialization**: The subclass represents a more specific type of the superclass. For example, a Dog `Is-A` Animal, and a Car `Is-A` Vehicle.
  - **Code Reusability**: Inheritance promotes code reusability by allowing subclasses to inherit and potentially override or extend the functionality of their superclasses, rather than duplicating code.
  - **Polymorphism**: The `Is-A` relationship enables polymorphism, where objects of different classes can be treated as objects of a common superclass, allowing for more flexible and extensible code.

```

# Superclass (Base class)

class Animal:
  def speak(self):
    return "Animal speaks"

# Subclass (Derived class) - Dog IS-A Animal

class Dog(Animal):
  def speak(self):
    return "Woof!"

# Subclass (Derived class) - Cat IS-A Animal

class Cat(Animal):
  def speak(self):
    return "Meow!"

# Usage

my_dog = Dog()
my_cat = Cat()

print(my_dog.speak()) # Output: Woof!
print(my_cat.speak()) # Output: Meow!

```

## The class composition method `Has-A`

- An object-oriented programming concept where a class includes an object of another class as an attribute
- This creates a **has-a** relationship, meaning the composite class has or owns a component object.
- Key Concepts
  - `Has-A` Relationship: This principle is central to composition. For example, a Car class "has an" Engine objec
  - **Strong Dependency**: In a strict composition relationship, the component object cannot exist independently of the composite object. If the Car object is destroyed, the Engine object it owns is also conceptually (or programmatically) destroyed.
  - **Code Reuse and Modularity**: Composition promotes flexibility and code reuse without creating a rigid class hierarchy that comes with inheritance. It allows you to change the behavior of a class by simply replacing one of its component objects.
  - **Single Responsibility Principle**: Composition helps in creating smaller, more focused classes, adhering to the principle that a class should have one specific responsibility

```

class Engine:
  def __init__(self, horse_power):
    self.horse_power = horse_power

  def start(self):
    return "Engine started."

class Car:
  def __init__(self, make, model, horse_power):
    self.make = make
    self.model = model # Composition: A Car has an Engine object as an attribute
    self.engine = Engine(horse_power)

  def display_car_info(self):
    engine_status = self.engine.start() # Accessing a method of the composed object
    return f"{self.make} {self.model} with {self.engine.horse_power}hp. {engine_status}"

# Create a Car instance

my_car = Car(make="Ford", model="Mustang", horse_power=500)
print(my_car.display_car_info())

```

- In this example
  - The Car class is the composite class.
  - The Engine class is the component class.
  - The Car class creates and manages an Engine instance within its own `__init__` method, demonstrating the strong ownership inherent in composition.

## Accessing a base class (parent class)

- When we don't specify a base class explicitly, Python will set the special `object` class as the base class for the one we're defining
- `super()` is a function that returns a proxy object that delegates method calls to a parent or sibling class

```
class Book:
  def __init__(self, title, publisher, pages):
    self.title = title
    self.publisher = publisher
    self.pages = pages


class Ebook(Book):
  def __init__(self, title, publisher, pages, format_):
    super().__init__(title, publisher, pages)
    # Another way to do the same thing is:
    # super(Ebook, self).__init__(title, publisher, pages)
    self.format_ = format_

ebook = Ebook(
 'Learn Python Programming', 'Packt Publishing', 500, 'PDF')

print(ebook.title) # Learn Python Programming
print(ebook.publisher) # Packt Publishing
print(ebook.pages) # 500
print(ebook.format_) # PDF
```

## Multiple inheritance

- Old way, it's not recommended

```
class Base1:
    def __init__(self, x):
        self.x = x


class Base2:
    def __init__(self, y):
        self.y = y


class Derived(Base1, Base2):
  def __init__(self, x, y, z):
    # Call second base class constructor explicitly
    # or Base1.__init__(self, x)
    super().__init__(x)  # Call first base class constructor
    # Call second base class constructor explicitly
    Base2.__init__(self, y)
    self.z = z


derived = Derived(1, 2, 3)

print("Derived:", derived.x, derived.y, derived.z)
```

- New way, the large framework use **Cooperative Multiple Inheritance**

```
class A:
    def __init__(self, a, **kwargs):
        self.a = a
        super().__init__(**kwargs)

class B:
    def __init__(self, b, **kwargs):
        self.b = b
        super().__init__(**kwargs)

class C(A, B):
    def __init__(self, a, b):
        super().__init__(a=a, b=b)

c = C(a=10, b=20)
```

## Method resolution order

- Python provides a way to always know the order in which classes are searched on attribute lookup: **the method resolution order (MRO)**.

```
class A:
  label = 'a'

class B(A):
  pass # was: label = 'b'

class C(A):
  label = 'c'

class D(B, C):
  pass

d = D()
print(d.label) # 'c'
print(d.__class__.mro()) # notice another way to get the MRO
# prints:
# [<class '__main__.D'>, <class '__main__.B'>,
# <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
```

## The `@staticmethod` method

- The `@staticmethod` decorator in Python transforms a regular function within a class into a static method. Static methods are distinct from instance methods and class methods in their relationship to the class and its instances.
- No `self` or `cls` argument
- Independent of instance and class state: Because static methods don't have access to `self` or `cls`, they cannot directly access or modify instance attributes or class attributes.
- Called on the class or instance: `ClassName.static_method()`
- Utility functions: They are often used for utility functions that logically belong to a class but do not require any instance-specific data or class-level state. Examples include helper functions, validation routines, or formatting methods.
- Code organization: Using @staticmethod helps in organizing code by grouping related functions within a class, even if those functions don't interact with the class's internal state.

```

class Calculator:

  @staticmethod
  def add(x, y):
    return x + y

  @staticmethod
  def multiply(x, y):
    return x * y

# Calling static methods

result_add = Calculator.add(5, 3)
print(f"Addition: {result_add}")

calc_instance = Calculator()
result_multiply = calc_instance.multiply(4, 2)
print(f"Multiplication: {result_multiply}")

```

## The `@classmethod` method

- The `@classmethod` decorator in Python defines a method that belongs to the class itself, rather than to an instance of the class.
- **Accessing Class Attributes**: Class methods can access and modify class-level attributes, which are shared across all instances of the class. This allows them to manage and interact with the state of the class itself.
- **Calling Conventions**: Class methods can be called on the class directly (e.g., `MyClass.my_class_method()`) or on an instance of the class (e.g., `my_instance.my_class_method()`). When called on an instance, the instance's class is automatically passed as the `cls` argument.
- **Alternative Constructors (Factory Methods)**: A common and powerful use of class methods is to create alternative constructors. These methods provide different ways to instantiate objects of the class, often by processing different input formats or applying specific logic before creating an instance. For example, a Person class might have a `@classmethod` called `from_birth_year` to create a Person object from a birth year.
- **Modifying Class State**: Class methods are suitable for operations that need to modify or interact with the class's state, such as updating class variables or performing actions that affect all instances.

```

class Vehicle:
  TYPES = ("car", "bike", "truck")

    def __init__(self, v_type, name):
        self.v_type = v_type
        self.name = name

    @classmethod
    def car(cls, name):
        return cls("car", name)

    @classmethod
    def bike(cls, name):
        return cls("bike", name)

    @classmethod
    def truck(cls, name):
        return cls("truck", name)

# ----------------------------

v1 = Vehicle.car("Toyota")
v2 = Vehicle.bike("Honda")
v3 = Vehicle.truck("Volvo")

print(v1.v_type, v1.name) # car Toyota
print(v2.v_type, v2.name) # bike Honda
print(v3.v_type, v3.name) # truck Volvo

```

## Private methods and attributes

- In Python, there is no such thing. Everything is public; therefore, we rely on conventions and, for privacy, on a mechanism called **name mangling**
- The convention is as follows
  - if an attribute's name has **no leading underscores**, it is considered public. This means you can access it and modify it freely
  - When the name has **one leading underscore**, the attribute is considered private, which means it's probably meant to be used internally and you should not modify it, or call it from the outside

## The property decorator

- **Reason**:
  - Imagine that you have an age attribute in a Person class and, at some point, you want to make sure that when you change its value, you're also checking that age is within a proper range, such as [18, 99]. You could write accessor methods, such as `get_age()` and `set_age(...)` (also called getters and setters), and put the logic there. `get_age()` will most likely just return age, while `set_age(...)` will set its value after checking its validity. The problem is that you may already have a lot of code accessing the age attribute directly, which means you're now up to some tedious refactoring. Python does this with the **property decorator**

- In Python we can use some special **decorators** to encapsulate our property getters and setters
- There are more things we should do to properly implement all this, in particular we should also be checking the positive and negative values during the `__init__` phase. We do so by using the accessor methods for height and width

```
class Rectangle:
    def __init__(self, width, height):
        self._width = None
        self._height = None
        # now we call our accessor methods to set the width and height
        self.width = width
        self.height = height

    def __repr__(self):
        return 'Rectangle({0}, {1})'.format(self.width, self.height)

    @property
    def width(self):
        return self._width

    @width.setter
    def width(self, width):
        if width <= 0:
            raise ValueError('Width must be positive.')
        self._width = width

    @property
    def height(self):
        return self._height

    @height.setter
    def height(self, height):
        if height <= 0:
            raise ValueError('Height must be positive.')
        self._height = height

r1 = Rectangle(10, 20)
r1.width # 10
r1.width = 100
r1 # Rectangle(100, 20)
r1.width = -10 # ValueError: Width must be positive.

r2 = Rectangle(0, 10) # ValueError: Width must be positive.
```

## Name mangling

- **Name mangling** means that any attribute name that has at least two leading underscores, such as `__my_attr`

- How It Works
  - When the Python interpreter encounters a mangled name inside a class definition, it textually replaces it with a new name in the format, such as `_ClassName__my_attr`
  - **Example Transformation**: If a class named Robot has an attribute `__name`, it is internally renamed to `_Robot__name`.
  - **Encapsulation**: This makes it harder for subclasses to accidentally override parent attributes or for external code to access them directly, though it is not a strict "private" access modifier like in C++ or Java
- Every class and instance object stores references to their attributes in a special attribute called `__dict__`, so let's inspect `obj.__dict__` to see name mangling in action, such as `print(obj.__dict__.keys())`

```
class A:
  def __init__(self, factor):
    self.__factor = factor

  def op1(self):
    print('Op1 with factor {}...'.format(self.__factor))

class B(A):
  def op2(self, factor):
    self.__factor = factor
    print('Op2 with factor {}...'.format(self.__factor))

obj = B(100)
obj.op1() # Op1 with factor 100...
obj.op2(42) # Op2 with factor 42...
obj.op1() # Op1 with factor 100... <- Wohoo! Now it's GOOD!
```

```
class MyClass:
    def __init__(self):
        self.__secret = "42"

obj = MyClass()
# print(obj.__secret)       # Raises AttributeError
print(obj._MyClass__secret) # Success: "42"
```

## The `__str__` method

- The `__str__()` method is a special method that controls what is returned when the object is printed:

```

class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def __str__(self):
    return f"{self.name} ({self.age})"

p1 = Person("Tobias", 36)

print(p1)

# It print Tobias (36)

```

## The `__repr__` method

- Used in debugging and logging
- Fallback for `__str__`: If a class does not define a `__str__` method, Python will fall back to using `__repr__` for user-facing string conversions (e.g., when using print())

```

class Point:
  def __init__(self, x, y):
    self.x = x
    self.y = y

    def __repr__(self):
        return f"Point(x={self.x}, y={self.y})"

# Usage

p = Point(10, 20)
print(repr(p)) # Explicitly calls **repr**
print(p) # Calls **repr** by default if **str** is not defined

```

## The `__eq__()` method

- The `__eq__()` method in Python is a "dunder" (double-underscore) method that defines the behavior of the equality operator (==) for a class.
- By implementing `__eq__()`, you can customize how instances of your class are compared for equality based on their values or attributes, rather than their memory location.
- How it Works: When you use the `==` operator to compare two objects (e.g., `obj1 == obj2`), Python automatically calls `obj1.__eq__(obj2)` behind the scene
  - The method takes two arguments: `self` (the object on the left of the == operator) and `other` (the object on the right).
  - It should return a boolean value (True or False) to indicate whether the objects are considered equal based on your custom logic.
  - If you don't define `__eq__()` in your class, the default behavior is to compare object identity (memory location), similar to the is operator, meaning two different instances are always unequal by default.

```
class Person:
    def __init__(self, first_name, last_name, age):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age

    def __eq__(self, other):
        # Check if the other object is an instance of the same class
        # (optional but recommended for robust comparison)
        if not isinstance(other, Person):
            return NotImplemented

        # Define equality based on the 'age' attribute
        return self.age == other.age

# Create instances
john = Person('John', 'Doe', 25)
jane = Person('Jane', 'Doe', 25)
someone_else = Person('Peter', 'Pan', 30)

# Compare instances using the == operator (which calls __eq__())
print(f"john == jane: {john == jane}") # Output: john == jane: True
print(f"john == someone_else: {john == someone_else}") # Output: john == someone_else: False
print(f"john == 25: {john == 25}") # Output: john == 25: False (due to the isinstance check)
```

## The `__lt__()`, `__gt__()` method

- The `__lt__` and `__gt__` methods in Python are "dunder" (double underscore) or magic methods used for operator overloading of the less-than (<) and greater-than (>) comparison operators

```
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

    def __str__(self):
        return 'Rectangle (width={0}, height={1})'.format(self.width, self.height)

    def __repr__(self):
        return 'Rectangle({0}, {1})'.format(self.width, self.height)

    def __eq__(self, other):
        if isinstance(other, Rectangle):
            return (self.width, self.height) == (other.width, other.height)
        else:
            return False

    def __lt__(self, other):
        if isinstance(other, Rectangle):
            return self.area() < other.area()
        else:
            return NotImplemented
```

```
r1 = Rectangle(100, 200)
r2 = Rectangle(10, 20)

r1 < r2 # False
r2 < r1 # True
```

- What about `>`?

```
r1 > r2 # True
```

- How did that work? We did not define a `__gt__` method.
  - Well, Python cleverly decided that since `r1 > r2` was not implemented, it would give `r2 < r1` a try. And since, `__lt__` **is** defined, it worked!
- Of course, `<=` is not going to magically work!. You must overloading `__le__` method

```
r1 <= r2 # TypeError: '<=' not supported between instances of 'Rectangle' and 'Rectangle'
```

## Python Operator Overloading – Magic Methods

- In most real projects you usually only need:

`__eq__`, `__lt__`, `__add__`, `__len__`, `__getitem__`, `__str__`, `__repr__`

```
| Category            | Operator / Usage | Magic Method            |
| ------------------- | ---------------- | ----------------------- | --------- |
| Comparison          | `<`              | `__lt__`                |
| Comparison          | `<=`             | `__le__`                |
| Comparison          | `>`              | `__gt__`                |
| Comparison          | `>=`             | `__ge__`                |
| Comparison          | `==`             | `__eq__`                |
| Comparison          | `!=`             | `__ne__`                |
| Arithmetic          | `+`              | `__add__`               |
| Arithmetic          | `-`              | `__sub__`               |
| Arithmetic          | `*`              | `__mul__`               |
| Arithmetic          | `/`              | `__truediv__`           |
| Arithmetic          | `//`             | `__floordiv__`          |
| Arithmetic          | `%`              | `__mod__`               |
| Arithmetic          | `**`             | `__pow__`               |
| Arithmetic          | `divmod()`       | `__divmod__`            |
| Reflected           | `+`              | `__radd__`              |
| Reflected           | `-`              | `__rsub__`              |
| Reflected           | `*`              | `__rmul__`              |
| Reflected           | `/`              | `__rtruediv__`          |
| Reflected           | `//`             | `__rfloordiv__`         |
| Reflected           | `%`              | `__rmod__`              |
| Reflected           | `**`             | `__rpow__`              |
| In-place            | `+=`             | `__iadd__`              |
| In-place            | `-=`             | `__isub__`              |
| In-place            | `*=`             | `__imul__`              |
| In-place            | `/=`             | `__itruediv__`          |
| In-place            | `//=`            | `__ifloordiv__`         |
| In-place            | `%=`             | `__imod__`              |
| In-place            | `**=`            | `__ipow__`              |
| Unary               | `-x`             | `__neg__`               |
| Unary               | `+x`             | `__pos__`               |
| Unary               | `abs(x)`         | `__abs__`               |
| Unary               | `~x`             | `__invert__`            |
| Bitwise             | `&`              | `__and__`               |
| Bitwise             | `                | `                       | `__or__`  |
| Bitwise             | `^`              | `__xor__`               |
| Bitwise             | `<<`             | `__lshift__`            |
| Bitwise             | `>>`             | `__rshift__`            |
| Bitwise (reflected) | `&`              | `__rand__`              |
| Bitwise (reflected) | `                | `                       | `__ror__` |
| Bitwise (reflected) | `^`              | `__rxor__`              |
| Bitwise (reflected) | `<<`             | `__rlshift__`           |
| Bitwise (reflected) | `>>`             | `__rrshift__`           |
| Bitwise (in-place)  | `&=`             | `__iand__`              |
| Bitwise (in-place)  | `                | =`                      | `__ior__` |
| Bitwise (in-place)  | `^=`             | `__ixor__`              |
| Bitwise (in-place)  | `<<=`            | `__ilshift__`           |
| Bitwise (in-place)  | `>>=`            | `__irshift__`           |
| Matrix              | `@`              | `__matmul__`            |
| Matrix              | `@` (right)      | `__rmatmul__`           |
| Matrix              | `@=`             | `__imatmul__`           |
| Container           | `len(x)`         | `__len__`               |
| Container           | `x[i]`           | `__getitem__`           |
| Container           | `x[i]=v`         | `__setitem__`           |
| Container           | `del x[i]`       | `__delitem__`           |
| Container           | `v in x`         | `__contains__`          |
| Iteration           | `for x in obj`   | `__iter__`              |
| Iteration           | `next()`         | `__next__`              |
| Callable            | `obj()`          | `__call__`              |
| Conversion          | `str(x)`         | `__str__`               |
| Conversion          | `repr(x)`        | `__repr__`              |
| Conversion          | `int(x)`         | `__int__`               |
| Conversion          | `float(x)`       | `__float__`             |
| Conversion          | `bool(x)`        | `__bool__`              |
| Conversion          | `bytes(x)`       | `__bytes__`             |
| Hashing             | `hash(x)`        | `__hash__`              |
| Context             | `with obj:`      | `__enter__`, `__exit__` |
```

## Don't use mutable defaults parameters

- **BAD**

```

class Student:
  def __init__(self, name: str, grades: list[int] = []): # BAD
    self.name = name
    self.grades = grades

  def take_exam(self, result: int):
    self.grades.append(result)

bob = Student('Bob')
rolf = Student('Rof')

bob.take_exam(90)

print(bob.grades)
print(rolf.grades)

# Print same output is [90]

```

- Why This Happens
  - Default parameter values are evaluated once, when the function is defined—not each time it is called.

  - So the default [] (empty list) is created only once.

  - All objects using that default will share the same list in memory.

  - Thus bob.grades and rolf.grades point to the same list, causing unexpected behavior.

- Correct approach

```

from typing import Optional

class Student:
  def __init__(self, name: str, grades: Optional[list[int]] = None):
    self.name = name
    self.grades = grades or []

```

# Function

## Argument vs Parameter

- In programming, the key difference is that a **parameter** is a **variable** in a function's definition (a placeholder), while an argument is the actual value passed to that function when it is called (the specific data).

| Feature           | Parameter                                                    | Argument                                                        |
| ----------------- | ------------------------------------------------------------ | --------------------------------------------------------------- |
| **Role**          | A placeholder variable in the function definition/signature. | The actual data or value supplied when the function is invoked. |
| **Location**      | Defined in the function header (declaration).                | Provided in the function call statement.                        |
| **Timing**        | Specified at compile-time/definition.                        | Passed at run-time/execution.                                   |
| **Also Known As** | Formal parameter, formal argument.                           | Actual parameter, actual argument.                              |

## Keyword-only arguments

- In Python, keyword-only arguments are function parameters that must be passed using their names, not by position.
- They are defined by placing a `*` in the function signature. All parameters after `*` become keyword-only.

```

def response(status_code, schema=None, \*, description=None, headers=None):
pass

```

## First-class functions

- Assigning Functions to Variables
- Passing Functions as Arguments
- Returning Functions from Other Functions
- Storing Functions in Data Structures

```

def msg(name):
return f"Hello, {name}!"

# Assigning the function to a variable

f = msg

# Calling the function using the variable

print(f("Emma"))

```

```

def msg(name):
return f"Hello, {name}!"

def fun1(fun2, name):
return fun2(name)

# Passing the msg function as an argument

print(fun1(msg, "Alex"))

```

```

def fun1(msg):
def fun2():
return f"Message: {msg}"
return fun2

# Getting the inner function

func = fun1("Hello, World!")
print(func())

def divide(dividend, divisor):
if divisor == 0:
raise ZeroDivisionError('Divisor cannot be 0.')

    return dividend / divisor

def calculate(*value, operator):
return operator(*values)

result = calculate(20, 4, operator=divide)
print(result)

```

```

def add(x, y):
return x + y

def subtract(x, y):
return x - y

# Storing functions in a dictionary

d = {
"add": add,
"subtract": subtract
}

# Calling functions from the dictionary

print(d["add"](5, 3))
print(d["subtract"](5, 3))

```

## Lambda functions

- The expression is executed and the result is returned:
- Syntax: `lambda arguments : expression`

## Destructuring

- If we try to destructure a collection with more or fewer values than we provide variables, we end up with a ValueError.
- Standard destructuring assignments

```

# or

# x, y = (5, 11)

# (5, 11) and 5, 11 are tuple

x, y = 5, 11

```

- Destructuring dictionaries

```

my_dict = {"name": "Bob", "age": 25}
x, y = my_dict

```

- If you wanted to destructure the dictionary values only, you can do:

```

my_dict = {"name": "Bob", "age": 25}
x, y = my_dict.values() # "Bob", 25

```

- Destructuring in for loops

```

example_list = ["A", "B", "C"]

for counter, letter in enumerate(example_list):
print(counter, letter)

# 0 A

# 1 B

# 2 C

```

```

people = [
("Bob", 42, "Mechanic"),
("James", 24, "Artist"),
("Harry", 32, "Lecturer")
]

for name, age, profession in people:
print(f"Name: {name}, Age: {age}, Profession: {profession}")

```

- Ignoring Values: So, what do we do if we have a collection of values and we don't want to assign all of them? We can use an \_ in place of a variable name.

```

person = ("Bob", 42, "Mechanic")
name, \_, profession = person

print(name, profession) # Bob Mechanic

```

- Using `*` to Collect Values: In Python, we can use the `*` operator to collect leftover values when performing a destructuring assignment. For example, we might have a list of numbers, and we want to grab the first number, and then assign the remaining numbers to a second variable

```

head, \*tail = [1, 2, 3, 4, 5]

print(head) # 1
print(tail) # [2, 3, 4, 5]

```

```

\*head, tail = [1, 2, 3, 4, 5]

print(head) # [1, 2, 3, 4]
print(tail) # 5

```

```

head, \*middle, tail = [1, 2, 3, 4, 5]

print(head) # 1
print(middle) # [2, 3, 4]
print(tail) # 5

```

## Iterable unpacking

- Iterable unpacking uses the syntax \*iterable_name to pass the elements of an iterable
  as positional arguments to a function

```

# arguments.unpack.iterable.py

def func(a, b, c):
print(a, b, c)

values = (1, 3, -7)
func(\*values) # equivalent to: func(1, 3, -7)

```

## Dictionary unpacking

- Dictionary unpacking is to keyword arguments what iterable unpacking is to
  positional arguments. We use the syntax `**dictionary_name` to pass keyword
  arguments, constructed from the keys and values of a dictionary, to a function

```

# arguments.unpack.dict.py

def func(a, b, c):
print(a, b, c)

values = {'b': 1, 'c': 2, 'a': 42}
func(\*\*values) # equivalent to func(b=1, c=2, a=42)

```

## A global variable

**Key characteristics of global variables:**

- **Scope**: They have global scope within the module where they are defined.
- **Accessibility**: You can read the value of a global variable directly inside a function without any special declaration.
- **Modification**: To modify a global variable inside a function, you must explicitly declare it using the **global** keyword. If you assign a new value to a variable with the same name inside a function without using **global**, Python will create a new local variable with that name, rather than modifying the **global** one

**Example of using and modifying a global variable:**

```

# Define a global variable

global_var = "Hello"

def access_global():
print(f"Inside function (accessing): {global_var}")

def modify_global():
global global_var # Declare intent to modify the global variable
global_var = "World"
print(f"Inside function (modifying): {global_var}")

access_global()
print(f"Outside function (after access): {global_var}")

modify_global()
print(f"Outside function (after modification): {global_var}")

```

## Arbitrary Positional Arguments

- **Purpose**: To collect an arbitrary number of non-keyword (positional) arguments into a single tuple within the function.
- **Syntax**: Precede a parameter name in the function definition with a single asterisk (`*`).

```

    def calculate_sum(*numbers):
        total = 0
        for num in numbers:
            total += num
        print(f"The sum is: {total}")

    calculate_sum(1, 2, 3)  # numbers will be (1, 2, 3)
    calculate_sum(10, 20, 30, 40, 50) # numbers will be (10, 20, 30, 40, 50)

```

## Mixing Positional and Arbitrary Arguments

- The parameter that accepts an arbitrary number of arguments must be placed last in the function definition

```

def make_pizza(size, \*toppings):
#Summarize the pizza we are about to make.
print(f"\nMaking a {size}-inch pizza with the following toppings:")
for topping in toppings:
print(f"- {topping}")

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

```

## Arbitrary Keyword Arguments

- This is achieved by placing a double asterisk `**` before a parameter name in the function definition. This parameter will then collect all the passed keyword arguments into a dictionary.

```

def build_profile(first, last, \*\*user_info): # Build a dictionary containing everything we know about a user.
user_info['first_name'] = first
user_info['last_name'] = last
return user_info

user_profile = build_profile(
'albert',
'einstein',
location='princeton',
field='physics'
)
print(user_profile)

```

## Type hint

- Type hints are a feature in Python that allow developers to annotate their code with expected types for variables and function arguments. This helps to improve code readability and provides an opportunity to catch errors before runtime using type checkers like mypy.
- Variable and Function Type Hints

```

age: int = 25
def greet(name: str) -> str:
return f"Hello, {name}!"

```

- Function Return Type

```

def add_numbers(x: int, y: int) -> int:
return x + y

```

- Optional Types and Collections

```

from typing import Optional, List, Tuple

def get_user(id: int) -> Optional[str]:
return None if id == 0 else "User"

def sum(num: List[int]) -> int:
return sum(num)

def get_name_and_age() -> Tuple[str, int]:
return ("Abc", 25)

```

- Python ≤ 3.8

```

from typing import List, Optional, Tuple

def f(data: List[int]) -> Optional[Tuple[int, str]]:
return None

```

- Python ≥ 3.10

```

def f(data: list[int]) -> tuple[int, str] | None:
return None

```

- When Forward References Are Needed in Python
  - When a method returns the same class (self-type)
  - When two classes reference each other (mutual references)
  - Recursive data structures
  - When annotating classmethods that return the class
  - When using complex types involving the class
  - When referencing a type defined later in the file

```

class User:
def clone(self) -> "User":
return User()

```

```

class A:
def set_b(self, b: "B"): ...

class B:
def set_a(self, a: "A"): ...

```

```

class Node:
def **init**(self, value: int, left: "Node" = None, right: "Node" = None):
self.value = value

```

```

class Product:
@classmethod
def from_name(cls, name: str) -> "Product":
return cls(name)

```

```

from typing import List

class Shape:
def combine(self, others: List["Shape"]) -> "Shape":
return self

```

```

# When referencing a type defined later in the file

def make(obj: "Factory"): ...

```

- Conclusion — Which Approach Should You Use?

| Python Version | Syntax Style                        | Recommendation          |
| -------------- | ----------------------------------- | ----------------------- |
| **3.11+**      | `-> Self`                           | ⭐ **Best option**      |
| **3.9–3.10**   | Generics + `Type[T]`                | 👍 **Most common**      |
| **3.7–3.8**    | `"User"` (string forward reference) | ✔ **Legacy-compatible** |

- Use Self - python 3.11+

```

from typing import Self

class User:
def **init**(self, name: str):
self.name = name

    @classmethod
    def from_fullname(cls, fullname: str) -> Self:
        first, last = fullname.split()
        return cls(first + " " + last)

u = User.from_fullname("John Doe")

```

- Use Generics + `Type[T]` - python 3.9 -> 3.10

```

from typing import Type, TypeVar

T = TypeVar("T", bound="User")

class User:
def **init**(self, name: str):
self.name = name

    @classmethod
    def from_fullname(cls: Type[T], fullname: str) -> T:
        first, last = fullname.split()
        return cls(first + " " + last)

```

# Decorators

- A design pattern that allows you to modify or extend the behavior of a function or a class without changing its source code
- This is achieved by "wrapping" the original function with another function (the decorator), which adds functionality before and/or after the original code runs.
- A decorator is essentially a function that takes another function as an argument and returns a new function with enhanced functionality.
- Decorators are often used in scenarios such as logging, authentication and memorization, allowing us to add additional functionality to existing functions or methods in a clean, reusable way.
- Declare

```

def decorator(func):
def wrapper():
print("Before calling the function.")
func()
print("After calling the function.")
return wrapper

# Using the @ symbol is equivalent to calling the decorator on the function it wraps and assigning the

# return value to the original name in the same scope

# greet = decorator(greet)

@decorator # Applying the decorator to a function
def greet():
print("Hello, World!")

greet()

```

## Define function Decorators with `functools.wraps`

- The cause of this isn’t hard to see. The **decorator** function returns the **wrapper** defined within its body. The **wrapper** function is what’s assigned to the **say_whee** name in the containing module because of the decorator.
- This behavior is problematic because it undermines tools that do introspection, such as debuggers

```

def decorator(func):
def wrapper_do_twice():
print("Something is happening before the function is called.")
func()
print("Something is happening after the function is called.")
return wrapper

@decorator
def say_whee():
print("Whee!")

print(say_whee.**name**)

# wrapper_do_twice

```

- To fix this, decorators should use the @wraps decorator, which will preserve information about the original function

```

# import functools

from functools import wraps

def do_twice(func): # @functools.wraps
@wraps(func)
def wrapper_do_twice(*args, \*\*kwargs):
func(*args, **kwargs)
return func(\*args, **kwargs)
return wrapper_do_twice

@do_twice
def say_whee():
print("Whee!")

print(say_whee.**name**)

# say_whee

```

## Decorators function with parameter

- Explanation of Parameters
  - `decorator_name(func)`: This is the decorator function. It takes another function (func) as input.
  - `**wrapper(*args, kwargs)`: A nested function that wraps func. `*args` collects positional arguments, `**kwargs` collects keyword arguments, so wrapper works with any function.
  - `@decorator_name`: Syntax sugar for `add = decorator_name(add)`.

```

def decorator_name(func):
def wrapper(*args, \*\*kwargs):
print("Before execution")
result = func(*args, \*\*kwargs)
print("After execution")
return result
return wrapper

@decorator_name
def add(a, b):
return a + b

print(add(5, 3))

```

## Decorators with parameter - A decorator factory

- Let's simplify this example now, going back to a single decorator: max_result(). We
  want to make it so that we can decorate different functions with different thresholds,
  as we don't want to write one decorator for each threshold. Let's therefore amend
  max_result() so that it allows us to decorate functions by specifying the threshold
  dynamicall

- Before: We want a decorator that prints an error message when the result of a function is greater than a certain threshold

```

from time import time
from functools import wraps
def measure(func):
@wraps(func)
def wrapper(*args, \*\*kwargs):
t = time()
result = func(*args, \*\*kwargs)
print(func.**name**, 'took:', time() - t)
return result
return wrapper

def max_result(func):
@wraps(func)
def wrapper(*args, \*\*kwargs):
result = func(*args, \*\*kwargs)
if result > 100:
print(
f'Result is too big ({result}). '
'Max allowed is 100.'
)
return result
return wrapper

@measure
@max_result
def cube(n):
return n \*\* 3

print(cube(2))
print(cube(5))

```

- After

```

# decorators/decorators.factory.py

from functools import wraps

def max_result(threshold):
def decorator(func):
@wraps(func)
def wrapper(*args, \*\*kwargs):
result = func(*args, \*\*kwargs)
if result > threshold:
print(
f'Result is too big ({result}). '
f'Max allowed is {threshold}.'
)
return result
return wrapper
return decorator

@max_result(75)
def cube(n):
return n \*\* 3

print(cube(5))

```

# Generator

## Why Do We Need Generators?

- Memory Efficient : Handle large or infinite data without loading everything into memory.
- No List Overhead : Yield items one by one, avoiding full list creation.
- Lazy Evaluation : Compute values only when needed, improving performance.
- Support Infinite Sequences : Ideal for generating unbounded data like Fibonacci series.
- Pipeline Processing : Chain generators to process data in stages efficiently.

## Iterable vs Iterator

| **Criteria**                       | **Iterable**                                   | **Iterator**                                                                   |
| ---------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------ |
| **Definition**                     | An object that can be looped over (loopable).  | An object that can return the next element when `next()` is called.            |
| **Purpose**                        | Stores data that can be iterated.              | Retrieves elements from an iterable one at a time, maintaining internal state. |
| **Has `__iter__()`?**              | ✔ Yes                                          | ✔ Yes (returns itself)                                                         |
| **Has `__next__()`?**              | ❌ No                                          | ✔ Yes                                                                          |
| **Usable with `for` loop?**        | ✔ Yes                                          | ✔ Yes                                                                          |
| **Usable directly with `next()`?** | ❌ No                                          | ✔ Yes                                                                          |
| **Maintains iteration state?**     | ❌ No                                          | ✔ Yes (remembers current position)                                             |
| **Examples**                       | `list`, `tuple`, `dict`, `set`, `str`, `range` | `iter(list)`, generator, file object                                           |
| **How to obtain an iterator?**     | Call `iter(x)`                                 | Already an iterator                                                            |
| **When elements are exhausted**    | No error                                       | Raises `StopIteration`                                                         |
| **Memory usage**                   | May hold all items in memory                   | Typically uses less memory (generators produce items lazily)                   |

## Yield vs Return

- **Yield**: is used in generator functions to provide a sequence of values over time. When yield is executed, it pauses the function, returns the current value and retains the state of the function. This allows the function to continue from same point when called again, making it ideal for generating large or complex sequences efficiently.
- **Return**: is used to exit a function and return a final value. Once return is executed, function is terminated immediately and no state is retained. This is suitable for cases where a single result is needed from a function.

## `next()` function

- Each call to `next()` on the generator object resumes execution right after the yield statement, where it last left off.
- Exception: `StopIteration`

```

# first.n.squares.manual.py

def get_squares_gen(n):
for x in range(n):
yield x \*\* 2

squares = get_squares_gen(4) # this creates a generator object

print(squares) # <generator object get_squares_gen at 0x10dd...>
print(next(squares)) # prints: 0
print(next(squares)) # prints: 1
print(next(squares)) # prints: 4
print(next(squares)) # prints: 9

# the following raises StopIteration, the generator is exhausted,

# any further call to next will keep raising StopIteration

print(next(squares))

```

## Generator functions

- These are very similar to regular functions, but instead
  of returning results through return statements, they use yield, which allows
  them to suspend and resume their state between each call.

- Syntax

```

def generator_function_name(parameters): # Your code here
yield expression # Additional code can follow

```

- The result of the two print statements will be the same: [0, 1, 4, 9, 16, 25, 36,
  49, 64, 81].
  - `get_squares()`: is a classic function that collects all the squares of numbers in `[0,..,n]` in a list, and returns it
  - `get_squares_gen()`: is a generator and behaves very differently. Each time the interpreter reaches the yield line, its execution is suspended. The only reason those print statements return the same result is because we fed `get_squares_gen()` to the `list()` constructor

```

# first.n.squares.py

def get_squares(n): # classic function approach
return [x ** 2 for x in range(n)]

print(get_squares(10))

def get_squares_gen(n): # generator approach
for x in range(n):
yield x \*\* 2 # we yield, we don't return

print(list(get_squares_gen(10)))

```

## `return` in generator function

- It will cause a StopIteration exception to be raised, effectively ending the iteration

```

def geometric_progression(a, q):
k = 0
while True:
result = a \* q\*\*k
if result <= 100000:
yield result
else:
return
k += 1

for n in geometric_progression(2, 5):
print(n)

```

## `send()` in generator function

- The `send` function is a method that allows us to send a value to a generator at its current yield expression
- Syntax:

```

generator.send(value)

```

- Example

```

def counter(start=0):
n = start
while True:
result = yield n # A
print(type(result), result) # B
if result == 'Q':
break
n += 1

c = counter()
print(next(c)) # C
print(c.send('Wow!')) # D
print(next(c)) # E
print(c.send('Q')) # F

```

```

0
<class 'str'> Wow!
1
<class 'NoneType'> None
2
<class 'str'> Q
Traceback (most recent call last):
File "gen.send.py", line 15, in <module>
print(c.send('Q')) # F
StopIteration

```

- Step #C: Within the generator, n is set to the same value as start. The while loop is entered, execution stops (#A), and n (0) is yielded back to the caller. 0 is printed on the console.
- Step #D: execution resumes, result is set to 'Wow!'(still #A), and then its type and value are printed on the console (#B). result is not 'Q', so n is incremented by 1 and execution goes back to the while condition, which, being True, evaluates to True (that wasn't hard to guess, right?). Another loop cycle begins, execution stops again (#A), and n (1) is yielded back to the caller. 1 is printed on the console.
- Step #E: , execution is resumed again (#A), and because we are not sending anything to the generator explicitly, the yield n expression (#A) returns None (the behavior is exactly the same as when we call a function that does not return anything). result is therefore set to None, and its type and value are again printed on the console (#B). Execution continues, result is not 'Q', so n is incremented by 1, and we start another loop again. Execution stops again (#A) and n (2) is yielded back to the caller. 2 is printed on the console
- Step #F: send again (#F), but this time we pass in 'Q', and so when execution is resumed, result is set to 'Q' (#A). Its type and value are printed on the console (#B), and then finally the if clause evaluates to True and the while loop is stopped by the break statement. The generator naturally terminates, which means a StopIteration exception is raised. You can see the print of its traceback on the last few lines printed on the console

## The `yield from` expression

- not use `yeild from`. Prints the numbers 4, 9, and 16 on the console

```

# gen.yield.for.py

def print_squares(start, end):
for n in range(start, end):
yield n \*\* 2

for n in print_squares(2, 5):
print(n)

```

- use `yeild from`. Prints the numbers 4, 9, and 16 on the console

```

# gen.yield.from.py

def print_squares(start, end):
yield from (n \*\* 2 for n in range(start, end))

for n in print_squares(2, 5):
print(n)

```

## Generator expressions

- **Generator expressions** are a concise way to create generators. They are similar to list comprehensions but use parentheses instead of square brackets and are more memory efficient.

- Syntax

```

(expression for item in iterable)

```

# Package and module

## What is module

- In Python, a module is simply a file containing Python definitions and statements. It is used to logically organize code into separate files, making programs easier to maintain and reuse
- Key Characteristics
  - **File-Based**: Any text file with a .py extension is technically a module.
  - **Encapsulation**: Each module has its own private namespace, which prevents naming conflicts between different parts of a program.
  - **Contents**: A module can define functions, classes, and variables, and can also include runnable initialization code
- Using Modules:
  - To use the contents of a module, you must `import` it into your script
- Types of Modules
  - **Built-in Modules**: Modules like os, math, sys, and random that are part of the Python Standard Library and come bundled with your installation.
  - **User-defined Modules**: Custom files created by you to organize your own project's code.
  - **Third-party Modules**: Libraries developed by others (e.g., requests, numpy) that can be installed via package managers like pip

- A module is simply another data type. And the modules we use are instances of that data type.

```
import math

# globals() is a built-in function that Returns the global namespace as a dictionary.
# representing the current global symbol table

# local() is a built-in function that Returns the local namespace as a dictionary.

globals()['math'] # <module 'math' (built-in)>

type(math) # module

math # <module 'math' (built-in)>

# The id() function in Python is a built-in function that returns the identity of an object.
# This identity is a unique and constant integer assigned to the object when it is created,
# and it remains the same throughout its lifetime

id(math) # 2043440173664
```

## `__name__` variable

- Built-in variable that automatically gets assigned a value by the Python interpreter based on how the script is being executed
- How `__name__` works
  - **When a script is run directly**: If a Python file is executed as the main program (e.g., by running python your_script.py from the command line), the `__name__` variable within that file is set to the string `'__main__'`
  - **When a script is imported as a module**: If a Python file is imported into another Python file as a module (e.g., import your_module), the `__name__` variable within the imported file is set to the name of the module (the filename without the .py extension).`
- Common Use Case: `if __name__ == '__main__'`:
  - Provide a clear entry point: Define the main logic of your script within this block.
  - Prevent unintended execution: Ensure that certain code (like test cases or setup functions) only runs when the file is the primary executable, avoiding side effects when imported
  - Create reusable modules: Write modules that can be both executed independently and imported by other scripts without automatically running their main logic

```

# my_module.py

def greet(name):
return f"Hello, {name}!"

if **name** == '**main**': # This code will only run when my_module.py is executed directly
print(greet("World"))
print(f"This script's **name** is: {**name**}")

```

If you run python my_module.py, the output will be:

```

Hello, World!
This script's **name** is: **main**

```

If you import my_module into another script:

```

# another_script.py

import my_module

print(my_module.greet("Python"))
print(f"my_module's **name** when imported is: {my_module.**name**}")

```

The output will be:

```

Hello, Python!
my_module's **name** when imported is: my_module

```

## Imports

- The `import` statement is used to bring modules or specific components (functions, classes, variables) from modules into the current namespace, making them available for use. This promotes code reusability and organization

## Absolute Imports

- An absolute path is the full, complete address of a file or directory, starting from the root of the file system

```

my_project/
│
├── app/
│ ├── __init__.py
│ ├── services/
│ │ ├── __init__.py
│ │ └── calculator.py
│ └── utils/
│ ├── __init__.py
│ └── formatter.py
│
└── main.py

```

```
# my_project/app/services/calculator.py

def add(a, b):
  return a + b
```

```
# main.py

from app.services.calculator import add

result = add(5, 3)
print(result)
```

## Relative Imports

- A relative path is a location defined in relation to the current working directory
- When to use `from . import module_name`
  - You use `.` when the file you want to import is in the same folder as the current file
- When to use `from ..folder_name import module_name`
  - Use `.folder_name` when the module is inside a subfolder of the current folder.
- When to use `from ...folder_name import module_name`
  - Use `...folder_name` when the module is inside a sub-subfolder of the current folder.

```
project/
app/
  __init__.py
utils/
  __init__.py
  formatter.py
services/
  __init__.py
  printer.py
```

```
# utils/formatter.py

def to_upper(s):
  return s.upper()
```

```
# services/printer.py

from ..utils.formatter import to_upper

def print_upper(text):
print(to_upper(text))
```

```
my_project/
│
├── main.py
└── utils/
├── **init**.py
├── math_tools.py
└── string_tools.py
```

```
# utils/math_tools.py

def add(a, b):
  return a + b
```

```
# utils/string_tools.py

def shout(text):
  return text.upper()
```

```

# utils/__init__.py

from . import math_tools
from . import string_tools

```

## Example Relative imports

```
my_project/
├── main.py
└── my_package/
    ├── __init__.py
    ├── module_a.py           # Contains: class Alpha
    ├── subpackage/
    │   ├── __init__.py
    │   ├── module_b.py       # <--- WE ARE CODING HERE
    │   └── utils.py          # Contains: def get_time()
    └── other_sub/
        ├── __init__.py
        └── module_c.py       # Contains: def helper()
```

- One Dot `.`: Current Directory

```
# In module_b.py

from .utils import get_time
```

- Two Dots `..`: Parent Directory

```
# module_b.py

from ..module_a import Alpha
```

- Three Dots `...`: Grandparent Directory

```
my_project/
├── __init__.py
├── global_utils.py       # <--- Target: Three dots away
└── my_package/
    ├── __init__.py
    └── subpackage/
        ├── __init__.py
        └── module_b.py   # <--- We are here

```

```
#  in module_b.py

from ...global_utils import some_function
```

## `__init__` file

- `__init__.py` file is a Python file that is executed when a package is imported and is used to initialize the package's namespace and structure how its contents are accessed.
- Package Recognition: In older Python versions (prior to 3.3), the `__init__.py` file was required for Python to recognize a directory as a package. While no longer strictly mandatory in Python 3.3+ (due to implicit namespace packages), it is still widely used and considered a best practice for most projects
- The `__all__` variable is a list of strings that indicate the names that should be imported when using the `*` operator
- Key purposes
  - It marks the directory as a Python Package so that the interpreter can find the modules inside it.
  - It can contain initialization code for the Package, such as importing submodules, defining variables, or executing other code.
  - Import up two levels: `from .... import x`

| Level                   | Syntax                        | Meaning                                  |
| ----------------------- | ----------------------------- | ---------------------------------------- |
| 1 level up              | `from .. import x`            | Go to the parent directory               |
| 2 levels up             | `from .... import x`          | Go to the parent of the parent directory |
| 1 level up + subfolder  | `from ..subfolder import x`   | Go up one level, then into a subfolder   |
| 2 levels up + subfolder | `from ....subfolder import x` | Go up two levels, then into a subfolder  |

- Creating a Simple Package Using `__init__.py` File

```

mypackage/
**init**.py
module1.py
module2.py
main.py

```

```

# **init**.py

# Define the **all** variable

**all** = ["module1", "module2"]

# Import the submodules

from . import module1
from . import module2

```

```

# module1.py

# Define a function called func1

def func1():
print("This is func1 from module1")

```

```

# module2.py

# Define a function called func2

def func2():
print("This is func2 from module2")

```

```

# main.py

# Import the package

import mypackage

# Import the modules

import mypackage.module1
import mypackage.module2

# Call the functions

mypackage.module1.func1()
mypackage.module2.func2()

# Output

# This is func1 from module1

# This is func2 from module2

```

## Set Up Virtual Environment and Install Dependencies

- Step 1: Create a virtual environment (recommended).

```

python -m venv venv

# python -m venv <<folder_name>>

```

- Step 2: Activate the virtual environment
  - On the window

```

venv\Scripts\activate

# <<folder_name>>\Scripts\activate

```

- On macOS / Linux:

```

source venv/bin/activate

# source <<folder_name>>/bin/activate

```

- Step 3: Install required libraries from requirements.txt

```

pip install -r requirements.txt

```

# Other

## Multi-Line Statements

### Implicit

- Implicit expressions in:
  - list literals []
  - tuple literals ( )
  - dictionary literals { }
  - set literals { }
  - function arguments / parameters

```
a = [1, #first element
    2, #second element
    3, #third element
    ]
```

```
def my_func(a, #some comment
           b, c):
    print(a, b, c)

my_func(10, #comment
       20, #comment
       30)
```

### Explicit

- You can break up statements over multiple lines explicitly, by using the `\` (backslash ) character
- Multi-line statements are not implicitly converted to a single logical line.
- Comments cannot be part of a statement, not even a multi-line statement.

```
a = 10
b = 20
c = 30
if a > 5 \
    and b > 10 \
    and c > 20:
    print('yes!!')
```

## Variable names

### Must

- Start with underscore `_` or letter `a-z A-Z`
- Followed by any number of underscores `_`, letters `a-z A-Z`, or digits `0-9`
- Cannot be reserved words

| Keyword  | Purpose                           |
| -------- | --------------------------------- |
| False    | Boolean false value               |
| None     | Represents null / no value        |
| True     | Boolean true value                |
| and      | Logical AND                       |
| as       | Alias in import / context manager |
| assert   | Debug assertion                   |
| async    | Define async function             |
| await    | Await async result                |
| break    | Exit loop                         |
| class    | Define class                      |
| continue | Skip to next loop iteration       |
| def      | Define function                   |
| del      | Delete object                     |
| elif     | Else-if condition                 |
| else     | Fallback condition                |
| except   | Catch exception                   |
| finally  | Always execute after try          |
| for      | Loop                              |
| from     | Import from module                |
| global   | Declare global variable           |
| if       | Conditional                       |
| import   | Import module                     |
| in       | Membership test                   |
| is       | Identity comparison               |
| lambda   | Anonymous function                |
| nonlocal | Declare non-local variable        |
| not      | Logical NOT                       |
| or       | Logical OR                        |
| pass     | Do nothing                        |
| raise    | Raise exception                   |
| return   | Return value                      |
| try      | Try block                         |
| while    | Loop                              |
| with     | Context manager                   |
| yield    | Generator output                  |

### Conventions

- `_my_var` (single underscore): This is a convention to indicate **internal use** or **private** objects. Objects named this way will not get imported by a statement such as `from module import *`
- `__my_var` (double underscore): Used to "mangle" class attributes – useful in inheritance chains
- `__my_var__` (double underscore): Used for system-defined names that have a special meaning to the interpreter. Don't invent them, stick to the ones pre-defined by Python!

### Other Naming Conventions

| Item     | Naming Convention                               | Example            |
| -------- | ----------------------------------------------- | ------------------ |
| Module   | short, all lowercase, underscores allowed       | db_utils           |
| Package  | short, all lowercase, preferably no underscores | utilities, dbutils |
| Class    | CapWords (UpperCamelCase)                       | BankAccount        |
| Function | lowercase with underscores (snake_case)         | open_account       |
| Variable | lowercase with underscores (snake_case)         | account_id         |
| Constant | ALL UPPERCASE with underscores                  | MIN_APR            |

## Debug in CLI command - without IDE editor

### Method 1: Start the debugger from the command line on the first line of the file.

- Step 1: Open your terminal or command prompt.
- Step 2: Run your Python script using the -m pdb option:

```

python3 -m pdb your_file_name.py

```

On Window

```

python -m pdb your_file_name.py

```

If it is not py file

```

python -m pdb -m flask run

# python -m pdb -m <command-line>

```

### Method 2: Start the debugger from the command line and debug at the line where the breakpoint is set.

- Step 1: Open your Python file in a text editor.
- Step 2: Insert the following line at the exact point where you want the debugger to pause

**With python < 3.7**

```

import pdb;
pdb.set_trace()

```

**With python >= 3.7** you can simply use the built-in function `breakpoint()` as a shortcut.

- Step 3: Run your script normally from the command line

```

python3 your_file_name.py

```

On Window

```

python your_file_name.py

```

If it is not py file

```

python -m pdb -m flask run

# python -m pdb -m <command-line>

```

### pdb Commands

- Once you are at the (Pdb) prompt, you can use these commands to navigate and inspect your code:
  - `n` (next): Execute the current line and move to the next line in the current function.
  - `s` (step): Step into a function call on the current line.
  - `c` (continue): Continue execution until the next breakpoint or the end of the program.
  - `l` (list): Show the source code around the current line.
  - `p  <variable_name>` (print): Print the value of a variable.
  - `w` (where): Show the current position in the code stack.
  - `b  <line_number>` (break): Set a new breakpoint at a specific line number in the current file.
  - `h` (help): Display a list of all available commands.
  - `q` or exit (quit): Exit the debugger immediately.

## Format datetime to string

```

from datetime import datetime

# Get the current date and time

now = datetime.now()

# Example 1: YYYY-MM-DD HH:MM:SS format

formatted_date_time = now.strftime("%Y-%m-%d %H:%M:%S")
print(f"Current date and time: {formatted_date_time}")

# Example 2: Month Day, Year (e.g., November 27, 2025)

formatted_date = now.strftime("%B %d, %Y")
print(f"Formatted date: {formatted_date}")

# Example 3: Abbreviated weekday and 12-hour time with AM/PM

formatted_time = now.strftime("%a %I:%M %p")
print(f"Formatted time: {formatted_time}")

```

**Common strftime() format codes:**

- %Y: Year with century (e.g., 2025)
- %m: Month as a zero-padded decimal number (01-12)
- %d: Day of the month as a zero-padded decimal number (01-31)
- %H: Hour (24-hour clock) as a zero-padded decimal number (00-23)
- %M: Minute as a zero-padded decimal number (00-59)
- %S: Second as a zero-padded decimal number (00-59)
- %B: Full month name (e.g., November)
- %a: Abbreviated weekday name (e.g., Thu)
- %A: Full weekday name (e.g., Thursday)
- %I: Hour (12-hour clock) as a zero-padded decimal number (01-12)
- %p: Locale's equivalent of AM or PM
- %j: Day of the year as a zero-padded decimal number (001-366)

## index of the day of the week from a date in Python

```

from datetime import date

# Create a date object

my_date = date(2025, 11, 27)

# Get the index of the day of the week

# Monday is 0, Tuesday is 1, ..., Sunday is 6

day_index = my_date.weekday()

print(f"The date is: {my_date}")
print(f"The index of the day of the week is: {day_index}")

```

## Add days to a date in Python

```

from datetime import datetime, timedelta

# Define a starting date

original_date = datetime(2023, 1, 15)
print(f"Original date: {original_date}")

# Add a specific number of days

days_to_add = 7
new_date = original_date + timedelta(days=days_to_add)
print(f"Date after adding {days_to_add} days: {new_date}")

# Example with a different number of days

another_date = datetime(2024, 10, 26, 10, 30, 0)
print(f"Another original date: {another_date}")

more_days = 30
future_date = another_date + timedelta(days=more_days)
print(f"Date after adding {more_days} days: {future_date}")

```

## Errors

- Handling Errors
  - `try` block runs code, raising an exception if any occurs
  - `except` block catches exceptions
  - `finally` block always executes
  - `else` Optional Code to execute if no exception occurred in the try block

```

try: # Code that might raise an exception
result = 10 / 0
except ZeroDivisionError: # Code to handle the specific exception
print("Cannot divide by zero!")
except Exception as e: # Catch-all for other exceptions
print(f"An unexpected error occurred: {e}")
else: # Optional: Code to execute if no exception occurred in the try block
print("No exceptions were raised.")
finally: # Optional: Code that always executes, regardless of exception
print("Execution finished.")

```

- Exception Object (e) Attributes & Methods

| Attribute / Method | Type                | Description                                                                                      |
| ------------------ | ------------------- | ------------------------------------------------------------------------------------------------ |
| `e.args`           | tuple               | The arguments used to create the exception (usually contains the error message).                 |
| `e.__str__()`      | method              | Returns the human-readable string representation of the exception (similar to calling `str(e)`). |
| `e.__repr__()`     | method              | Returns the official string representation, useful for debugging.                                |
| `e.__cause__`      | exception or `None` | The direct cause of the exception when using `raise ... from ...`.                               |
| `e.__context__`    | exception or `None` | The previous exception that was active when the current exception was raised.                    |
| `e.__traceback__`  | traceback object    | Contains the full traceback information used for debugging.                                      |
| `type(e)`          | type                | Returns the exception class (e.g., `<class 'ZeroDivisionError'>`).                               |

- Built-in exception hierarchy of Python

```

BaseException
├── Exception
│ ├── ArithmeticError
│ │ ├── FloatingPointError
│ │ ├── OverflowError
│ │ └── ZeroDivisionError
│ │
│ ├── AssertionError
│ ├── AttributeError
│ ├── BufferError
│ ├── EOFError
│ ├── ExceptionGroup
│ ├── ImportError
│ │ └── ModuleNotFoundError
│ │
│ ├── LookupError
│ │ ├── IndexError
│ │ └── KeyError
│ │
│ ├── MemoryError
│ ├── NameError
│ │ └── UnboundLocalError
│ │
│ ├── OSError
│ │ ├── BlockingIOError
│ │ ├── ChildProcessError
│ │ ├── ConnectionError
│ │ │ ├── BrokenPipeError
│ │ │ ├── ConnectionAbortedError
│ │ │ ├── ConnectionRefusedError
│ │ │ └── ConnectionResetError
│ │ │
│ │ ├── FileExistsError
│ │ ├── FileNotFoundError
│ │ ├── InterruptedError
│ │ ├── IsADirectoryError
│ │ ├── NotADirectoryError
│ │ ├── PermissionError
│ │ ├── ProcessLookupError
│ │ ├── TimeoutError
│ │ └── UnsupportedOperation
│ │
│ ├── ReferenceError
│ ├── RuntimeError
│ │ ├── NotImplementedError
│ │ └── RecursionError
│ │
│ ├── StopAsyncIteration
│ ├── StopIteration
│ ├── SyntaxError
│ │ └── IndentationError
│ │ └── TabError
│ │
│ ├── SystemError
│ ├── TypeError
│ ├── ValueError
│ │ ├── UnicodeError
│ │ │ ├── UnicodeDecodeError
│ │ │ ├── UnicodeEncodeError
│ │ │ └── UnicodeTranslateError
│ │ │
│ │ └── UnsupportedOperation (also appears under OSError subclass)
│ │
│ ├── Warning
│ │ ├── UserWarning
│ │ ├── DeprecationWarning
│ │ ├── PendingDeprecationWarning
│ │ ├── SyntaxWarning
│ │ ├── RuntimeWarning
│ │ ├── FutureWarning
│ │ ├── ImportWarning
│ │ ├── UnicodeWarning
│ │ └── ResourceWarning
│ │
│ └── KeyboardInterrupt
│
├── GeneratorExit
├── KeyboardInterrupt
└── SystemExit

```

## Custom error classes

- Why Define Custom Exceptions?
  - **Clarity**: They provide clear, specific error messages that are relevant to your application.
  - **Granularity**: They allow for more fine-grained error handling, making it easier to pinpoint and address specific issues.
  - **Reusability**: They can be reused across different parts of your application or even in different projects.

- Defining a Custom Exception

```

class MyCustomError(Exception): # Exception raised for custom error scenarios. # Attributes: # message -- explanation of the error

    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

```

```

class MyCustomError(Exception): # Exception raised for custom error in the application.

    def __init__(self, message, error_code):
        super().__init__(message)
        self.error_code = error_code

    def __str__(self):
        return f"{self.message} (Error Code: {self.error_code})"

```

## Raise an exception

- `raise` is the correct Python keyword for signaling an error or an unusual condition in your program, effectively halting its normal flow

```

x = -5
if x < 0:
raise ValueError("Sorry, no numbers below zero are allowed.")

```

## Using raise with a custom exception.

- Raising a Custom Exception

```

def divide(a, b):
if b == 0:
raise MyCustomError("Division by zero is not allowed", 400)
return a / b

```

- Handling Custom Exceptions

```

try:
result = divide(10, 0)
except MyCustomError as e:
print(f"Caught an error: {e}")

```

## Re-raising an exception

- Within an except block, you can use a bare raise statement without any arguments to re-raise the exception that was just caught. This is useful for adding context or performing some logging before propagating the exception further up the call stack

```

try: # Some operation that might raise an exception
result = 10 / 0
except ZeroDivisionError as e:
print(f"An error occurred: {e}") # Re-raises the ZeroDivisionError
raise

```

## Python Docstrings - `__doc__` or `help()`

- Docstrings (Documentation Strings) are special strings used to document Python code. They provide a description of what a module, class, function or method does.
- Syntax
  - Declared using triple quotes (`'''` or `"""`)
  - Written just below the definition of a function, class, or module
  - Unlike comments (#), docstrings can be accessed at runtime using `__doc__` or `help()`

```

def my_function():
"""Demonstrates triple quotes docstring and does nothing."""
return None

print("Using **doc**:")
print(my_function.**doc**)

print("Using help():")
help(my_function)

```

Output

```

Using **doc**:
Demonstrates triple quotes docstring and does nothing.
Using help():
Help on function my_function in module **main**:

my_function()
Demonstrates triple quotes docstring and does no...

```

## API - Application programing interface

- An Application programing interface (API) is a set of commands, functions, protocals and objects that programers can use to create software or interact with an external system

## HTTP Request

### What is an HTTP Request?

An **HTTP request** is a message sent by a **client** (browser, mobile app, API client) to a **server** to ask for a resource or to perform an action.

Examples:

- A browser requests a web page
- A frontend app requests data from a backend API
- A client sends data to create or update a record

HTTP requests follow the **HTTP (HyperText Transfer Protocol)** standard.

---

### Client–Server Model

HTTP works based on a **client–server architecture**:

1. The **client** sends an HTTP request
2. The **server** processes the request
3. The **server** returns an HTTP response

The server does **nothing** until it receives a request.

---

### Structure of an HTTP Request

An HTTP request consists of **four main parts**:

1. Request Line
2. Headers
3. Blank Line
4. Body (optional)

### Example

```

POST /users HTTP/1.1
Host: api.example.com
Content-Type: application/json
Authorization: Bearer token123

{
"name": "Alice",
"email": "alice@example.com
"
}

```

### Request Line

- The request line contains: `METHOD /path HTTP/version`

```

GET /users/1 HTTP/1.1

```

- Components:
  - **HTTP Method**– what action the client wants to perform
  - **Path (URL)** – the resource being accessed
  - **HTTP Version** – protocol version (HTTP/1.1, HTTP/2)

### HTTP Methods

- HTTP methods describe the intention of the request.

  | Method | Purpose | Description                          |
  | ------ | ------- | ------------------------------------ |
  | GET    | Read    | Retrieve data (no data modification) |
  | POST   | Create  | Create a new resource                |
  | PUT    | Update  | Replace an existing resource         |
  | PATCH  | Update  | Partially update a resource          |
  | DELETE | Delete  | Remove a resource                    |

### HTTP Headers

- Headers provide metadata about the request.

- Common request headers:

| Header        | Description                |
| ------------- | -------------------------- |
| Host          | Target server              |
| Content-Type  | Format of request body     |
| Authorization | Authentication credentials |
| User-Agent    | Client information         |
| Accept        | Expected response format   |

- Example:

```

Content-Type: application/json

```

### Request Body

- The request body contains data sent to the server.

- Used mainly with POST, PUT, PATCH

- Not typically used with GET

- Common body formats: JSON, Form data, XML

- Example (JSON):

```

{
"username": "john",
"password": "secret"
}

```

### Query Parameters

- Query parameters are part of the URL and are used to pass filtering or optional data.
- Start with `?`
- Separated by `&`

Example:

```

GET /users?page=2&limit=10

```

### HTTP Request vs HTTP Response

| HTTP Request              | HTTP Response               |
| ------------------------- | --------------------------- |
| Sent by client            | Sent by server              |
| Asks for an action        | Returns result              |
| Contains method & headers | Contains status code & data |

## Responses HTTP codes

### 1xx — Informational

| Code    | Meaning             |
| ------- | ------------------- |
| **100** | Continue            |
| **101** | Switching Protocols |
| **102** | Processing          |

### 2xx — Success

| Code    | Meaning                       |
| ------- | ----------------------------- |
| **200** | OK                            |
| **201** | Created                       |
| **202** | Accepted                      |
| **203** | Non-Authoritative Information |
| **204** | No Content                    |
| **205** | Reset Content                 |
| **206** | Partial Content               |

### 3xx — Redirection

| Code    | Meaning                    |
| ------- | -------------------------- |
| **300** | Multiple Choices           |
| **301** | Moved Permanently          |
| **302** | Found (Temporary Redirect) |
| **303** | See Other                  |
| **304** | Not Modified               |
| **307** | Temporary Redirect         |
| **308** | Permanent Redirect         |

### 4xx — Client Errors

| Code    | Meaning                |
| ------- | ---------------------- |
| **400** | Bad Request            |
| **401** | Unauthorized           |
| **402** | Payment Required       |
| **403** | Forbidden              |
| **404** | Not Found              |
| **405** | Method Not Allowed     |
| **406** | Not Acceptable         |
| **408** | Request Timeout        |
| **409** | Conflict               |
| **410** | Gone                   |
| **411** | Length Required        |
| **413** | Payload Too Large      |
| **414** | URI Too Long           |
| **415** | Unsupported Media Type |
| **422** | Unprocessable Entity   |
| **429** | Too Many Requests      |

### 5xx — Server Errors

| Code    | Meaning                    |
| ------- | -------------------------- |
| **500** | Internal Server Error      |
| **501** | Not Implemented            |
| **502** | Bad Gateway                |
| **503** | Service Unavailable        |
| **504** | Gateway Timeout            |
| **505** | HTTP Version Not Supported |
| **507** | Insufficient Storage       |
| **508** | Loop Detected              |

## Universally Unique Identifier (UUID)

- Universally Unique Identifier (UUID) is a globally unique identifier used to uniquely identify objects, records, requests, sessions, and more without relying on a central authority to generate IDs.

### What is a UUID?

- A UUID is a 128-bit (16-byte) value, typically represented as a 36-character string (32 hexadecimal characters and 4 hyphens)

```

550e8400-e29b-41d4-a716-446655440000

```

### Why is it called “Universally Unique”?

- Universal: Can be generated anywhere

- Unique: Practically guaranteed not to collide

- Identifier: Used for identification

### UUIDs ideal for

- Distributed systems

- Microservices

- Offline-capable applications

### Common UUID Versions

- UUID v1 – Time-based:
  - Generated using a timestamp and the machine’s MAC address
  - May leak hardware information → less commonly used today
- UUID v4 – Random (most common)
  - Generated randomly
  - Does not reveal system information
  - Very low collision probability
- UUID v5 – Name-based (SHA-1)
  - Deterministic: the same namespace + name always produce the same UUID
  - Useful when you need a consistent, reproducible ID

### How to use

```

import uuid
uuid.uuid4().hex

```

## SQLAlchemy Database URL with Special Characters

- When using SQLAlchemy to connect to a PostgreSQL database, you need to pay attention to how the database URL is constructed. Special characters in the username or password (like `@`, `:`, `/`) can cause connection errors.

### Connection URL Format

- Syntax

```

dialect+driver://username:password@host:port/database

```

- Example

```

postgresql+psycopg2://username:password@localhost:5432/mydatabase

```

### Common Issue with Special Characters

- If your password contains `@`, `:`, or other special characters, a URL like this:

```

postgresql+psycopg2://sonda:Son@22011995@localhost:5432/rest_api_flask_python

# will fail with:

# sqlalchemy.exc.OperationalError: could not translate host name "22011995@localhost" to address

```

- Reason: SQLAlchemy interprets the first @ as the separator between password and host, so the host is parsed incorrectly.

### Solution: URL Encode Special Characters

- Encode special characters in the username or password using percent-encoding.
- Example: `@` → `%40`.

### Encode Password Programmatically in Python

```

from urllib.parse import quote_plus

password = "Son@22011995"
encoded_password = quote_plus(password) # returns 'Son%4022011995'

db_url = f"postgresql+psycopg2://sonda:{encoded_password}@localhost:5432/rest_api_flask_python"

```

# Python Built-in Functions

## Basic I/O & Introspection

| Function       | Meaning               | Syntax                               | Parameters               | Example                       |
| -------------- | --------------------- | ------------------------------------ | ------------------------ | ----------------------------- |
| `print()`      | Print text to console | `print(*objects, sep=' ', end='\n')` | `*objects`, `sep`, `end` | `print("Hello", "World")`     |
| `input()`      | Read user input       | `input(prompt=None)`                 | `prompt`                 | `name = input("Your name: ")` |
| `type()`       | Get object type       | `type(object)`                       | `object`                 | `type(10)`                    |
| `isinstance()` | Check object type     | `isinstance(obj, classinfo)`         | `obj`, `classinfo`       | `isinstance(5, int)`          |
| `id()`         | Get memory address    | `id(object)`                         | `object`                 | `id(x)`                       |
| `dir()`        | List attributes       | `dir([object])`                      | `object` (optional)      | `dir(str)`                    |
| `help()`       | Show documentation    | `help(object)`                       | `object`                 | `help(list)`                  |

## Sequence & Iterable Operations

| Function      | Meaning                                                                                                                                | Syntax                                      | Parameters                                                                                          | Example                                                                                                                          |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `len()`       | Count elements                                                                                                                         | `len(s)`                                    | `s`                                                                                                 | `len([1,2,3])`                                                                                                                   |
| `range()`     | Create integer sequence                                                                                                                | `range(start, stop, step)`                  | `start=0`, `step=1`                                                                                 | `range(1, 5)`                                                                                                                    |
| `enumerate()` | Index + value                                                                                                                          | `enumerate(iterable, start=0)`              | `iterable`, `start`                                                                                 | `enumerate(lst)`                                                                                                                 |
| `zip()`       | Combine iterables                                                                                                                      | `zip(*iterables)`                           | iterables                                                                                           | `zip(a, b)`                                                                                                                      |
| `sorted()`    | Return sorted list                                                                                                                     | `sorted(iterable, key=None, reverse=False)` | `key`, `reverse`                                                                                    | `sorted(nums, reverse=True)`                                                                                                     |
| `reversed()`  | Reverse sequence                                                                                                                       | `reversed(seq)`                             | `seq`                                                                                               | `list(reversed("abc"))`                                                                                                          |
| `next()`      | Retrieves the next item from an iterator. If the iterator is exhausted, it raises `StopIteration`, unless a default value is provided. | `next(iterator, default)`                   | **iterator**: any iterator object **default** (optional): value returned when iterator is exhausted | nums = iter([1, 2, 3]) print(next(nums)) # 1 print(next(nums)) # 2 print(next(nums)) # 3 print(next(nums, 0)) # 0 (default used) |

## Functional Programming Tools

| Function   | Meaning                 | Syntax                   | Parameters          | Example                      |
| ---------- | ----------------------- | ------------------------ | ------------------- | ---------------------------- |
| `map()`    | Apply function to items | `map(func, iterable)`    | `func`, `iterable`  | `map(str, nums)`             |
| `filter()` | Filter by condition     | `filter(func, iterable)` | `func`, `iterable`  | `filter(lambda x: x>5, lst)` |
| `any()`    | True if any True        | `any(iterable)`          | `iterable`          | `any(x>5 for x in nums)`     |
| `all()`    | True if all True        | `all(iterable)`          | `iterable`          | `all(x>0 for x in nums)`     |
| `sum()`    | Sum elements            | `sum(iterable, start=0)` | `iterable`, `start` | `sum([1,2,3])`               |
| `min()`    | Minimum value           | `min(iterable)`          | `iterable`          | `min(nums)`                  |
| `max()`    | Maximum value           | `max(iterable)`          | `iterable`          | `max(nums)`                  |

## Type Conversion

| Function  | Meaning            | Syntax            | Parameters  | Example          |
| --------- | ------------------ | ----------------- | ----------- | ---------------- |
| `int()`   | Convert to int     | `int(x, base=10)` | `x`, `base` | `int("10")`      |
| `float()` | Convert to float   | `float(x)`        | `x`         | `float("3.14")`  |
| `str()`   | Convert to string  | `str(obj)`        | `obj`       | `str(123)`       |
| `bool()`  | Convert to boolean | `bool(x)`         | `x`         | `bool("")`       |
| `list()`  | Convert to list    | `list(iterable)`  | `iterable`  | `list("abc")`    |
| `tuple()` | Convert to tuple   | `tuple(iterable)` | `iterable`  | `tuple([1,2])`   |
| `set()`   | Convert to set     | `set(iterable)`   | `iterable`  | `set([1,1,2])`   |
| `dict()`  | Create dictionary  | `dict(**kwargs)`  | key/value   | `dict(a=1, b=2)` |

## Numeric Helpers

| Function  | Meaning        | Syntax                   | Parameters     | Example             |
| --------- | -------------- | ------------------------ | -------------- | ------------------- |
| `abs()`   | Absolute value | `abs(x)`                 | `x`            | `abs(-5)`           |
| `round()` | Round number   | `round(x, ndigits=None)` | `x`, `ndigits` | `round(3.14159, 2)` |
| `pow()`   | Exponent       | `pow(a, b)`              | `a`, `b`       | `pow(2, 3)`         |

## File & Execution

| Function | Meaning             | Syntax                 | Parameters         | Example                 |
| -------- | ------------------- | ---------------------- | ------------------ | ----------------------- |
| `open()` | Open file           | `open(filename, mode)` | `filename`, `mode` | `open("data.txt", "r")` |
| `eval()` | Evaluate expression | `eval(expr)`           | `expr`             | `eval("1+2")`           |
| `exec()` | Execute code        | `exec(code)`           | `code`             | `exec("x=10")`          |

## OOP Helpers

| Function         | Meaning                | Syntax          | Parameters | Example              |
| ---------------- | ---------------------- | --------------- | ---------- | -------------------- |
| `super()`        | Call parent class      | `super()`       | —          | `super().__init__()` |
| `classmethod()`  | Define class method    | `@classmethod`  | —          | see OOP section      |
| `staticmethod()` | Define static method   | `@staticmethod` | —          | see OOP section      |
| `property()`     | Getter/setter property | `@property`     | —          | property getter      |

## What does in-place mean?

- The operation modifies the original object directly, instead of creating a new one.

```

a = [1, 2, 3]
a.append(4)

```

- The list a is modified directly
- No new list is created
- append() returns None

## List Built-in Functions & Methods

| Function / Method | Syntax               | Description                                         | In-place | Return Value | Example                |
| ----------------- | -------------------- | --------------------------------------------------- | -------- | ------------ | ---------------------- |
| append            | lst.append(x)        | Add an element to the end of the list               | ✅       | None         | a=[1,2]; a.append(3)   |
| extend            | lst.extend(iterable) | Extend list by appending elements from an iterable  | ✅       | None         | a=[1]; a.extend([2,3]) |
| insert            | lst.insert(i, x)     | Insert element at position i                        | ✅       | None         | a=[1,3]; a.insert(1,2) |
| remove            | lst.remove(x)        | Remove first occurrence of value x                  | ✅       | None         | a=[1,2,2]; a.remove(2) |
| pop               | lst.pop([i])         | Remove and return element at index i (default last) | ✅       | element      | a.pop()                |
| clear             | lst.clear()          | Remove all elements from the list                   | ✅       | None         | a.clear()              |
| index             | lst.index(x)         | Return index of first occurrence of x               | ❌       | int          | a.index(2)             |
| count             | lst.count(x)         | Count occurrences of x                              | ❌       | int          | a.count(2)             |
| sort              | lst.sort()           | Sort the list                                       | ✅       | None         | a.sort()               |
| reverse           | lst.reverse()        | Reverse the list in place                           | ✅       | None         | a.reverse()            |
| copy              | lst.copy()           | Return a shallow copy of the list                   | ❌       | list         | b=a.copy()             |
| len               | len(lst)             | Return number of elements                           | ❌       | int          | len(a)                 |
| min / max         | min(lst)             | Return smallest / largest element                   | ❌       | element      | min(a)                 |
| sum               | sum(lst)             | Return sum of numeric elements                      | ❌       | number       | sum(a)                 |

## Dictionary Built-in Functions & Methods

| Function / Method | Syntax              | Description                                 | In-place | Return Value | Example              |
| ----------------- | ------------------- | ------------------------------------------- | -------- | ------------ | -------------------- |
| get               | d.get(k[, default]) | Return value for key k, no error if missing | ❌       | value        | d.get('a', 0)        |
| setdefault        | d.setdefault(k, v)  | Return value; insert key with v if missing  | ✅       | value        | d.setdefault('a', 1) |
| update            | d.update(other)     | Merge another dict into this one            | ✅       | None         | d.update({'a':1})    |
| pop               | d.pop(k)            | Remove key and return its value             | ✅       | value        | d.pop('a')           |
| popitem           | d.popitem()         | Remove and return last key-value pair       | ✅       | (key, value) | d.popitem()          |
| clear             | d.clear()           | Remove all items                            | ✅       | None         | d.clear()            |
| keys              | d.keys()            | Return a view of keys                       | ❌       | view         | d.keys()             |
| values            | d.values()          | Return a view of values                     | ❌       | view         | d.values()           |
| items             | d.items()           | Return a view of key-value pairs            | ❌       | view         | d.items()            |
| copy              | d.copy()            | Return a shallow copy of the dictionary     | ❌       | dict         | d.copy()             |
| len               | len(d)              | Return number of items                      | ❌       | int          | len(d)               |
| in                | k in d              | Check if key exists                         | ❌       | bool         | 'a' in d             |

- Convert List[Dict] to Dict[Dict[id]: Dict]

```
blogs_by_id = {blog["id"]:blog for blog in blogs}
blog = blogs_by_id.get(id)
```

## Merge dictionaries (Python ≥ 3.9)

- This merge creates an entirely new dict object z where we unpack every value from x and y. This way of merging two dictionaries feels unnatural and hardly obvious. If both dictionaries have the same keys, the values of dictionary x are overwritten by the values of dictionary y.

```

x = {"key1": "value1 from x", "key2": "value2 from x"}
y = {"key2": "value2 from y", "key3": "value3 from y"}

z = {**x, **y}
print(z)

# {'key1': 'value1 from x', 'key2': 'value2 from y', 'key3': 'value3 from y'}

```

- If the key already exists, the new value will overwrite the old one.

```

# before merging

x = {"key1": "value1 from x", "key2": "value2 from x"}
y = {"key2": "value2 from y", "key3": "value3 from y"}
print(id(x)) # 2670466407744
print(id(y)) # 2670466407808

# after merging

x | y
print(id(x)) # 2670466407744
print(id(y)) # 2670466407808

# assigning the expression to the variable `z`

z = x | y
print(id(z)) # 2670466542912
print(z is x) # False
print(z is y) # False

```

# Python Libraries

## Flask

- Role: Core web framework

- Main functions
  - Build web applications and REST APIs
  - URL routing (@app.route)
  - Handle HTTP requests and responses
  - Middleware hooks (before_request, after_request)
  - Template rendering (via Jinja2, optional)

## Flask_smorest

- REST API framework + OpenAPI (Swagger) support
- Main functions
  - Build RESTful APIs in Flask
  - Validate request data
  - Serialize response data
  - Generate OpenAPI / Swagger documentation automatically
  - Integrate with **Marshmallow** schemas

## python-dotenv

- Role: Environment variable management

- Main functions
  - Load environment variables from a `.env` file
  - Separate configuration from source code
  - Manage secrets such as database URLs and JWT keys

## Marshmallow

- Role: Serialization, deserialization, and validation library

- Main functions
  - Convert Python objects → JSON-friendly data (serialization)
  - Convert input data (JSON) → Python objects (deserialization)
  - Validate request data using schemas
  - Enforce data types, required fields, and custom validation rules

## SQLAlchemy

- Role: Core ORM and SQL toolkit
- Main functions
  - Object–Relational Mapping (ORM)
  - Map Python classes to database tables
  - Build database queries using Python instead of raw SQL
  - Handle transactions and connection pooling
  - Protect against SQL injection

## psycopg2

- Role: PostgreSQL database driver
- Main functions
  - Enable Python to communicate with PostgreSQL
  - Execute SQL commands at a low level

## PyJWT

- Role: JSON Web Token (JWT) implementation
- Main functions
  - Encode JWT tokens
  - Decode and validate JWT tokens
  - Verify signatures and expiration times

## flask-jwt-extended

- Role: Authentication and authorization using JWT
- Main functions
  - Create access tokens and refresh tokens
  - Protect endpoints with decorators (@jwt_required)
  - Support fresh tokens and refresh tokens
  - Retrieve user identity from JWTs
  - Token revocation and blacklist support

## passlib

- Role: Password hashing and verification
- Main functions
  - Securely hash passwords (bcrypt, PBKDF2, Argon2, etc.)
  - Verify passwords against stored hashes

## flask-migrate

- Role: Database schema migration tool. Built on top of Alembic, designed specifically for Flas
- Main functions
  - Track changes in SQLAlchemy models
  - Generate migration scripts automatically
  - Apply and rollback database schema changes

## Alembic

- Role: Database schema migration engine

- Main functions
  - Manage database schema changes over time
  - Generate migration scripts by comparing models and database state
  - Apply schema upgrades and downgrades
  - Version-control database structure

## Selenium

- Role: Browser automation and web testing tool

- Main functions
  - Automate real browser interactions (Chrome, Firefox, Edge, etc.)
  - Simulate user actions (click, type, scroll, submit forms)
  - Test dynamic web applications (JavaScript-heavy sites)
  - Handle authentication, cookies, sessions
  - Support end-to-end (E2E) testing and web scraping where JS rendering is required

## BeautifulSoup

- Role: HTML and XML parsing library for web scraping

- Main functions
  - Parse HTML/XML documents into a navigable tree
  - Extract data using tags, attributes, CSS selectors
  - Clean and transform raw HTML content
  - Work with static web pages (no JavaScript execution)
  - Integrate with HTTP libraries (e.g., requests) for scraping workflows

## Mailgun

- Role: Transactional email service for sending, receiving, and tracking emails via API or SMTP

- Main functions
  - Send transactional emails (verification, password reset, notifications)
  - Send bulk and marketing emails with high deliverability
  - Receive and route inbound emails via webhooks
  - Email validation (verify email addresses to reduce bounce rate)
  - Track email events (delivered, opened, clicked, bounced, spam complaints)
  - Manage domains, templates, and email logs
  - Integrate via REST API or SMTP with backend applications (Python, Node.js, Java, etc.)

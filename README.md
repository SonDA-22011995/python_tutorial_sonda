- [OOP](#oop)
  - [The `class attributes`](#the-class-attributes)
  - [The `@staticmethod` method](#the-staticmethod-method)
  - [The `@classmethod` method](#the-classmethod-method)
  - [`Is-A` relation](#is-a-relation)
  - [The class composition method `Has-A`](#the-class-composition-method-has-a)
  - [The `__str__` method](#the-__str__-method)
  - [The `__repr__` method](#the-__repr__-method)
- [Other](#other)
  - [Lambda functions](#lambda-functions)
  - [Destructuring](#destructuring)
  - [Format datetime to string](#format-datetime-to-string)
  - [index of the day of the week from a date in Python](#index-of-the-day-of-the-week-from-a-date-in-python)
  - [Add days to a date in Python](#add-days-to-a-date-in-python)
  - [A global variable](#a-global-variable)
  - [Arbitrary Positional Arguments](#arbitrary-positional-arguments)
  - [Mixing Positional and Arbitrary Arguments](#mixing-positional-and-arbitrary-arguments)
  - [Arbitrary Keyword Arguments](#arbitrary-keyword-arguments)
  - [Type hint](#type-hint)
  - [`__name__` variable](#__name__-variable)
  - [Imports](#imports)
  - [Absolute Imports](#absolute-imports)
  - [Relative Imports](#relative-imports)
  - [`__init__` file](#__init__-file)
  - [Errors](#errors)
  - [Custom error classes](#custom-error-classes)
  - [Raise an exception](#raise-an-exception)
  - [Using raise with a custom exception.](#using-raise-with-a-custom-exception)
  - [Re-raising an exception](#re-raising-an-exception)
  - [First-class functions](#first-class-functions)
  - [Python Docstrings - `__doc__` or `help()`](#python-docstrings---__doc__-or-help)
  - [Decorators](#decorators)
  - [Define function Decorators with `functools.wraps`](#define-function-decorators-with-functoolswraps)
  - [Decorators function with parameter](#decorators-function-with-parameter)
  - [Decorators with parameter - A decorator factory](#decorators-with-parameter---a-decorator-factory)
  - [Mutable objects](#mutable-objects)
  - [Immutable objects](#immutable-objects)
  - [Mutable vs. Immutable in Python](#mutable-vs-immutable-in-python)
  - [Don't use mutable defaults parameters](#dont-use-mutable-defaults-parameters)
  - [Argument vs Parameter](#argument-vs-parameter)

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
- **Calling Conventions**: Class methods can be called on the class directly (e.g., `MyClass.my_class_method()`) or on an instance of the class (e.g., `my_instance.my_class_method()`). When called on an instance, the instance's class is automatically passed as the cls argument.
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

print(v1.v_type, v1.name)  # car Toyota
print(v2.v_type, v2.name)  # bike Honda
print(v3.v_type, v3.name)  # truck Volvo

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

print(my_dog.speak())  # Output: Woof!
print(my_cat.speak())  # Output: Meow!
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
        self.model = model
        # Composition: A Car has an Engine object as an attribute
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
- Fallback for **str**: If a class does not define a **str** method, Python will fall back to using **repr** for user-facing string conversions (e.g., when using print())

```
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return f"Point(x={self.x}, y={self.y})"

# Usage
p = Point(10, 20)
print(repr(p))  # Explicitly calls __repr__
print(p)        # Calls __repr__ by default if __str__ is not defined

```

# Other

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
x, y = my_dict.values()  # "Bob", 25
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
name, _, profession = person

print(name, profession)  # Bob Mechanic
```

- Using `*` to Collect Values: In Python, we can use the `*` operator to collect leftover values when performing a destructuring assignment. For example, we might have a list of numbers, and we want to grab the first number, and then assign the remaining numbers to a second variable

```
head, *tail = [1, 2, 3, 4, 5]

print(head)  # 1
print(tail)  # [2, 3, 4, 5]
```

```
*head, tail = [1, 2, 3, 4, 5]

print(head)  # [1, 2, 3, 4]
print(tail)  # 5
```

```
head, *middle, tail = [1, 2, 3, 4, 5]

print(head)    # 1
print(middle)  # [2, 3, 4]
print(tail)    # 5
```

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
    global global_var  # Declare intent to modify the global variable
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
def make_pizza(size, *toppings):
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
def build_profile(first, last, **user_info):
    # Build a dictionary containing everything we know about a user.
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
    def __init__(self, value: int, left: "Node" = None, right: "Node" = None):
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
    def __init__(self, name: str):
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
    def __init__(self, name: str):
        self.name = name

    @classmethod
    def from_fullname(cls: Type[T], fullname: str) -> T:
        first, last = fullname.split()
        return cls(first + " " + last)

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

if __name__ == '__main__':
    # This code will only run when my_module.py is executed directly
    print(greet("World"))
    print(f"This script's __name__ is: {__name__}")
```

If you run python my_module.py, the output will be:

```
Hello, World!
This script's __name__ is: __main__
```

If you import my_module into another script:

```
# another_script.py
import my_module

print(my_module.greet("Python"))
print(f"my_module's __name__ when imported is: {my_module.__name__}")
```

The output will be:

```
Hello, Python!
my_module's __name__ when imported is: my_module
```

## Imports

- The `import` statement is used to bring modules or specific components (functions, classes, variables) from modules into the current namespace, making them available for use. This promotes code reusability and organization

## Absolute Imports

- An absolute path is the full, complete address of a file or directory, starting from the root of the file system

```
my_project/
│
├── app/
│   ├── __init__.py
│   ├── services/
│   │   ├── __init__.py
│   │   └── calculator.py
│   └── utils/
│       ├── __init__.py
│       └── formatter.py
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
- When to use `from .folder_name import module_name`
  - Use `.folder_name` when the module is inside a subfolder of the current folder.

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
    ├── __init__.py
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
    __init__.py
    module1.py
    module2.py
main.py
```

```
# __init__.py
# Define the __all__ variable
__all__ = ["module1", "module2"]

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

## Errors

- Handling Errors
  - `try` block runs code, raising an exception if any occurs
  - `except` block catches exceptions
  - `finally` block always executes
  - `else` Optional Code to execute if no exception occurred in the try block

```
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Code to handle the specific exception
    print("Cannot divide by zero!")
except Exception as e:
    # Catch-all for other exceptions
    print(f"An unexpected error occurred: {e}")
else:
    # Optional: Code to execute if no exception occurred in the try block
    print("No exceptions were raised.")
finally:
    # Optional: Code that always executes, regardless of exception
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
│   ├── ArithmeticError
│   │   ├── FloatingPointError
│   │   ├── OverflowError
│   │   └── ZeroDivisionError
│   │
│   ├── AssertionError
│   ├── AttributeError
│   ├── BufferError
│   ├── EOFError
│   ├── ExceptionGroup
│   ├── ImportError
│   │   └── ModuleNotFoundError
│   │
│   ├── LookupError
│   │   ├── IndexError
│   │   └── KeyError
│   │
│   ├── MemoryError
│   ├── NameError
│   │   └── UnboundLocalError
│   │
│   ├── OSError
│   │   ├── BlockingIOError
│   │   ├── ChildProcessError
│   │   ├── ConnectionError
│   │   │   ├── BrokenPipeError
│   │   │   ├── ConnectionAbortedError
│   │   │   ├── ConnectionRefusedError
│   │   │   └── ConnectionResetError
│   │   │
│   │   ├── FileExistsError
│   │   ├── FileNotFoundError
│   │   ├── InterruptedError
│   │   ├── IsADirectoryError
│   │   ├── NotADirectoryError
│   │   ├── PermissionError
│   │   ├── ProcessLookupError
│   │   ├── TimeoutError
│   │   └── UnsupportedOperation
│   │
│   ├── ReferenceError
│   ├── RuntimeError
│   │   ├── NotImplementedError
│   │   └── RecursionError
│   │
│   ├── StopAsyncIteration
│   ├── StopIteration
│   ├── SyntaxError
│   │   └── IndentationError
│   │       └── TabError
│   │
│   ├── SystemError
│   ├── TypeError
│   ├── ValueError
│   │   ├── UnicodeError
│   │   │   ├── UnicodeDecodeError
│   │   │   ├── UnicodeEncodeError
│   │   │   └── UnicodeTranslateError
│   │   │
│   │   └── UnsupportedOperation (also appears under OSError subclass)
│   │
│   ├── Warning
│   │   ├── UserWarning
│   │   ├── DeprecationWarning
│   │   ├── PendingDeprecationWarning
│   │   ├── SyntaxWarning
│   │   ├── RuntimeWarning
│   │   ├── FutureWarning
│   │   ├── ImportWarning
│   │   ├── UnicodeWarning
│   │   └── ResourceWarning
│   │
│   └── KeyboardInterrupt
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
class MyCustomError(Exception):
    # Exception raised for custom error scenarios.
    # Attributes:
    # message -- explanation of the error

    def __init__(self, message):
        self.message = message
        super().__init__(self.message)
```

```
class MyCustomError(Exception):
    # Exception raised for custom error in the application.

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
try:
    # Some operation that might raise an exception
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"An error occurred: {e}")
    # Re-raises the ZeroDivisionError
    raise
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

print("Using __doc__:")
print(my_function.__doc__)

print("Using help():")
help(my_function)
```

Output

```
Using __doc__:
Demonstrates triple quotes docstring and does nothing.
Using help():
Help on function my_function in module __main__:

my_function()
    Demonstrates triple quotes docstring and does no...
```

## Decorators

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
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@decorator
def say_whee():
    print("Whee!")

print(say_whee.__name__)
# wrapper_do_twice

```

- To fix this, decorators should use the @wraps decorator, which will preserve information about the original function

```
# import functools
from functools import wraps

def do_twice(func):
    # @functools.wraps
    @wraps(func)
    def wrapper_do_twice(*args, **kwargs):
        func(*args, **kwargs)
        return func(*args, **kwargs)
    return wrapper_do_twice

@do_twice
def say_whee():
    print("Whee!")

print(say_whee.__name__)
# say_whee
```

## Decorators function with parameter

- Explanation of Parameters
  - `decorator_name(func)`: This is the decorator function. It takes another function (func) as input.
  - `**wrapper(*args, kwargs)`: A nested function that wraps func. `*args` collects positional arguments, `**kwargs` collects keyword arguments, so wrapper works with any function.
  - `@decorator_name`: Syntax sugar for `add = decorator_name(add)`.

```
def decorator_name(func):
    def wrapper(*args, **kwargs):
        print("Before execution")
        result = func(*args, **kwargs)
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
    def wrapper(*args, **kwargs):
        t = time()
        result = func(*args, **kwargs)
        print(func.__name__, 'took:', time() - t)
        return result
    return wrapper

def max_result(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
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
    return n ** 3

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
        def wrapper(*args, **kwargs):
            result = func(*args, **kwargs)
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
    return n ** 3

print(cube(5))
```

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

## Don't use mutable defaults parameters

## Argument vs Parameter

- In programming, the key difference is that a **parameter** is a **variable** in a function's definition (a placeholder), while an argument is the actual value passed to that function when it is called (the specific data).

| Feature           | Parameter                                                    | Argument                                                        |
| ----------------- | ------------------------------------------------------------ | --------------------------------------------------------------- |
| **Role**          | A placeholder variable in the function definition/signature. | The actual data or value supplied when the function is invoked. |
| **Location**      | Defined in the function header (declaration).                | Provided in the function call statement.                        |
| **Timing**        | Specified at compile-time/definition.                        | Passed at run-time/execution.                                   |
| **Also Known As** | Formal parameter, formal argument.                           | Actual parameter, actual argument.                              |

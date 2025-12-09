- [The `class attributes`](#the-class-attributes)
- [The `@staticmethod` method](#the-staticmethod-method)
- [The `@classmethod` method](#the-classmethod-method)
- [The class composition method](#the-class-composition-method)
- [The `__str__` method](#the-__str__-method)
- [The `__repr__` method](#the-__repr__-method)
- [Lambda functions](#lambda-functions)
- [Destructuring](#destructuring)
- [Format datetime to string](#format-datetime-to-string)
- [index of the day of the week from a date in Python](#index-of-the-day-of-the-week-from-a-date-in-python)
- [Add days to a date in Python](#add-days-to-a-date-in-python)
- [A global variable](#a-global-variable)
- [Arbitrary Positional Arguments](#arbitrary-positional-arguments)
- [Mixing Positional and Arbitrary Arguments](#mixing-positional-and-arbitrary-arguments)
- [Arbitrary Keyword Arguments](#arbitrary-keyword-arguments)

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

## The class composition method

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

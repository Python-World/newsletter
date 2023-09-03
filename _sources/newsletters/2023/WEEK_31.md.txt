# Week 31 - Augest 2023


## 1. 🔢 Python Match Statement

Introduced in Python 3.10, the match statement is a powerful tool for pattern matching. It allows you to simplify complex if-elif-else chains by providing a concise and readable syntax. Here's an example:

```python
def get_day_of_week(day_number):
    match day_number:
        case 1:
            return "Monday"
        case 2:
            return "Tuesday"
        case 3:
            return "Wednesday"
        case 4:
            return "Thursday"
        case 5:
            return "Friday"
        case 6:
            return "Saturday"
        case 7:
            return "Sunday"
        case _:
            return "Invalid day number"
```

The match statement evaluates the input expression (`day_number` in this case) and compares it against different patterns (`case` statements). If a match is found, the corresponding block of code is executed. The `_` represents a wildcard pattern that matches anything.

## 2. 🌪️ Decorators that Take Arguments

Building upon the [previous article](https://python-world.github.io/newsletter/newsletters/2023/WEEK_27.html#unleash-the-power-of-python-function-decorators) on decorators, we can enhance their functionality by allowing them to accept arguments. This provides greater flexibility and customization.

Here's an example:

```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("John")
```

In this example, the `repeat` decorator takes an argument `n` and returns a decorator function. This decorator function, in turn, takes the original function as an argument and returns the modified function (`wrapper`). The modified function is then executed multiple times, as specified by the `repeat` argument.

## 3. 🛫 Map and Filter Functions

Python provides two built-in functions, `map` and `filter`, that are widely used to process iterables.

The `map` function applies a given function to each item in an iterable and returns an iterator with the results. Here's an example:

```python
numbers = [1, 2, 3, 4, 5]

squared_numbers = map(lambda x: x ** 2, numbers)
print(list(squared_numbers))  # Output: [1, 4, 9, 16, 25]
```

The `filter` function applies a given function to each item in an iterable and returns an iterator with the items for which the function returns `True`. Here's an example:

```python
numbers = [1, 2, 3, 4, 5]

even_numbers = filter(lambda x: x % 2 == 0, numbers)
print(list(even_numbers))  # Output: [2, 4]
```

## 4. 🍁 Global and Nonlocal Variables

In Python, the `global` and `nonlocal` keywords allow you to modify variables outside the current scope.

The `global` keyword is used to indicate that a variable within a function should refer to the global variable with the same name. Here's an example:

```python
count = 0

def increment():
    global count
    count += 1

increment()
print(count)  # Output: 1
```

The `nonlocal` keyword is used to indicate that a variable within a nested function should refer to a variable from its outer scope. Here's an example:

```python
def outer():
    x = 1

    def inner():
        nonlocal x
        x += 1
        print(x)

    inner()

outer()  # Output: 2
```

## 5. 🫙 Closures

A closure is a function object that remembers values in its enclosing scope, even if they are not present in memory. This allows the function to access and manipulate variables from the outer function, even after the outer function has finished executing. Here's an example:

```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

add_5 = outer_function(5)
print(add_5(3))  # Output: 8
```

In this example, `outer_function` returns `inner_function`, which remembers the value of `x` even after `outer_function` has completed. The returned `inner_function` can be called later, providing the remembered value `x` and accepting an additional parameter `y` to perform the desired computation.

These are just a few examples of Python's powerful features. Each of these concepts has its own unique applications and can greatly enhance your Python programming skills. Experiment with these concepts and explore their potential to unlock even more possibilities in your projects!


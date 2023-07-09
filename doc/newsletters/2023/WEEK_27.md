
# Week 27 - Jully 2023

## Introduction and Highlights


Welcome to the latest edition of the Python-World Newsletter! We bring
you the most exciting updates and insightful content from the Python
community. In this week’s edition, we have some incredible code
snippets, community spotlights, upcoming events, useful resources, and
more. Let’s dive in!

## Code Snippets




### 1. 🔄  Mastering the 'else' Statement in Looping

In Python, the 'else' statement in loops is often overlooked but can bring some valuable functionality to your code. It allows you to specify a block of code that will execute only if the loop completes normally, without any 'break' statements being encountered.

Here's an example to illustrate its usage:

```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 0:
        break
else:
    print("All numbers processed successfully!")
```

In this code snippet, the 'else' block will execute only if the loop completes without encountering a 'break' statement. It acts as a way to provide additional actions or notifications when the loop finishes its iteration.

**Practical Applications ✨**

The 'else' statement in loops can be handy in various scenarios. Here are a few practical use cases:

1️⃣ **Searching for an item**: You can use a 'for' loop to search for an element in a list and execute specific code in the 'else' block if the item is not found.

2️⃣ **Validating conditions**: If you have a loop that checks multiple conditions, you can use the 'else' block to perform additional checks or execute code when all conditions are satisfied.

3️⃣ **Looping with 'try-except'**: When working with exceptions, you can combine a loop with a 'try-except' statement. In this case, the 'else' block will run if no exceptions are raised within the loop.

Keep in mind that the 'else' block in loops is entirely optional and not mandatory. You can choose to use it when it provides clarity and improves the readability of your code.





### 2. 🌐 Track the history of a request using the "requests.history"

**Understanding Requests History 📜**

The "requests" library is widely used for making HTTP requests in Python. One of its notable features is the ability to track the history of a request using the "requests.history" attribute. This attribute provides access to a list of response objects that contains the entire redirect history of the original request.

**Why is Requests History Useful? 🤔**

1️⃣ **Redirect Tracing**: By accessing the requests history, you can trace the path of your request, including any redirections that occurred. This is particularly helpful when dealing with APIs or web scraping tasks that involve following redirects.

2️⃣ **Error Diagnosis**: If a request encounters an error, examining the history can provide insights into the intermediate steps and the responses received. This can aid in diagnosing and troubleshooting issues during the request lifecycle.

3️⃣ **Verification**: Verifying the request history allows you to ensure that the expected redirections or intermediary responses are occurring correctly. This can be crucial for compliance with specific APIs or handling authentication flows.

**Example Usage 🚀**

Let's look at a simple example to demonstrate how to access the requests history:

```python

import requests

response = requests.get('https://example.com')

if response.history:
    print(f"Request was redirected {len(response.history)} times.")

    for resp in response.history:
        print(f"Redirected to: {resp.url}")
else:
    print("Request was not redirected.")
```

In this code snippet, we make a GET request to "https://example.com". If the request encountered any redirects, we print the number of times it was redirected and display the URLs of the intermediate responses.

**Start Tracing Your Requests! 🔎**

Now that you're aware of the "requests.history" feature, start incorporating it into your projects. It enables you to track the journey of your requests, diagnose errors, and ensure the proper flow of interactions with APIs and websites.


### 3. 🆔 Understanding UUIDs

A UUID, which stands for Universally Unique Identifier, is a 128-bit identifier that ensures uniqueness across all devices and platforms. It provides a reliable way to generate unique identifiers without the need for central coordination. Python offers a built-in module called "uuid" that allows you to work with UUIDs effortlessly.

**Why are UUIDs Useful? 🤔**

1️⃣ **Uniqueness**: UUIDs are designed to be highly unique, reducing the chances of collisions when generating identifiers. This makes them ideal for scenarios where unique identification is essential, such as database records, distributed systems, or data synchronization.

2️⃣ **Global Uniqueness**: UUIDs generated using different machines and at different times will still maintain their uniqueness, making them suitable for distributed systems or scenarios involving multiple devices.

3️⃣ **Persistence**: UUIDs can be serialized and stored in databases or used as identifiers in various contexts. They can be easily converted to strings, making them compatible with different data formats.

**Generating UUIDs in Python 🚀**

The "uuid" module in Python provides several functions to generate different types of UUIDs. Let's take a look at a simple example:

```python

import uuid

# Generate a random UUID
random_uuid = uuid.uuid4()
print("Random UUID:", random_uuid)

# Generate a UUID based on a host ID and current time
time_based_uuid = uuid.uuid1()
print("Time-based UUID:", time_based_uuid)
```

In this code snippet, we use the `uuid.uuid4()` function to generate a random UUID and `uuid.uuid1()` to generate a time-based UUID. You can explore other functions in the "uuid" module to generate UUIDs based on different criteria.

If security is the primary concern in your application, using uuid4 is recommended due to its reliance on cryptographic randomness. However, if high uniqueness is the primary requirement and the potential predictability of MAC addresses is not a concern in your specific use case, uuid1 can still be a viable option.

**Embrace the Power of Uniqueness! 🔐**

By incorporating UUIDs into your Python projects, you can ensure global uniqueness, mitigate the risk of collisions, and simplify identification and data synchronization. The "uuid" module provides the necessary tools to generate and work with UUIDs effortlessly.



### 4. ⚠️ Understanding Errno and Error Handling

In Python, "errno" refers to the system error codes that are provided by the underlying operating system. These codes represent various types of errors encountered during program execution. Python's "errno" module provides a convenient way to access and handle these error codes.

**Why is Error Handling Important? 🤔**

1️⃣ **Graceful Program Flow**: Effective error handling allows your program to gracefully handle unexpected scenarios and prevent crashes or undesirable outcomes. It enables you to anticipate potential issues and take appropriate actions, ensuring a smoother user experience.

2️⃣ **Debugging and Troubleshooting**: Error handling provides valuable insights into the cause of errors and helps with debugging and troubleshooting. By capturing and logging error messages and associated error codes, you can quickly identify the root cause and address the underlying issues.

3️⃣ **Robustness and Resilience**: Proper error handling makes your code more robust and resilient. It allows you to handle exceptions, recover from errors, and implement fallback mechanisms, ensuring that your program continues to run smoothly even in challenging conditions.

**Utilizing "Errno" in Python 🚀**

Let's take a look at an example that demonstrates the usage of "errno" in Python:

```python

import errno

try:
    file = open("nonexistent_file.txt", "r")
except IOError as e:
    if e.errno == errno.ENOENT:
        print("File not found!")
    elif e.errno == errno.EACCES:
        print("Permission denied!")
    else:
        print("An error occurred:", e)
```

In this code snippet, we attempt to open a file that doesn't exist. If an `IOError` exception occurs, we check the associated `errno` attribute to determine the specific error code and provide a customized error message based on the code.

Here are some commonly used `errno` attributes along with their meanings:

    - `errno.EACCES`: Permission denied. Indicates that the operation was not permitted due to insufficient access rights or privileges.

    - `errno.EEXIST`: File or directory already exists. Occurs when attempting to create a file or directory that already exists.

    - `errno.ENOENT`: No such file or directory. Indicates that the specified file or directory does not exist.

    - `errno.EIO`: Input/output error. Indicates an error occurred during an input/output operation, such as reading from or writing to a file.

    - `errno.ERANGE`: Result too large. Occurs when the result of an operation exceeds the maximum representable value.

    - `errno.EAGAIN`: Resource temporarily unavailable. Indicates that a resource required for the operation is temporarily unavailable and the operation should be retried.

    - `errno.EPIPE`: Broken pipe. Occurs when a process tries to write to a pipe that has been closed by the reader.

    - `errno.ENOTEMPTY`: Directory not empty. Indicates that a directory being operated on is not empty and cannot be removed or overwritten.

    - `errno.EINVAL`: Invalid argument. Occurs when an invalid argument is passed to a function or system call.

These are just a few examples of `errno` attributes. Python's `errno` module provides a wide range of error codes that cover various scenarios. You can refer to the Python documentation for a comprehensive list of `errno` attributes and their meanings: https://docs.python.org/3/library/errno.html

Understanding these error codes can help you diagnose and handle specific error conditions in your Python programs more effectively.

**Handle Errors like a Pro! 💪**

By mastering the art of error handling and utilizing the "errno" module, you can ensure your Python programs handle errors gracefully and respond intelligently to unexpected situations. Error handling empowers you to build robust and reliable applications.


### 5. 🐞 Dive into Debugging with PDB

**⚙️ Understanding PDB and its Importance ⚙️**

PDB, the Python Debugger, is an invaluable tool for debugging and troubleshooting Python programs. It allows you to pause the execution of your code, inspect variables, step through statements, and gain insights into the flow of your program. PDB comes in handy when you encounter unexpected behavior, errors, or when you simply want to understand the inner workings of your code.

**Why is PDB Useful? 🤔**

1️⃣ **Precise Bug Identification**: PDB enables you to set breakpoints in your code and examine variables at specific points. This helps identify the exact location of bugs and understand the values that lead to unexpected outcomes.

2️⃣ **Program Flow Exploration**: By stepping through your code, line by line, you gain a deeper understanding of how your program executes. PDB allows you to see the sequence of statements and the values of variables at each step, making it easier to spot errors or inefficiencies.

3️⃣ **Interactive Troubleshooting**: PDB provides an interactive environment within your program, allowing you to experiment with statements, modify variables, and test hypotheses on-the-fly. This interactive approach makes the debugging process more dynamic and efficient.

**Unleash the Power of PDB 🚀**

Let's take a glimpse at how to use PDB in your Python projects:

1. Import the `pdb` module:

```python

import pdb
```

2. Set a breakpoint in your code:

```python

pdb.set_trace()
```

3. Run your program and start debugging!

Once the program hits the breakpoint, you can use PDB's commands to navigate, inspect variables, execute statements, and step through your code.

**Level up Your Debugging Skills! 💪**

By embracing PDB, you unlock a whole new level of debugging proficiency. Understanding PDB's capabilities and integrating it into your development workflow can save you time and frustration when troubleshooting issues.



### 6. 🔥 Unleash the power of Python Function Decorators

In Python, functions are first-class objects, which means they can be passed as arguments to other functions.
This property is known as "higher-order functions" or "first-class functions."

For example, I want to add some logging statements, before and after function execution, and log how much time the function took to execute.

```python
import time


def my_func():
    # dummy function
    print("Executing my function")
    for i in range(3):
        print(1000000*100000*1000000*23456423)
        time.sleep(0.5)

def log_time(func):
    print("Before executing function")
    start = time.time()
    func()
    end = time.time()
    print("Finished function execution")
    print(f"Function exitted in {(end-start):.2f}s")


log_time(my_func)

```

In this above example, you see that `log_time` function executes `my_func`,
but also adds extra functionality.
For external users or other modules of my library,
if I dont want to expose `log_time` and `my_func`,
I can simply, create a new function, calling which would have the same effect
as doing `log_time(my_func)`

```python
def log_time_decorator(func):
    print("Printing from decorator ...")
    def log_time_wrapper():
        print("Printing from wrapper function ...")
        print("Before executing function")
        start = time.time()
        func()
        end = time.time()
        print("Finished function execution")
        print(f"Function exitted in {(end-start):.2f}s")
    return log_time_wrapper
```

- We can see that the `wrapper` function wraps the original function, and adds additional features to it.
- The `decorator` function returns the `wrapper` function.

Now, I can enhance and convert `my_func` to a more powerful function.

```python
print("Creating decorated function ...")
my_func_t = log_time_decorator(my_func)
print("\n\nCalling decorated function ...")
my_func_t()
```

We may choose not to create a seperate `my_func_t` object, and just modify the existing `my_func` function object, by decorating it.

```python
my_func =  log_time_decorator(my_func)
```

The above line has same effect, as using the `@decorator` shortcut in python while defining a function.

```python
@log_time_decorator
def my_func():
    # dummy function
    ...
    # business logic

```

This decorator, can be re-used very easily to enhance any other function, by logging its execution time.

In the newsletter of upcoming weeks, we will go through decorators in much more depth. We will discuss decorators that can take arguments and also class decorators.
We will also discuss about various open source libraries where this decorator patter is commonly used.
Stay tuned.


### 7. ✅ Using `assert` in Python

The usage of `assert` is very simple. You simply write `assert` and then the condition, you want to check.

If the condition you have put, turns out to be true, then the program flow continues as intended. Otherwise the program exits at that point, throwing an assertion error.

You may choose to handle that error, and do something specific, depending on your business logic.

```python
x = 10
assert x == 10
assert x > 0
assert x < 0
```

If you run this piece of code, the first two `assert` statements would pass, but the third would fail.

```shell
Traceback (most recent call last):
  File "/home/aahnik/Projects/Writing/newsletter/test.py", line 4, in <module>
    assert x < 0
           ^^^^^
AssertionError
```

We can also show a custom error message, when this assertion fails.

```python
assert x < 0, "x is not negative"
```

This would output

```shell
AssertionError: x is not negative
```

#### Industry use cases of `assert`

The `assert` statement in Python is a powerful tool that allows programmers to perform runtime assertions in their code. It helps verify assumptions and catch potential bugs during development and testing. While its primary purpose is to validate conditions, `assert` can be used in a variety of real-life scenarios, ranging from simple to advanced applications. In this article, we explore some practical use cases of `assert` in Python.

##### 1. Input Validation

One common use of `assert` is to validate input parameters or function arguments. By using `assert` statements, you can ensure that the provided inputs meet the expected criteria or constraints. Let's consider an example:

```python
def calculate_discount(price, discount):
    assert price > 0, "Price should be greater than 0"
    assert 0 <= discount <= 100, "Discount should be between 0 and 100"

    discounted_price = price - (price * discount / 100)
    return discounted_price
```

In this scenario, the `assert` statements ensure that the `price` is positive and the `discount` is within the valid range. If any of these conditions are not met, an `AssertionError` is raised with a custom error message, providing valuable feedback to the developer.

##### 2. Debugging and Testing

When debugging code or writing test cases, `assert` statements can be incredibly useful. They help to check intermediate values, test assumptions, and ensure that the code is behaving as expected. Let's consider a simple debugging example:

```python
def divide_numbers(a, b):
    assert b != 0, "Division by zero is not allowed"

    result = a / b
    return result

# Debugging
a = 10
b = 0
assert b != 0, "b should not be zero"  # Assertion for debugging
result = divide_numbers(a, b)
print(result)
```

In this case, the `assert` statement is used as a debugging tool to validate the assumption that `b` should not be zero before executing the `divide_numbers` function. If the condition fails, the program halts, and an error message is displayed, aiding in identifying the issue.

##### 3. Program Invariants

Program invariants are conditions that are expected to be true at specific points during the program's execution. Using `assert` statements to check these invariants can help detect logical errors. For instance, consider a banking application where account balances should always be positive:

```python
class BankAccount:
    def __init__(self, balance):
        assert balance >= 0, "Balance should be non-negative"
        self.balance = balance

    def withdraw(self, amount):
        assert amount > 0, "Withdraw amount should be positive"
        assert amount <= self.balance, "Insufficient funds"

        self.balance -= amount
        return self.balance
```

Here, the `assert` statements ensure that the `balance` is non-negative and that the withdrawal amount is both positive and within the available funds. Violating these conditions would indicate a logical error, allowing developers to identify and fix issues early.

##### 4. Unit Testing

In unit testing, `assert` statements are frequently used to verify the correctness of code by comparing expected and actual values. By comparing these values, `assert` statements help validate that functions and classes produce the expected output. Let's look at a simple example:

```python
def add_numbers(a, b):
    return a + b

# Unit Test
result = add_numbers(2, 3)
assert result == 5, f"Expected 5, but got {result}"
```

In this case, the `assert` statement ensures that the `add_numbers` function correctly adds two numbers by comparing the expected result (5) with the actual result. If they don't match, an `AssertionError` is raised, indicating a potential bug or unexpected behavior.

#### Conclusion

The `assert` statement in Python is a versatile tool that serves various purposes in real-life scenarios. From input validation to debugging, testing, enforcing invariants, and unit testing, `assert` statements provide a means to verify conditions and catch potential issues early. By leveraging `assert`, programmers can improve code quality, ensure correct behavior, and reduce the likelihood of bugs in their applications.

Remember that `assert` statements are primarily intended for debugging and testing purposes and can be disabled in a production environment. Therefore, it's crucial to use them judiciously and consider appropriate error handling mechanisms for production code.


### 8. 🌀 Exploiting Parallelism with Python: Multiprocessing vs Multithreading vs Co-routines

When executing code synchronously or sequentially, each task is processed one after the other. This approach can be limiting, especially when dealing with computationally intensive or time-consuming tasks. To overcome this limitation, parallelism comes into play, allowing multiple tasks to be executed simultaneously. In Python, there are three main techniques for exploiting parallelism: Multiprocessing, Multithreading, and Co-routines. In this article, we'll explore these techniques, understand their differences, and determine their best use cases.

#### Synchronous/Sequential Execution

Before diving into parallelism, let's briefly discuss synchronous or sequential execution. In this mode, code is executed line by line, and each task must complete before moving on to the next. This approach works well for simple programs, but it becomes inefficient when dealing with time-consuming operations or tasks that can benefit from concurrent processing.

#### IO-Bound Tasks vs CPU-Bound Tasks

Before we explore parallelism techniques, it's important to understand the distinction between IO-bound and CPU-bound tasks.

- **IO-Bound Tasks**: These tasks spend most of their time waiting for input/output operations to complete. Examples include reading from/writing to files, making network requests, or interacting with a database. IO-bound tasks can benefit from parallelism as they can be scheduled concurrently, utilizing idle time during IO operations.

- **CPU-Bound Tasks**: These tasks heavily rely on the CPU for processing and computation. Examples include complex mathematical calculations, image/video processing, or simulations. CPU-bound tasks can benefit from parallelism by utilizing multiple CPU cores to speed up execution.

#### Multiprocessing for CPU-Bound Tasks

Multiprocessing is a technique that involves running multiple processes simultaneously to achieve parallel execution. Each process has its own memory space, allowing them to execute independently. This technique is well-suited for CPU-bound tasks, as it takes advantage of multiple CPU cores.

```python
import multiprocessing

def process_data(data):
    # Perform CPU-intensive computations
    pass

if __name__ == "__main__":
    data = [...]  # Data to be processed

    # Create a pool of processes
    with multiprocessing.Pool() as pool:
        # Distribute the data across processes
        results = pool.map(process_data, data)
```

By utilizing the `multiprocessing` module, we can spin up multiple processes to distribute CPU-bound tasks across available CPU cores. This allows us to scale the execution speed and improve overall performance.

#### Multithreading for IO-Bound Tasks

Multithreading is a technique where multiple threads of execution run concurrently within a single process. Each thread shares the same memory space, making data sharing easier. While multithreading can provide parallelism, it's not always suitable for CPU-bound tasks due to Python's Global Interpreter Lock (GIL), which prevents true parallelism for CPU-bound tasks. However, it can be used effectively for IO-bound tasks.

```python
import threading

def process_data(data):
    # Perform IO-bound operations
    pass

if __name__ == "__main__":
    data = [...]  # Data to be processed

    # Create multiple threads
    threads = []
    for d in data:
        thread = threading.Thread(target=process_data, args=(d,))
        threads.append(thread)
        thread.start()

    # Wait for all threads to complete
    for thread in threads:
        thread.join()
```

In this example, multiple threads are created to process IO-bound tasks concurrently. Each thread performs its operations independently, taking advantage of idle time during IO operations.

#### Co-routines for Efficient Asynchronous Tasks

Co-routines are lightweight, independent units of execution that can be scheduled and paused during their execution. They allow for efficient concurrency without the overhead associated with operating system threads or processes. Co-routines enable us to exploit parallelism by efficiently handling both IO-bound and CPU-bound tasks.

In Python, co-routines are implemented using the `asyncio` module, which provides an event loop for managing the execution of co-routines.

```python
import asyncio

async def process_data(data):
    # Perform async operations
    pass

if __name__ == "__main__":
    data = [...]  # Data to be processed

    # Create an event loop
    loop = asyncio.get_event_loop()

    # Schedule the execution of co-routines
    tasks = [process_data(d) for d in data]
    loop.run_until_complete(asyncio.gather(*tasks))

    # Close the event loop
    loop.close()
```

Using `asyncio`, we can define co-routines with the `async` keyword, enabling them to be paused and resumed during execution. Co-routines provide a more efficient approach to parallelism, allowing for both IO-bound and CPU-bound tasks to be handled effectively.

#### Simplifying Co-routine Development with `async`/`await`

Python 3.5 introduced the `async` and `await` keywords, simplifying the development of co-routines. `async` is used to define a co-routine, and `await` is used to suspend execution until the awaited operation completes.

`async`/`await` syntax simplifies the handling of asynchronous tasks, making the code more readable and reducing complexity. It allows for straightforward development of highly concurrent and efficient programs.

#### Comparison and Use Cases

To summarize the different techniques:

- Multiprocessing is best suited for CPU-bound tasks that can benefit from parallel execution across multiple CPU cores.
- Multithreading is useful for IO-bound tasks, leveraging concurrent execution to maximize performance during IO operations.
- Co-routines, with the help of `asyncio`, are effective for both IO-bound and CPU-bound tasks, providing efficient concurrency and allowing developers to write highly concurrent code.

When choosing a parallelism technique, consider the nature of the task (IO-bound or CPU-bound) and the specific requirements of your application. Each technique has its strengths and use cases, allowing you to exploit parallelism in Python effectively.

By leveraging parallelism, Python developers can significantly improve the performance and efficiency of their applications, enabling faster execution and better resource utilization.

Remember, each technique has its own considerations and trade-offs, so choose the approach that best suits your specific requirements and use cases. Happy parallel programming in Python!


#### Video Resources

- [Making multiple HTTP requests using Python (synchronous, multiprocessing, multithreading, asyncio)](https://youtu.be/R4Oz8JUuM4s) by [Indian Pythonista](https://www.youtube.com/@IndianPythonista)
- [Python Multiprocessing Tutorial: Run Code in Parallel Using the Multiprocessing Module](https://youtu.be/fKl2JW_qrso) by [Corey Schafer](https://www.youtube.com/@coreyms)
- [Python Threading Tutorial: Run Code Concurrently Using the Threading Module](https://youtu.be/IEEhzQoKtQU) by [Corey Schafer](https://www.youtube.com/@coreyms)


### 9. 🤸 Understanding Python Typing and Type Hints with MyPy and VS Code Support

Python is a dynamically typed language, meaning variables do not require explicit type declarations. However, with the introduction of type hints in Python 3.5 and the support of tools like MyPy and VS Code, developers can now add static type information to their code, enhancing readability, maintainability, and catching potential type-related bugs.

#### Python Typing and Type Hints

Type hints in Python allow developers to provide information about the expected types of variables, function arguments, and return values. While type hints are optional and do not affect the runtime behavior of the code, they serve as documentation and enable static type checking tools to analyze the code for potential type-related errors.

Consider the following example:

```python
def add_numbers(a: int, b: int) -> int:
    return a + b
```

In this code snippet, type hints are used to indicate that both `a` and `b` should be of type `int`, and the function should return an `int`. These type hints provide clarity about the expected types, making the code more self-explanatory and enabling static analysis tools to detect type inconsistencies.

#### MyPy - Static Type Checker for Python

MyPy is a popular static type checker for Python that can analyze code with type hints and detect potential type errors without running the program. It helps catch common mistakes and allows developers to find type-related bugs early in the development process.

Using MyPy is straightforward. After installing it, you can run MyPy on your codebase:

```bash
mypy your_code.py
```

If there are any type errors or inconsistencies in your code, MyPy will provide detailed error messages and suggestions for fixing them. This helps ensure that your code aligns with the specified types, improving code quality and reliability.

#### VS Code Support for Type Hints

Visual Studio Code (VS Code) is a popular code editor with excellent support for Python and type hints. With the help of various extensions, such as the Python extension and the Pyright extension, developers can take advantage of advanced type checking features directly within the editor.

Once you have the necessary extensions installed, VS Code will automatically analyze your code for type errors and provide real-time feedback. It highlights potential type mismatches, missing type hints, and other issues, helping you write more robust and maintainable code.

Additionally, VS Code offers features like autocompletion and hover information based on type hints, enabling you to write code faster and with fewer errors. It improves the development experience and encourages best practices in using type hints.

#### Benefits of Type Hints and Tooling Support

The use of type hints and tools like MyPy and VS Code support offer several advantages:

1. **Improved Readability**: Type hints make code more self-documenting by providing explicit information about the expected types, leading to enhanced code comprehension and maintainability.

2. **Early Bug Detection**: Static type checkers like MyPy can catch potential type errors before the code is executed, reducing the chances of runtime errors and improving overall code quality.

3. **Enhanced Tooling**: IDEs and code editors, such as VS Code, leverage type hints to provide better autocompletion, code navigation, and error checking, leading to a more efficient and error-free development experience.

4. **Collaboration and Documentation**: Type hints serve as documentation for developers, making it easier to understand and collaborate on codebases. They can also generate API documentation automatically, providing clear guidance for users of your code.

#### Embrace the Power of Type Hints

Type hints and the associated tooling support, such as MyPy and VS Code, offer powerful ways to enhance your Python code. By providing static type information, you can improve code quality, catch bugs early, and enjoy a more productive development experience. Embrace type hints and the available tooling to write more robust and maintainable Python code.



#### Resources

- [Python Types Intro](https://fastapi.tiangolo.com/python-types/) from [FastAPI docs](https://fastapi.tiangolo.com/)


### 10. 🗄️ Python Persistence: Pickling and SQLite

Python provides several mechanisms for data persistence, allowing you to store and retrieve data across different program executions. Two commonly used methods for persistence are pickling and SQLite. Let's explore these techniques briefly.

#### Pickling

Pickling is a Python-specific way of serializing and deserializing Python objects. It allows you to convert complex objects into a byte stream that can be stored in a file or transferred over a network. The `pickle` module in Python provides the necessary functions for pickling and unpickling objects.

To persist data using pickling, you can use the following code:

```python
import pickle

# Data to be pickled
data = [1, 2, 3, 4, 5]

# Pickle the data to a file
with open('data.pickle', 'wb') as file:
    pickle.dump(data, file)

# Unpickle the data from the file
with open('data.pickle', 'rb') as file:
    unpickled_data = pickle.load(file)
```

Here, the `pickle.dump()` function is used to pickle the `data` list and store it in a file named `data.pickle`. The `pickle.load()` function is then used to retrieve the pickled data from the file and store it in the `unpickled_data` variable.

Pickling is a convenient way to store and retrieve Python objects, but it's important to note that it can have security implications if used with untrusted data. Therefore, it's recommended to use pickling only in trusted environments.

#### SQLite

SQLite is a lightweight and embedded relational database engine that is widely used in Python applications. It provides a simple and efficient way to store and query structured data without requiring a separate database server. Python includes the `sqlite3` module, which allows seamless interaction with SQLite databases.

To use SQLite for data persistence, you can use the following code:

```python
import sqlite3

# Connect to the database
conn = sqlite3.connect('database.db')

# Create a cursor object
cursor = conn.cursor()

# Create a table
cursor.execute('CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)')

# Insert data into the table
cursor.execute('INSERT INTO users (name, age) VALUES (?, ?)', ('Alice', 25))

# Retrieve data from the table
cursor.execute('SELECT * FROM users')
data = cursor.fetchall()

# Commit the changes
conn.commit()

# Close the connection
conn.close()
```

In this code, we first connect to the SQLite database file named `database.db`. We then create a cursor object to execute SQL statements. The code demonstrates creating a table, inserting data, and retrieving data from the table. Finally, we commit the changes and close the connection to the database.

SQLite provides a SQL-based interface, making it easy to work with structured data. It supports a wide range of SQL operations, including creating tables, inserting data, querying, and more. It's a reliable and efficient choice for many small to medium-sized applications.

#### Choosing the Right Persistence Method

When deciding between pickling and SQLite for data persistence, consider the nature of your data and the requirements of your application. Pickling is suitable for storing and retrieving Python objects with their full state intact, while SQLite is better suited for structured data and complex querying needs.

If you need to store and retrieve complex Python objects without the need for advanced querying capabilities, pickling can be a straightforward and efficient solution. On the other hand, if you require structured data storage and advanced querying capabilities, SQLite offers a more robust solution.

Pickling and SQLite are just two of the many options available for data persistence in Python. Depending on your specific needs, you may explore other alternatives, such as using file systems, NoSQL databases, or ORM frameworks.

Remember to evaluate the trade-offs of each persistence method, considering factors like performance, scalability, security, and the complexity of your data model. By choosing the right persistence technique, you can ensure that your data is stored effectively and can be retrieved efficiently in your Python applications.


## Upcoming Events


| Event Name       | Date    | Location  | URL                       |
|------------------|---------|-----------|---------------------------|
| PyCon 2023       | Sept 29 To Oct 2 | HYDRABAD  | [Website](https://in.pycon.org/2023/) |


Stay updated with the latest events and conferences in the Python
community. Mark your calendars and don’t miss out on these exciting
opportunities to learn, network, and engage with fellow Python
enthusiasts!



Contact
-------

Sure! Here's the text formatted in proper Markdown format:

If you have any questions or need further assistance, feel free to reach out to us at [pythonworldhelp@gmail.com](mailto:pythonworldhelp@gmail.com) or join the discussion on our [GitHub Discussions](https://github.com/Python-World/newsletter/discussions) board.


## Contributors


We would like to express our sincere gratitude to the following
contributors who have made valuable contributions to this edition of the
Python-World Newsletter:

- [Ravishankar Chavare](https://github.com/chavarera/)
- [Aahnik Daw](https://github.com/aahnik/)


Thank you for your dedication and for enriching the Python community
with your valuable insights, code snippets, and contributions! Happy
coding! 🐍✨

# 100 Core Python Interview Questions

<div>
<p align="center">
<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>

#### You can also find all 100 answers here 👉 [Devinterview.io - Python](https://devinterview.io/questions/web-and-mobile-development/python-interview-questions)

<br>

## 1. What are the _key features_ of _Python_?

**Python** is a versatile and popular programming language known for its simplicity, **elegant syntax**, and a vast ecosystem of libraries. Let's look at some of the key features that make Python stand out.

### Key Features of Python

#### 1. Interpreted and Interactive

Python uses an interpreter, allowing developers to run code **line-by-line**, making it ideal for rapid prototyping and debugging.

#### 2. Easy to Learn and Read

Python's **clean, readable syntax**, often resembling plain English, reduces the cognitive load for beginners and experienced developers alike.

#### 3. Cross-Platform Compatibility

Python is versatile, running on various platforms, such as Windows, Linux, and macOS, without requiring platform-specific modifications.

#### 4. Modular and Scalable

Developers can organize their code into modular packages and reusabale functions.

#### 5. Rich Library Ecosystem

The Python Package Index (PyPI) hosts over 260,000 libraries, providing solutions for tasks ranging from web development to data analytics.

#### 6. Exceptionally Versatile

From web applications to scientific computing, Python is equally proficient in diverse domains.

#### 7. Memory Management

Python seamlessly allocates and manages memory, shielding developers from low-level tasks, such as memory deallocation.

#### 8. Dynamically Typed

Python infers the data type of a variable during execution, easing the declartion and manipulation of variables.

#### 9. Object-Oriented

Python supports object-oriented paradigms, where everything is an **object**, offering attributes and methods to manipulate data.

#### 10. Extensible

With its C-language API, developers can integrate performance-critical tasks and existing C modules with Python.
<br>

## 2. How is _Python_ executed?

**Python** source code is processed through various steps before it can be executed. Let's explore the key stages in this process.

### Compilation & Interpretation

Python code goes through both **compilation** and **interpretation**. 

- **Bytecode Compilation**: High-level Python code is transformed into low-level bytecode by the Python interpreter with the help of a compiler. Bytecode is a set of instructions that Python's virtual machine (PVM) can understand and execute.
  
- **On-the-fly Interpretation**: The PVM reads and executes bytecode instructions in a step-by-step manner.
  
This dual approach known as "compile and then interpret" is what sets Python (and certain other languages) apart. 

### Bytecode versus Machine Code Execution

While some programming languages compile directly to machine code, Python compiles to bytecode. This bytecode is then executed by the Python virtual machine. This extra step of bytecode execution **can make Python slower** in certain use-cases when compared to languages that compile directly to machine code.

The advantage, however, is that bytecode is platform-independent. A Python program can be run on any machine with a compatible PVM, ensuring cross-platform support.

### Source Code to Bytecode: Compilation Steps

1. **Lexical Analysis**: The source code is broken down into tokens, identifying characters and symbols for Python to understand.
2. **Syntax Parsing**: Tokens are structured into a parse tree to establish the code's syntax and grammar.
3. **Semantic Analysis**: Code is analyzed for its meaning and context, ensuring it's logically sound.
4. **Bytecode Generation**: Based on the previous steps, bytecode instructions are created.

### Just-In-Time (JIT) Compilation

While Python typically uses a combination of interpretation and compilation, **JIT** boosts efficiency by selectively compiling parts of the program that are frequently used or could benefit from optimization.

JIT compiles sections of the program to machine code on-the-fly. This direct machine code generation for frequently executed parts can significantly speed up those segments, blurring the line between traditional interpreters and compilers.

### Code Example: Disassembly of Bytecode

```python
import dis

def example_func():
    return 15 * 20

# Disassemble to view bytecode instructions
dis.dis(example_func)
```

Disassembling code using Python's `dis` module can reveal the underlying bytecode instructions that the PVM executes. Here's the disassembled output for the above code:

```plaintext
  4           0 LOAD_CONST               2 (300)
              2 RETURN_VALUE
```
<br>

## 3. What is _PEP 8_ and why is it important?

**PEP 8** is a style guide for Python code that promotes code consistency, readability, and maintainability. It's named after Python Enhancement Proposal (PEP), the mechanism used to propose and standardize changes to the Python language.

PEP 8 is not a set-in-stone rule book, but it provides general guidelines that help developers across the Python community write code that's visually consistent and thus easier to understand.

### Key Design Principles

PEP 8 emphasizes:

- **Readability**: Code should be easy to read and understand, even by someone who didn't write it.
- **Consistency**: Codebase should adhere to a predictable style so there's little cognitive load in reading or making changes.
- **One Way to Do It**: Instead of offering multiple ways to write the same construct, PEP 8 advocates for a single, idiomatic style.

### Base Rules

- **Indentation**: Use 4 spaces for each level of logical indentation.
- **Line Length**: Keep lines of code limited to 79 characters. This number is a guideline; longer lines are acceptable in certain contexts.
- **Blank Lines**: Use them to separate logical sections but not excessively.

### Naming Styles

- **Class Names**: Prefer `CamelCase`.
- **Function and Variable Names**: Use `lowercase_with_underscores`.
- **Module Names**: Keep them short and in `lowercase`.

### Documentation

- Use triple quotes for documentation strings.
- Comments should be on their own line and explain the reason for the following code block.

### Whitespace Usage

- **Operators**: Surround them with a single space.
- **Commas**: Follow them with a space.

### Example: Directory Walker

Here is the `PEP8` compliant code:

```python
import os

def walk_directory(path):
    for dirpath, dirnames, filenames in os.walk(path):
        for filename in filenames:
            file_path = os.path.join(dirpath, filename)
            print(file_path)

walk_directory('/path/to/directory')
```
<br>

## 4. How is memory allocation and garbage collection handled in _Python_?

In Python, **both memory allocation** and **garbage collection** are handled discretely.

### Memory Allocation

- The "heap" is the pool of memory for storing objects. The Python memory manager allocates and deallocates this space as needed.

- In latest Python versions, the `obmalloc` system is responsible for small object allocations. This system preallocates small and medium-sized memory blocks to manage frequently created small objects.

- The `allocator` abstracts the system-level memory management, employing memory management libraries like `Glibc` to interact with the operating system.

- Larger blocks of memory are primarily obtained directly from the operating system.

- **Stack** and **Heap** separation is joined by "Pool Allocator" for internal use.

### Garbage Collection

Python employs a method called **reference counting** along with a **cycle-detecting garbage collector**.

#### Reference Counting

- Every object has a reference count. When an object's count drops to zero, it is immediately deallocated.

- This mechanism is swift, often releasing objects instantly without the need for garbage collection.

- However, it can be insufficient in handling **circular references**.

#### Cycle-Detecting Garbage Collector

- Python has a separate garbage collector that periodically identifies and deals with circular references.

- This is, however, a more time-consuming process and is invoked less frequently than reference counting.

### Memory Management in Python vs. C

Python handles memory management quite differently from languages like C or C++:

- In Python, the developer isn't directly responsible for memory allocations or deallocations, reducing the likelihood of memory-related bugs.

- The memory manager in Python is what's known as a **"general-purpose memory manager"** that can be slower than the dedicated memory managers of C or C++ in certain contexts.

- Python, especially due to the existence of a garbage collector, might have memory overhead compared to C or C++ where manual memory management often results in minimal overhead is one of the factors that might contribute to Python's sometimes slower performance.

- The level of memory efficiency isn't as high as that of C or C++. This is because Python is designed to be convenient and easy to use, often at the expense of some performance optimization.
<br>

## 5. What are the _built-in data types_ in _Python_?

Python offers numerous **built-in data types** that provide varying functionalities and utilities.

### Immutable Data Types

#### 1. int
   Represents a whole number, such as 42 or -10.

#### 2. float
   Represents a decimal number, like 3.14 or -0.01.

#### 3. complex
   Comprises a real and an imaginary part, like 3 + 4j.

#### 4. bool
   Represents a boolean value, True or False.

#### 5. str
   A sequence of unicode characters enclosed within quotes.

#### 6. tuple
   An ordered collection of items, often heterogeneous, enclosed within parentheses.

#### 7. frozenset
   A set of unique, immutable objects, similar to sets, enclosed within curly braces.

#### 8. bytes
   Represents a group of 8-bit bytes, often used with binary data, enclosed within brackets.

#### 9. bytearray
   Resembles the 'bytes' type but allows mutable changes.

#### 10. NoneType
   Indicates the absence of a value.

### Mutable Data Types

#### 1. list
   A versatile ordered collection that can contain different data types and offers dynamic sizing, enclosed within square brackets.

#### 2. set
   Represents a unique set of objects and is characterized by curly braces.

#### 3. dict
   A versatile key-value paired collection enclosed within braces.

#### 4. memoryview
   Points to the memory used by another object, aiding efficient viewing and manipulation of data.

#### 5. array
   Offers storage for a specified type of data, similar to lists but with dedicated built-in functionalities.

#### 6. deque
   A double-ended queue distinguished by optimized insertion and removal operations from both its ends.

#### 7. object
   The base object from which all classes inherit.

#### 8. types.SimpleNamespace
   Grants the capability to assign attributes to it.

#### 9. types.ModuleType
   Represents a module body containing attributes.

#### 10. types.FunctionType
   Defines a particular kind of function.
<br>

## 6. Explain the difference between a _mutable_ and _immutable_ object.

Let's look at the difference between **mutable** and **immutable** objects.

### Key Distinctions

- **Mutable Objects**: Can be modified after creation.
- **Immutable Objects**: Cannot be modified after creation.

### Common Examples

- **Mutable**: Lists, Sets, Dictionaries
- **Immutable**: Tuples, Strings, Numbers

### Code Example: Immutability in Python

Here is the Python code:

```python
# Immutable objects (int, str, tuple)
num = 42
text = "Hello, World!"
my_tuple = (1, 2, 3)

# Trying to modify will raise an error
try:
    num += 10
    text[0] = 'M'  # This will raise a TypeError
    my_tuple[0] = 100  # This will also raise a TypeError
except TypeError as e:
    print(f"Error: {e}")

# Mutable objects (list, set, dict)
my_list = [1, 2, 3]
my_dict = {'a': 1, 'b': 2}

# Can be modified without issues
my_list.append(4)
del my_dict['a']

# Checking the changes
print(my_list)  # Output: [1, 2, 3, 4]
print(my_dict)  # Output: {'b': 2}
```

### Benefits & Trade-Offs

**Immutability** offers benefits such as **safety** in concurrent environments and facilitating **predictable behavior**.

**Mutability**, on the other hand, often improves **performance** by avoiding copy overhead and redundant computations.

### Impact on Operations

- **Reading and Writing**: Immutable objects typically favor **reading** over **writing**, promoting a more straightforward and predictable code flow.  

- **Memory and Performance**: Mutability can be more efficient in terms of memory usage and performance, especially concerning large datasets, thanks to in-place updates.

Choosing between the two depends on the program's needs, such as the required data integrity and the trade-offs between predictability and performance.
<br>

## 7. How do you _handle exceptions_ in _Python_?

**Exception handling** is a fundamental aspect of Python, and it safeguards your code against unexpected errors or conditions. Key components of exception handling in Python include:

### Components

- **Try**: The section of code where exceptions might occur is placed within a `try` block.

- **Except**: Any possible exceptions that are `raised` by the `try` block are caught and handled in the `except` block.

- **Finally**: This block ensures a piece of code always executes, regardless of whether an exception occurred. It's commonly used for cleanup operations, such as closing files or database connections.

### Generic Exception Handling vs. Handling Specific Exceptions

It's good practice to **handle** specific exceptions. However, a more **general** approach can also be taken. When doing the latter, ensure the general exception handling is at the end of the chain, as shown here:

```python
try:
    risky_operation()
except IndexError:  # Handle specific exception types first.
    handle_index_error()
except Exception as e:  # More general exception must come last.
    handle_generic_error()
finally:
    cleanup()
```

### Raising Exceptions

Use this mechanism to **trigger and manage** exceptions under specific circumstances. This can be particularly useful when building custom classes or functions where specific conditions should be met.

**Raise** a specific exception:

```python
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Divisor cannot be zero")
    return a / b

try:
    result = divide(4, 0)
except ZeroDivisionError as e:
    print(e)
```

**Raise a general exception**:

```python
def some_risky_operation():
    if condition: 
        raise Exception("Some generic error occurred")
```

### Using `with` for Resource Management

The `with` keyword provides a more efficient and clean way to handle resources, like files, ensuring their proper closure when operations are complete or in case of any exceptions. The resource should implement a `context manager`, typically by having `__enter__` and `__exit__` methods.

Here's an example using a file:

```python
with open("example.txt", "r") as file:
    data = file.read()
# File is automatically closed when the block is exited.
```

### Silence with `pass`, `continue`, or `else`

There are times when not raising an exception is appropriate. You can use `pass` or `continue` in an exception block when you want to essentially ignore an exception and proceed with the rest of your code.

- **`pass`**: Simply does nothing. It acts as a placeholder.

  ```python
  try:
      risky_operation()
  except SomeSpecificException:
      pass
  ```

- **`continue`**: This keyword is generally used in loops. It moves to the next iteration without executing the code that follows it within the block.

  ```python
  for item in my_list:
      try:
          perform_something(item)
      except ExceptionType:
          continue
      ```

- **`else` with `try-except` blocks**: The `else` block after a `try-except` block will only be executed if no exceptions are raised within the `try` block

  ```python
  try:
      some_function()
  except SpecificException:
      handle_specific_exception()
  else:
      no_exception_raised()
  ```

### Callback Function: `ExceptionHook`

Python 3 introduced the better handling of uncaught exceptions by providing an optional function for printing stack traces. The `sys.excepthook` can be set to match any exception in the module as long as it has a `hook` attribute.

Here's an example for this test module:

```python
# test.py
import sys

def excepthook(type, value, traceback):
    print("Unhandled exception:", type, value)
    # Call the default exception hook
    sys.__excepthook__(type, value, traceback)

sys.excepthook = excepthook

def test_exception_hook():
    throw_some_exception()
```

When run, calling `test_exception_hook` will print "Unhandled exception: ..."

_Note_: `sys.excepthook` will not capture exceptions raised as the result of interactive prompt commands, such as SyntaxError or KeyboardInterrupt.
<br>

## 8. What is the difference between _list_ and _tuple_?

**Lists** and **Tuples** in Python share many similarities, such as being sequences and supporting indexing.

However, these data structures differ in key ways:

### Key Distinctions

- **Mutability**: Lists are mutable, allowing you to add, remove, or modify elements after creation. Tuples, once created, are immutable.

- **Performance**: Lists are generally slower than tuples, most apparent in tasks like iteration and function calls.

- **Syntax**: Lists are defined with square brackets `[]`, whereas tuples use parentheses `()`.

### When to Use Each

- **Lists** are ideal for collections that may change in size and content. They are the preferred choice for storing data elements.

- **Tuples**, due to their immutability and enhanced performance, are a good choice for representing fixed sets of related data.

### Syntax

#### List: Example

```python
my_list = ["apple", "banana", "cherry"]
my_list.append("date")
my_list[1] = "blackberry"
```

#### Tuple: Example

```python
my_tuple = (1, 2, 3, 4)
# Unpacking a tuple
a, b, c, d = my_tuple
```
<br>

## 9. How do you create a _dictionary_ in _Python_?

**Python dictionaries** are versatile data structures, offering key-based access for rapid lookups. Let's explore various data within dictionaries and techniques to create and manipulate them.

### Key Concepts

- A **dictionary** in Python contains a collection of `key:value` pairs.
- **Keys** must be unique and are typically immutable, such as strings, numbers, or tuples.
- **Values** can be of any type, and they can be duplicated.

### Creating a Dictionary

You can use several methods to create a dictionary:

1. **Literal Definition**: Define key-value pairs within curly braces { }.

2. **From Key-Value Pairs**: Use the `dict()` constructor or the `{key: value}` shorthand.

3. **Using the `dict()` Constructor**: This can accept another dictionary, a sequence of key-value pairs, or named arguments.

4. **Comprehensions**: This is a concise way to create dictionaries using a single line of code.

5. **`zip()` Function**: This creates a dictionary by zipping two lists, where the first list corresponds to the keys, and the second to the values.

### Examples

#### Dictionary Literal Definition

Here is a Python code:

```python
# Dictionary literal definition
student = {
    "name": "John Doe",
    "age": 21,
    "courses": ["Math", "Physics"]
}
```

#### From Key-Value Pairs

Here is the Python code:

```python
# Using the `dict()` constructor
student_dict = dict([
    ("name", "John Doe"),
    ("age", 21),
    ("courses", ["Math", "Physics"])
])

# Using the shorthand syntax
student_dict_short = {
    "name": "John Doe",
    "age": 21,
    "courses": ["Math", "Physics"]
}
```

#### Using `zip()`

Here is a Python code:

```python
keys = ["a", "b", "c"]
values = [1, 2, 3]

zipped = zip(keys, values)
dict_from_zip = dict(zipped) # Result: {"a": 1, "b": 2, "c": 3}
```

#### Using `dict()` Constructor

Here is a Python code:

```python
# Sequence of key-value pairs
student_dict2 = dict(name="Jane Doe", age=22, courses=["Biology", "Chemistry"])

# From another dictionary
student_dict_combined = dict(student, **student_dict2)
```
<br>

## 10. What is the difference between _==_ and _is operator_ in _Python_?

Both the **`==`** and **`is`** operators in Python are used for comparison, but they function differently.

-  The **`==`** operator checks for **value equality**.
- The **`is`** operator, on the other hand, validates **object identity**,

In Python, every object is unique, identifiable by its memory address. The **`is`** operator uses this memory address to check if two objects are the same, indicating they both point to the exact same instance in memory.

- **`is`**: Compares the memory address or identity of two objects.
- **`==`**: Compares the content or value of two objects.

While **`is`** is primarily used for **None** checks, it's generally advisable to use **`==`** for most other comparisons.

### Tips for Using Operators

- **`==`**: Use for equality comparisons, like when comparing numeric or string values.
- **`is`**: Use for comparing membership or when dealing with singletons like **None**.
<br>

## 11. How does a _Python function_ work?

**Python functions** are the building blocks of code organization, often serving predefined tasks within modules and scripts. They enable reusability, modularity, and encapsulation.

### Key Components

- **Function Signature**: Denoted by the `def` keyword, it includes the function name, parameters, and an optional return type.
- **Function Body**: This section carries the core logic, often comprising conditional checks, loops, and method invocations.
- **Return Statement**: The function's output is determined by this statement. When None is specified, the function returns by default.
- **Local Variables**: These variables are scoped to the function and are only accessible within it.

### Execution Process

When a function is called:

1. **Stack Allocation**: A stack frame, also known as an activation record, is created to manage the function's execution. This frame contains details like the function's parameters, local variables, and **instruction pointer**.
  
2. **Parameter Binding**: The arguments passed during the function call are bound to the respective parameters defined in the function header.

3. **Function Execution**: Control is transferred to the function body. The statements in the body are executed in a sequential manner until the function hits a return statement or the end of the function body.

4. **Return**: If a return statement is encountered, the function evaluates the expression following the `return` and hands the value back to the caller. The stack frame of the function is then popped from the call stack.

5. **Post Execution**: If there's no `return` statement, or if the function ends without evaluating any return statement, `None` is implicitly returned.

### Local Variable Scope

- **Function Parameters**: These are a precursor to local variables and are instantiated with the values passed during function invocation.
- **Local Variables**: Created using an assignment statement inside the function and cease to exist when the function execution ends.
- **Nested Scopes**: In functions within functions (closures), non-local variables - those defined in the enclosing function - are accessible but not modifiable by the inner function, without using the `nonlocal` keyword.

### Global Visibility

If a variable is not defined within a function, the Python runtime will look for it in the global scope. This behavior enables functions to access and even modify global variables.

### Avoiding Side Effects

Functions offer a level of encapsulation, potentially reducing side effects by ensuring that data and variables are managed within a controlled environment. Such containment can help enhance the robustness and predictability of a codebase. As a best practice, minimizing the reliance on global variables can lead to more maintainable, reusable, and testable code.
<br>

## 12. What is a _lambda function_, and where would you use it?

A **Lambda function**, or **lambda**, for short, is a small anonymous function defined using the `lambda` keyword in Python.

While you can certainly use named functions when you need a function for something in Python, there are places where a lambda expression is more suitable.

### Distinctive Features

- **Anonymity**: Lambdas are not given a name in the traditional sense, making them suited for one-off uses in your codebase.
- **Single Expression Body**: Their body is limited to a single expression. This can be an advantage for brevity but a restriction for larger, more complex functions.
- **Implicit Return**: There's no need for an explicit `return` statement.
- **Conciseness**: Lambdas streamline the definition of straightforward functions.

### Common Use Cases

- **Map, Filter, and Reduce**: Functions like `map` can take a lambda as a parameter, allowing you to define simple transformations on the fly. For example, doubling each element of a list can be achieved with `list(map(lambda x: x*2, my_list))`.
- **List Comprehensions**: They are a more Pythonic way of running the same `map` or `filter` operations, often seen as an alternative to lambdas and `map`.
- **Sorting**: Lambdas can serve as a custom key function, offering flexibility in sort orders.
- **Callbacks**: Often used in events where a function is needed to be executed when an action occurs (e.g., button click).
- **Simple Functions**: For functions that are so basic that giving them a name, especially in more procedural code, would be overkill.

### Notable Limitations

- **Lack of Verbose Readability**: Named functions are generally preferred when their intended use is obvious from the name. Lambdas can make code harder to understand if they're complex or not used in a recognizable pattern.
- **No Formal Documentation**: While the function's purpose should be apparent from its content, a named function makes it easier to provide direct documentation. Lambdas would need a separate verbal explanation, typically in the code or comments.
<br>

## 13. Explain _*args_ and _**kwargs_ in _Python_.

In Python, `*args` and `**kwargs` are often used to pass a variable number of arguments to a function. 

`*args` collects a variable number of positional arguments into a **tuple**, while `**kwargs` does the same for keyword arguments into a **dictionary**.

Here are the key features, use-cases, and their respective code examples.

### **\*args**: Variable Number of Positional Arguments

- **How it Works**: The name `*args` is a convention. The asterisk (*) tells Python to put any remaining positional arguments it receives into a tuple.

- **Use-Case**: When the number of arguments needed is uncertain.

#### Code Example: "*args"

```python
def sum_all(*args):
    result = 0
    for num in args:
        result += num
    return result

print(sum_all(1, 2, 3, 4))  # Output: 10
```

### **\*\*kwargs**: Variable Number of Keyword Arguments

- **How it Works**: The double asterisk (**) is used to capture keyword arguments and their values into a dictionary.

- **Use-Case**: When a function should accept an arbitrary number of keyword arguments.

#### Code Example: "**kwargs"

```python
def print_values(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Keyword arguments are captured as a dictionary
print_values(name="John", age=30, city="New York")
# Output:
# name: John
# age: 30
# city: New York
```
<br>

## 14. What are _decorators_ in _Python_?

In Python, a **decorator** is a design pattern and a feature that allows you to modify functions and methods dynamically. This is done primarily to keep the code clean, maintainable, and DRY (Don't Repeat Yourself).

### How Decorators Work

- Decorators wrap a target function, allowing you to execute custom code before and after that function.
- They are typically **higher-order functions** that take a function as an argument and return a new function.
- This paradigm of "functions that modify functions" is often referred to as **metaprogramming**.

### Common Use Cases

- **Authorization and Authentication**: Control user access.
- **Logging**: Record function calls and their parameters.
- **Caching**: Store previous function results for quick access.
- **Validation**: Verify input parameters or function output.
- **Task Scheduling**: Execute a function at a specific time or on an event.
- **Counting and Profiling**: Keep track of the number of function calls and their execution time.

### Using Decorators in Code

Here is the Python code:

```python
from functools import wraps

# 1. Basic Decorator
def my_decorator(func):
    @wraps(func)  # Ensures the original function's metadata is preserved
    def wrapper(*args, **kwargs):
        print('Something is happening before the function is called.')
        result = func(*args, **kwargs)
        print('Something is happening after the function is called.')
        return result
    return wrapper

@my_decorator
def say_hello():
    print('Hello!')

say_hello()

# 2. Decorators with Arguments
def decorator_with_args(arg1, arg2):
    def actual_decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            print(f'Arguments passed to decorator: {arg1}, {arg2}')
            result = func(*args, **kwargs)
            return result
        return wrapper
    return actual_decorator

@decorator_with_args('arg1', 'arg2')
def my_function():
    print('I am decorated!')

my_function()
```

### Decorator Syntax in Python

The `@decorator` syntax is a convenient shortcut for:

```python
def say_hello():
    print('Hello!')
say_hello = my_decorator(say_hello)
```

### Role of **functools.wraps**

When defining decorators, particularly those that return functions, it is good practice to use `@wraps(func)` from the `functools` module. This ensures that the original function's metadata, such as its name and docstring, is preserved.
<br>

## 15. How can you create a _module_ in _Python_?

You can **create** a Python module through one of two methods:

- **Define**: Begin with saving a Python file with `.py` extension. This file will automatically function as a module. 

- **Create a Blank Module**: Start an empty file with no extension. Name the file using the accepted module syntax, e.g., `__init__ `, for it to act as a module. 

Next, use **import** to access the module and its functionality.

### Code Example: Creating a `math_operations` Module

#### Module Definition

Save the below `math_operations.py` file :

```python
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    return x / y
```

#### Module Usage

You can use `math_operations` module by using import as shown below:

```python
import math_operations

result = math_operations.add(4, 5)
print(result)

result = math_operations.divide(10, 5)
print(result)
```

Even though it is not required in the later **versions of Python**, you can also use statement `from math_operations import *` to import all the members such as functions and classes at once:

```python
from math_operations import *  # Not recommended generally due to name collisions and readability concerns

result = add(3, 2)
print(result)
```

### Best Practice
Before submitting the code, let's make sure to follow the **Best Practice**:

- **Avoid Global Variables**: Use a `main()` function.
- **Guard Against Code Execution on Import**: To avoid unintended side effects, use:

```python
if __name__ == "__main__":
    main()
```

This makes sure that the block of code following `if __name__ == "__main__":` is only executed when the module is run directly and not when imported as a module in another program.
<br>

## 16. What is the use of `if __name__ == '__main__':`?

The `if __name__ == '__main__':` construct in Python allows you to write code that will only execute when the script is run directly, not when it is imported as a module in another script. It is typically used to define a script's behavior when it is executed as the main program.

```python
if __name__ == '__main__':
    # This code block will execute when the script is run directly
    print("This script is being run directly")
else:
    # This code block will execute when the script is imported as a module
    print("This script is being imported as a module")
```

## 17. What are Python namespaces?

In Python, a namespace is a mapping from names to objects. It allows you to uniquely identify objects within a program. Namespaces ensure that object names are unique and can be used without naming conflicts.

## 18. How does a Python module search path work?

Python searches for modules in the following order:

1. The current directory.
2. Paths defined in the `PYTHONPATH` environment variable.
3. Installation-dependent default paths.

## 19. What is a Python package?

A Python package is a directory containing Python modules and an `__init__.py` file. It allows you to organize modules into a hierarchical structure. Packages are used to organize and distribute Python projects.

## 20. What is list comprehension? Give an example.

List comprehension is a concise way to create lists in Python by evaluating an expression for each item in an iterable. It provides a more readable and compact syntax compared to traditional loops.

```python
# Example of list comprehension
numbers = [1, 2, 3, 4, 5]
squared_numbers = [num ** 2 for num in numbers]
print(squared_numbers)  # Output: [1, 4, 9, 16, 25]
```

## 21. Explain dictionary comprehension.

Dictionary comprehension is similar to list comprehension but creates dictionaries instead of lists. It allows you to create dictionaries from iterables using a concise syntax.

```python
# Example of dictionary comprehension
numbers = [1, 2, 3, 4, 5]
squared_dict = {num: num ** 2 for num in numbers}
print(squared_dict)  # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

## 22. What are generators in Python, and how do you use them?

Generators in Python are functions that produce a sequence of results using `yield` instead of `return`. They generate values lazily and are memory efficient compared to lists.

```python
# Example of a generator function
def countdown(n):
    while n > 0:
        yield n
        n -= 1

# Using the generator
for num in countdown(5):
    print(num)  # Output: 5, 4, 3, 2, 1
```

## 23. How do you implement concurrency in Python?

Concurrency in Python can be achieved using threads (`threading`) or asynchronous programming (`asyncio`). Threads allow concurrent execution of tasks, while asyncio enables concurrent execution of asynchronous functions.

## 24. What are coroutines and how do they differ from threads?

Coroutines are specialized functions used for cooperative multitasking. They allow tasks to voluntarily yield control to other tasks, unlike threads which can be preemptively interrupted. Coroutines are managed by the programmer and are more lightweight than threads.

## 25. What is the Global Interpreter Lock (GIL)?

The Global Interpreter Lock (GIL) is a mutex that protects access to Python objects, preventing multiple native threads from executing Python bytecodes simultaneously. It limits the execution of Python threads to one at a time, affecting multi-threaded performance in CPU-bound tasks.

## 26. How would you optimize the performance of a Python application?

To optimize the performance of a Python application:

- Use efficient algorithms and data structures.
- Profile your code to identify bottlenecks.
- Optimize critical sections of code.
- Leverage concurrency and parallelism.
- Utilize caching mechanisms.
- Use compiled extensions or libraries for performance-critical tasks.

## 27. What is a context manager and the `with` statement in Python?

A context manager is an object that defines the `__enter__` and `__exit__` methods. It allows you to manage resources (like files or locks) in a way that ensures they are properly initialized and cleaned up. The `with` statement simplifies the management of these resources.

## 28. What strategies can be employed to optimize memory usage in Python applications?

To optimize memory usage in Python applications:

- Use generators and iterators instead of lists where possible.
- Avoid unnecessary copies of objects.
- Use data structures that are optimized for memory usage (e.g., `array.array`).
- Monitor and manage memory usage using tools like `memory_profiler`.
- Implement caching mechanisms to reuse objects.

## 29. What is monkey patching in Python?

Monkey patching refers to dynamically modifying or extending a module or class at runtime. It allows you to change or augment the behavior of code without altering its original source code. Monkey patching is powerful but should be used judiciously to avoid unexpected behavior.

## 30. What are classes in Python?

Classes in Python are blueprints for creating objects. They define attributes (data) and methods (functions) that operate on those attributes. Classes support object-oriented programming concepts such as inheritance, encapsulation, and polymorphism.

## 31. How does Python support object-oriented programming?

Python supports object-oriented programming (OOP) through:

- Classes and objects: Define and instantiate classes.
- Inheritance: Create subclasses that inherit attributes and methods from a parent class.
- Encapsulation: Hide implementation details within classes.
- Polymorphism: Define methods in subclasses that override methods in parent classes.

## 32. What is inheritance and give an example in Python?

Inheritance in Python allows a class (subclass) to inherit the attributes and methods of another class (superclass). It promotes code reusability and supports the "is-a" relationship.

```python
# Example of inheritance
class Animal:
    def __init__(self, name):
        self.name = name

    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        return "Bark"

dog = Dog("Fido")
print(dog.sound())  # Output: Bark
```

## 33. How do you achieve encapsulation in Python?

Encapsulation in Python is achieved by using private and protected access specifiers (`__` and `_` prefixes) to restrict access to certain class members. It hides the implementation details and prevents direct modification of data.

## 34. What are class methods, static methods, and instance methods?

- **Instance methods**: Operate on an instance of a class and have access to instance variables (`self` parameter).
- **Class methods**: Operate on the class itself and have access to class variables (`cls` parameter).
- **Static methods**: Do not operate on instance or class data and are defined using the `@staticmethod` decorator.

## 35. What is polymorphism in Python?

Polymorphism in Python allows objects of different classes to be treated as objects of a common superclass. It enables flexibility and extensibility by defining methods in subclasses that override methods in the superclass.

## 36. Explain the use of the `super()` function.

The `super()` function in Python is used to call methods of a superclass from a subclass. It allows you to access superclass methods and constructors, facilitating method overriding and inheritance.

## 37. What is method resolution order (MRO) in Python?

Method Resolution Order (MRO) defines the order in which Python looks for methods and attributes in a hierarchy of classes. It ensures that the correct method or attribute is accessed in cases of multiple inheritance.

## 38. What are magic methods in Python?

Magic methods, also known as dunder methods, are special methods in Python that begin and end with double underscores (`__`). They provide functionality to classes that can be used with built-in Python operations (e.g., `__init__`, `__repr__`, `__add__`).

## 39. How do you prevent a class from being inherited?

To prevent a class from being inherited in Python, define it with the `final` keyword or use the `__final__()` method.

## 40. How do you debug a Python program?

To debug a Python program:

- Use print statements for basic debugging.
- Use the built-in `pdb` debugger (`import pdb; pdb.set_trace()`).
- Use integrated development environments (IDEs) with debugging support (e.g., PyCharm, VS Code).
- Use logging for detailed debugging information.

## 41. What are some popular debugging tools for Python?

Popular debugging tools for Python include:
- `pdb`: Python's built-in debugger.
- `pdb++`: An enhanced version of `pdb` with colorization and tab completion.
- `PyCharm`: A powerful IDE with built-in debugging capabilities.
- `VS Code`: A lightweight IDE with debugging support through extensions.
- `ipdb`: A more interactive debugger with tab completion and syntax highlighting.

## 42. What is unit testing in Python?

Unit testing in Python involves testing individual units or components of a program in isolation. It ensures that each unit of code performs as expected by validating input, output, and behavior using automated tests.

## 43. How do you write a basic test case in Python using `unittest`?

To write a basic test case using `unittest`:

```python
import unittest

def add(a, b):
    return a + b

class TestAddition(unittest.TestCase):
    def test_add(self):
        result = add(3, 5)
        self.assertEqual(result, 8)

if __name__ == '__main__':
    unittest.main()
```

## 44. What is `pytest` and how is it used?

`pytest` is a testing framework for Python that allows you to write simple and scalable test cases. It supports test discovery, fixtures, parameterized testing, and more concise syntax compared to `unittest`.

## 45. How do you test a Python function with side effects?

To test a Python function with side effects, use assertions to verify the expected changes in state, output, or behavior caused by the function.

## 46. What is a breakpoint and how do you use it?

A breakpoint is a point in your code where program execution pauses for debugging purposes. You can set breakpoints in IDEs or debuggers like `pdb` to inspect variables, step through code, and analyze program state during execution.

## 47. How do you log messages in Python?

In Python, you can log messages using the `logging` module, which provides a flexible framework for recording log messages with different severity levels (e.g., DEBUG, INFO, WARNING, ERROR, CRITICAL).

## 48. How do you use assertions in Python?

Assertions in Python are statements that assert or guarantee a condition to be true. They are used for debugging and testing purposes to ensure that assumptions about program state hold true during execution.

## 49. What is a traceback, and how do you analyze it?

A traceback in Python is a report of the function calls made in the program up to the point where an exception occurred. It helps you trace the sequence of events leading to the error and analyze the cause of the exception.

## 50. How do you open and close a file in Python?

To open and close a file in Python:

```python
# Opening a file
file = open('example.txt', 'r')

# Reading from the file
content = file.read()
print(content)

# Closing the file
file.close()
```

## 51. What are the different modes for opening a file?

Python supports different modes for opening a file:
- `'r'`: Read (default).
- `'w'`: Write (truncate existing file or create new).
- `'a'`: Append (create new file if not exists).
- `'b'`: Binary mode.
- `'+'`: Read and write.

## 52. How do you read and write data to a file in Python?

To read and write data to a file in Python:

```python
# Writing to a file
with open('output.txt', 'w') as file:
    file.write('Hello, World!')

# Reading from a file
with open('output.txt', 'r') as file:
    content = file.read()
    print(content)  # Output: Hello, World!
```

## 53. What is a CSV file and how do you read it in Python?

A CSV (Comma Separated Values) file is a plain text file that stores tabular data in a structured format, where each line represents a row, and columns are separated by commas. You can read CSV files in Python using the `csv` module.

## 54. What are JSON files and how does Python process them?

JSON (JavaScript Object Notation) files store data in a human-readable format using key-value pairs. Python can process JSON files using the `json` module to parse JSON strings into Python objects (serialization) and convert Python objects back into JSON strings (deserialization).

## 55. How do you handle binary files in Python?

To handle binary files in Python, use the `'b'` mode when opening files. Binary files contain data that is not in human-readable format and may include images, executables, or serialized objects.

## 56. What is the `pandas` library, and how is it used?

`pandas` is a Python library for data manipulation and analysis. It provides data structures like `DataFrame` and `Series` for handling structured data, supports data cleaning, transformation, and analysis tasks.

## 57. How do you process data in chunks with `pandas`?

To process data in chunks with `pandas`, use the `chunksize` parameter in `read_csv()` or `read_excel()` to read large datasets in manageable chunks. Iterate over these chunks to perform operations on data incrementally.

## 58. What are the advantages of using NumPy arrays over nested Python lists?

NumPy arrays offer advantages over nested Python lists:
- Faster computation due to efficient element-wise operations.
- Memory efficiency with homogeneous data types.
- Built-in mathematical functions for array manipulation.
- Broadcasting for applying operations on arrays of different shapes.

## 59. How do you use the `os` and `sys` modules for interacting with the operating system?

The `os` and `sys` modules in Python allow you to interact with the operating system:
- `os`: Provides functions for interacting with the file system, environment variables, and processes.
- `sys`: Provides access to system-specific parameters and functions (e.g., command-line arguments).

## 60. What are the key features of the Flask framework?

Flask is a lightweight and flexible Python web framework with key features:
- Built-in development server and debugger.
- URL routing and RESTful request dispatching.
- Jinja2 templating and secure cookie support.
- Lightweight and extensible with modular extensions (Flask extensions).

## 61. How do you build a REST API in Flask?

To build a REST API in Flask:
- Define routes using `@app.route()` decorators for different HTTP methods (`GET`, `POST`, `PUT`, `DELETE`).
- Serialize and deserialize data using `jsonify()` and `request.json`.
- Implement authentication, error handling, and validation using Flask extensions (e.g., Flask-RESTful).

## 62. What is Django and what is it used for?

Django is a high-level Python web framework that promotes rapid development and clean, pragmatic design. It provides an ORM for database interaction, a powerful admin interface, and built-in security features. Django is used for building web applications and APIs.

## 63. How do you create a new Django project?

To create a new Django project:
1. Install Django (`pip install django`).
2. Use `django-admin` to create a new project:
   
```python
django-admin startproject myproject
```

## 64. What is an ORM, and how does Django use it?

An ORM (Object-Relational Mapping) is a programming technique for converting data between incompatible type systems (object-oriented programming languages and relational databases). Django uses an ORM to map Python objects to database tables, simplifying database interactions and query construction.

## 65. What is the purpose of the `requests` module?

The `requests` module in Python allows you to send HTTP requests easily. It provides simple APIs for performing HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) and handling responses, making it ideal for web scraping, API interaction, and testing.

## 66. How do you visualize data in Python?

To visualize data in Python, use libraries like `matplotlib`, `seaborn`, and `plotly`. These libraries provide functions for creating various types of plots (e.g., line plots, bar plots, scatter plots) to visualize data distributions, trends, and relationships.

## 67. What are some libraries you can use for machine learning in Python?

Python offers several machine learning libraries:
- `scikit-learn`: General-purpose machine learning library with algorithms for classification, regression, clustering, etc.
- `TensorFlow` and `Keras`: Deep learning frameworks for building neural networks.
- `PyTorch`: Deep learning framework with dynamic computation graphs.
- `XGBoost` and `LightGBM`: Gradient boosting libraries for tree-based models.

## 68. How do you schedule tasks in Python?

To schedule tasks in Python, use libraries like `schedule`, `APScheduler`, or system utilities like `cron` (on Unix-like systems). These tools allow you to automate repetitive tasks by specifying the schedule and actions to be performed.

## 69. What is asyncio and how do you use it?

`asyncio` is a Python module for asynchronous programming. It allows you to write concurrent code using `async` and `await` syntax, facilitating non-blocking I/O operations. `asyncio` is used for scalable network servers, web frameworks, and other asynchronous applications.

## 70. How do you implement socket programming in Python?

To implement socket programming in Python:
- Use the `socket` module to create socket objects (`socket.socket()`).
- Bind sockets to addresses and ports using `bind()`.
- Establish connections with `connect()` and handle incoming connections with `listen()` and `accept()`.
- Send and receive data using `send()` and `recv()` methods.

## 71. What are the steps to make a simple HTTP request in Python?

To make a simple HTTP request in Python:
- Use the `requests` module to create a `Request` object.
- Send the request using HTTP methods (`GET`, `POST`, `PUT`, `DELETE`).
- Handle the response object to retrieve data or handle errors.

## 72. How do you connect to a SQL database in Python?

To connect to a SQL database in Python:
- Install a DB-API compatible database driver (`mysql-connector-python`, `psycopg2`, `cx_Oracle`).
- Use the `connect()` function with connection parameters (e.g., host, port, username, password) to establish a connection object.
- Create a cursor object using `cursor()` to execute SQL queries and retrieve results.

## 73. How do you execute a query in a database using Python?

To execute a query in a database using Python:
- Use the cursor object (`cursor`) to execute SQL statements (`execute()`, `executemany()`).
- Fetch results using methods like `fetchone()`, `fetchall()`, or iterate over the cursor to process query results.

## 74. What is a NoSQL database and how would you interact with it in Python?

A NoSQL (Not Only SQL) database is a non-relational database that stores data in flexible, schema-less formats (e.g., key-value pairs, document stores, graph databases). To interact with NoSQL databases in Python, use client libraries (e.g., `pymongo` for MongoDB, `cassandra-driver` for Apache Cassandra) that provide APIs for CRUD operations and data modeling.

## 75. How would you automate a repetitive task in Python?

To automate a repetitive task in Python:
- Identify the task and its requirements (e.g., file processing, data analysis, web scraping).
- Write a Python script using appropriate libraries and modules to perform the task.
- Schedule script execution using tools like `cron`, task schedulers (`schedule`, `APScheduler`), or deployment platforms (e.g., AWS Lambda, Azure Functions).

## 76. How can Python scripts be used for system administration?

Python scripts can be used for system administration tasks such as:
- Managing files and directories (`os`, `shutil`).
- Interacting with the system environment (`os`, `sys`, `subprocess`).
- Automating tasks with cron jobs or task scheduling libraries.
- Monitoring system performance (e.g., `psutil` for process management).
- Network configuration and monitoring (`socket`, `paramiko` for SSH).

## 77. What techniques can you use for parsing text files?

To parse text files in Python, use techniques like:
- String manipulation (e.g., `split()`, `strip()`).
- Regular expressions (`re` module) for complex pattern matching.
- Tokenization and parsing libraries (`nltk`, `spaCy`) for natural language processing tasks.
- CSV and JSON parsing modules (`csv`, `json`) for structured data formats.

## 78. How do you manipulate CSV files using Python?

To manipulate CSV files in Python:
- Use the `csv` module for reading, writing, and manipulating CSV data.
- Read CSV files using `reader()` or `DictReader()` to handle rows as lists or dictionaries.
- Write CSV files using `writer()` or `DictWriter()` to output data from lists or dictionaries.

## 79. How do you automate web browsing using Python?

To automate web browsing in Python:
- Use the `requests` module for HTTP requests and web scraping.
- Utilize headless browsers with tools like `Selenium` for simulating user interactions (e.g., form submissions, button clicks).
- Parse HTML content with libraries (`BeautifulSoup`, `lxml`) to extract data from web pages.

## 80. What are regular expressions and how are they used?

Regular expressions (regex) are sequences of characters that define search patterns for matching strings. They are used for pattern matching, text manipulation, and data validation tasks in Python.

## 81. How do you compile a regular expression in Python?

To compile a regular expression in Python, use the `re.compile()` function:
```python
import re

pattern = re.compile(r'\d+')  # Compiles a regex pattern to match digits
```

82. Give examples of commonly used regex patterns in Python.
   ```python
   - Matching email addresses: `^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$`
   - Matching URLs: `^(http|https):\/\/[^\s]+$`
   - Matching dates in YYYY-MM-DD format: `^\d{4}-\d{2}-\d{2}$`
   - Matching phone numbers: `^\+?\d{1,3}[-\.\s]?\(?\d{3}\)?[-\.\s]?\d{3}[-\.\s]?\d{4}$`
  ```
83. How do you replace text in a string using regular expressions?
   ```python
   import re
   text = "Hello, my name is Alice."
   new_text = re.sub(r'Alice', 'Bob', text)
   print(new_text)  # Output: "Hello, my name is Bob."
   ```

84. When should you use regular expressions and when should you avoid them?
   Use regular expressions when:
   - You need to search for complex patterns in text.
   - You want to extract specific information from structured text data.
   - Performance considerations are acceptable for the task at hand.

   Avoid regular expressions when:
   - The task can be easily accomplished using simpler string methods.
   - The pattern is overly complex and difficult to understand or maintain.
   - Performance is a critical concern in high-volume applications.

85. How do you manage Python environments using venv?
   ```python
   python3 -m venv myenv
   source myenv/bin/activate  # On Unix/macOS
   myenv\Scripts\activate  # On Windows
   ```

86. What is a virtual environment and when should you use one?
   A virtual environment is a self-contained directory that contains a Python installation for a particular project, along with its own dependencies. You should use a virtual environment to isolate project dependencies and avoid conflicts between different Python projects.

87. How do you install Python packages?
   ```python
   pip install package_name
   ```

88. How do you manage dependencies in Python projects?
   Dependencies can be managed using a requirements file (requirements.txt) listing all packages and versions:
   ```python
   pip freeze > requirements.txt
   pip install -r requirements.txt
   ```

89. What is Docker and how do you use it with Python?
   Docker is a platform for developing, shipping, and running applications in containers. With Docker, you can create containerized environments for Python applications, ensuring consistency across different development and deployment environments.

90. What is data science and how is Python used in it?
   Data science is the field of study that combines domain expertise, programming skills, and knowledge of mathematics and statistics to extract meaningful insights from data. Python is widely used in data science for its extensive libraries (like NumPy, pandas, and scikit-learn) that support data analysis, visualization, and machine learning.

91. How do you clean and preprocess data in Python?
   Data cleaning and preprocessing in Python involve tasks such as handling missing values, removing duplicates, normalizing data, and transforming categorical variables into numerical representations. Libraries like pandas and scikit-learn provide tools and methods for these tasks.

92. What is a DataFrame in pandas?
   A DataFrame in pandas is a two-dimensional, size-mutable, labeled data structure with columns of potentially different data types. It is similar to a spreadsheet or SQL table, and it is used for data manipulation and analysis.

93. How do you handle missing data with pandas?
   Pandas provides methods like `isnull()`, `dropna()`, and `fillna()` to handle missing data. You can identify missing values, drop rows or columns with missing data, or fill missing values with specified values (e.g., mean, median).

94. How can you perform data aggregation in pandas?
   Data aggregation in pandas involves operations like sum, mean, count, etc., applied to grouped data. You can use `groupby()` along with aggregation functions to compute summary statistics for groups of data.

95. What is scikit-learn and how do you use it?
   Scikit-learn is a machine learning library in Python that provides tools for data mining and data analysis. It includes various algorithms and utilities for tasks such as classification, regression, clustering, dimensionality reduction, and model selection.

96. How do you handle feature selection in Python?
   Feature selection in Python involves techniques like statistical tests, feature importance ranking, and model-based selection. Libraries like scikit-learn provide functions and classes (e.g., `SelectKBest`, `RFECV`) for performing feature selection based on various criteria.

97. What is cross-validation and how do you perform it in Python?
   Cross-validation is a technique used to evaluate the performance of machine learning models by splitting the data into multiple subsets (folds). Scikit-learn provides functions and classes (e.g., `KFold`, `cross_val_score`) for performing cross-validation in Python, helping to assess a model's generalization ability.

98. How do you save a trained machine learning model with Python?
   ```python
   import joblib
   joblib.dump(model, 'model.pkl')
   ```

99. What are the steps involved in training a machine learning model with Python?
   Steps involved in training a machine learning model include:
   - Data preprocessing (cleaning, normalization, feature engineering)
   - Splitting data into training and testing sets
   - Choosing a suitable algorithm and model
   - Training the model on the training data
   - Evaluating the model's performance on the test data
   - Fine-tuning the model (hyperparameter tuning)
   - Saving the trained model for future use


#### Explore all 100 answers here 👉 [Devinterview.io - Python](https://devinterview.io/questions/web-and-mobile-development/python-interview-questions)

<br>


<br>
<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>


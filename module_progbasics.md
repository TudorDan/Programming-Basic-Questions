# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
* The purpose of a list is to collect objects in an orderly manner. 
* Some list methods are: _append()_, _extend()_, _insert()_, _remove()_, or _pop()_.
#### What is the difference between a list/array and a set?
* A list is ordered, can be accessed using an index, can have duplicate elements and are mutable (elements can be added,deleted, or moved around). 
* A set is unordered, its elements are unique and are immutable (they can't be changed once they have been assigned).
#### What is the purpose and methods of a dictionary/map data structure?
* The purpose of a dictionary is to map keys to values and store them in an array or collection. 
* The methods of a dictionary are: _items()_, _keys()_, _values()_, _get()_ and _popitem()_.
* * *

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
```
def fibonacci(n):
    terms = [0, 1]
    i = 2
    while i <= n:
        terms.append(terms[i - 1] + terms[i - 2])
        i += 1
    return terms
```
#### How do you find a max value in a list/array if you can’t use any built-in functions?
```
def max_in_list(listOfNr):
    maxi = -1.8e308
    for number in listOfNr:
        if maxi < number:
            maxi = number
    return maxi
```
#### How do you find the average of values in a list/array if you can’t use any built-in functions?
```
def find_avg(array):
    sum_of_values = 0
    for value in array:
        sum_of_values += value
    return sum_of_values / len(array)
```
#### What do we call an *in-place* sort?
* We call _sort()_ an in-place method because it modifies a given list in-place (it modifies the actual list on the spot without returning a new one) by using _<_ comparisons between items.
#### Explain an algorithm which sorts a list!
* Example of *Bubble Sort* algorithm:
```
finished = False                                 # declare a boolean variable to check if we finished sorting the list
list_length = len(a_list)           # get the number of items in a list so that we don't call len() for each iteration
while not finished:                 # we keep looping until we finished sorting (finished == True)
    finished = True                 # we assume it's finished (the condition to break out of the while loop)
    for i in range(list_length - 1):               # iterate through the list without the last item
        if a_list[i] > a_list[i + 1]:              # if the current item is bigger than the next..
            a_list[i], a_list[i + 1] = a_list[i + 1], a_list[i]         # we swap them
            finished = False        # keep looping until we have nothing left to swap
```
* * *

### Programming paradigms - procedural

#### What is the call stack?
* The _call stack_ is a frame where Python stores information about functions which have been called. 
* Whenever a function is called, a new stack frame is added to the stack – all of the function’s parameters are added to it, and as the body of the function is executed, local variables will be created there.
* When the function finishes executing, its stack frame is discarded, and the flow of control returns to wherever you were before you called the function, at the previous level of the stack.
#### What is “Stack overflow”?
* _Stack overflow_ is a filled up stack frame. Python’s stack has a finite size – if we keep placing instances of the function on the stack we will eventually fill it up and cause a stack overflow.
#### What are the main parts of a function?
* The mai parts of a function are: _parameters_, _function body_, _variables_, _statements_, _expressions_, _function call_ and _arguments (input parameters)_.
* * *

### Programming languages - Python  
#### How do you use a dictionary in Python?
* We can use a dictionary to store key-value pairs. To define a dictionary literal, we put a comma-separated list of key-value pairs between curly brackets. We use a colon to separate each key from its value. We access values in the dictionary by using keys instead of indices.
#### What does it mean that an object is immutable in Python?
* _Immutable_ means we cannot alter the existing value in any way. Some values in Python can be modified, and some cannot. 
* Integers, floating-point numbers and strings are all immutable types. Tuples are immutable data types.
#### What is conditional expression in Python?
* A _conditional expression_ is a selection control statement that allows programmers to change the flow of control.
* Conditionals (the _if/elif/else_ family) can be used to pick a code block based upon the truth value of the conditions in them.
#### What are different types of arguments in Python?
* There are 3 types of arguments:
    1. _optional_ => To make a parameter optional, we need to supply a default value for it. Optional parameters must come after all the required parameters in the function definition:
    ```
    def make_greeting(title, name, surname, formal=True):
        if formal:
            return "Hello, %s %s!" % (title, surname)
        return "Hello, %s!" % name
    make_greeting("Mr", "John", "Smith")
    make_greeting("Mr", "John", "Smith", False)
    ```
    2. _positional_ => a tuple of values which are matched up with parameters in the function signature based on their positions:
    ```
    def make_greeting(title, name, surname, formal=True, time=None):
        if formal:
            fullname =  "%s %s" % (title, surname)
        else:
            fullname = name
        if time is None:
            greeting = "Hello"
        else:
            greeting = "Good %s" % time
        return "%s, %s!" % (greeting, fullname)
    make_greeting("Mr", "John", "Smith", False, "evening")
    ```
    3. _keyword_: => explicitly specify the parameter names along with the values:
    ```
    make_greeting(title="Mr", name="John", surname="Smith", formal=False, time="evening")
    ```
#### What is variable shadowing? (context: variable scope)
* _Variable shadowing_ occurs when a variable declared within a certain scope (decision block, method, or inner class) has the same name as a variable declared in an outer scope:
```
x = 0
def outer():
    x = 1
    def inner():
        x = 2
        print("inner:", x)
    inner()                # prints //inner: 2
    print("outer:", x) 
outer()                    # prints //outer: 1
print("global:", x)        # prints //global: 0
```
#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
* You may encounter an IndexError: list index out of range.
#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
* The "golden rule" of variable scoping in Python (context: LEGB, L = Local, E = Enclosed (function is wrapped inside another function), G = Global, B =Built-in): when local as well as global variable is present, *preference is given to the local variable*. 
* The lifetime of a variable: it exists for as long as the function is executing. 
#### If you need to access the iterator variable after a for loop, how would you do it in Python?
* The built-in Python function _iter()_, which returns something called an iterator. The built-in function _next()_ is used to obtain the next value from in iterator:
```
a = ['foo', 'bar', 'baz']
itr = iter(a)
next(itr)
next(itr)
next(itr)
```
* If all the values from an iterator have been returned already, a subsequent next() call raises a StopIteration exception. 
#### What type of elements can a list contain in Python?
* A list can contain basically any type of elements.
#### What is slice operator in Python and how to use?
* The slice operator is a method that extracts a subset of a list, which will itself be a list.
* In order to use it, you need to specify an upper and lower bound. Note that our sublist will include the element at the lower bound, but _exclude_ the element at the upper bound:
```
animals = ['cat', 'dog', 'fish', 'bison']
print(animals[1:3]) # ['dog', 'fish']
print(animals[1:-1]) # ['dog', 'fish']
```
#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
* The arithmetic operators that can be used on lists are:
    - **+** addition
    - **-** subtraction
    - __*__ multiplication
    - **/** division
    - **%** modulo (the remainder of division)
    - __**__ exponentiation
#### What is the purpose of the in and not in membership operators in Python?
* Membership operators like _in_ and _not in_ are operators used to validate the membership of a value. It test for membership in a sequence, such as strings, lists, or tuples.
#### What does the + operator mean when used with strings in Python?
* When used with strings, the __+__ operator means concatenation: a method to add multiple strings together.
#### Explain f strings in Python?
* Python 3.6 added a new string formatting approach called formatted string literals or “f-strings”. This new way of formatting strings lets you use embedded Python expressions inside string constants:
```
>>> f'Hello, {name}!'
'Hello, Bob!'
```
#### Name 4 iterable types in Python!
* Lists, tuples, dictionaries and sets are all iterable types in Python. 
#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
* List Comprehension allows us to create a list using for loop with lesser code.
* The Generator Expression allows us to create a generator without the yield keyword. Instead of creating a list/set/dictionary and keeping the whole sequence in the memory, the generator generates the next element in demand.
```
list_comprehension = [i for i in range(11) if i % 2 == 0]
generator_expression = (i for i in range(11) if i % 2 == 0)
```
* The generator yields one item at a time and generates item only when in demand. Whereas, in a list/set/dictionary  comprehension, Python reserves memory for the whole list. Thus we can say that the generator expressions are memory efficient than the lists/set/dictionary comprehensions. Also generator expressions are faster than list/set/dictionary comprehensions and hence time efficient.
#### Does the order of the function definitions matter in Python? Why?
 * Yes, the order of the function definitions does matter in Python, because any call to a function must come after that function definition.
#### What does unpacking mean in Python?
* We can use * or ** when we are calling a function to _unpack_ a sequence or a dictionary into a series of individual parameters:
```
my_list = ["one", "two", "three"]
print_args(*my_list)
my_dict = {"name": "Jane", "surname": "Doe"}
print_kwargs(**my_dict)
```
#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
* A function without an explicit return statement returns _None_. The variable will the value of _None_.
* * *

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
#### What does step over, step into and step out mean while using the debugger?
#### How can you start to debug a program from a certain line using the debugger?

### Version control

#### What are the advantages of using a version control system?
#### What is the difference between the working directory, the staging area and the repository in git?
#### What are remote repositories in git?
#### Why does a merge conflict occur?
#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
#### What does it mean atomic commits and descriptive commit messages?
#### What’s the difference between git and GitHub?

## Software design

### Clean code

#### What does clean code mean?
#### What steps do we usually do during a clean code refactoring?

### Error handling

#### What is exception handling?
#### What are the basics of exception handling in Python?
#### In which case should we catch an exception? Why?
#### What can/should we do with an exception in the ‘except’ block?
#### What does the else and finally statement do in a try-except block in Python?

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?

## Programming environment

### Unix

#### What is UNIX and what is Linux?
#### What do we call the shell in Linux?
#### What does root means in a Linux environment?
#### How do you access your personal files in Linux?
#### How can you install an application in Linux?
#### What is package management in Linux, what are repositories?
#### How do you navigate in the filesystem with the command line?
#### What does the following commands do: mkdir, rm, cat, cp, touch?
#### How can you look up what does a command do in Linux if you have no internet connection?
#### What does the following commands do: head, tail, more, less?
#### How do you download a file from internet using the terminal?

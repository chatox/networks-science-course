# Practice Session 03: Python for C Programmers

So far you have programmed mostly in C. During this course, we will use Python, which you will find much more suitable for data and graph management tasks. Most of the time we will be using Python to:

* Read from files to create a graph that Cytoscape can read.
* Run an algorithm over a graph.

The particular version of Python we will use is Python 3, and in particular we will use IPython, its interactive version, through an environment named the Jupyter Notebook. Jupyter is a web-based application that can contain code, visualizations, and text.

The rest of this document is a simple introduction to Python for C programmers. Remember that you learn by doing, so enter these commands into a new Python Notebook, play with variations, see what works and what does not work.

# 1. Notebooks

## 1.1. Creating a notebook

* In Unix, you can run "ipython3 notebook".
* Then, create a new Python 3 notebook.

## 1.2. Understanding the notebook

You can name your notebook by clicking on "Untitled" on the top-left. Similarly to cloud-based office applications, notebooks are auto-saved. You can also save them with File > Save and Checkpoint, or with the "Save" icon in the toolbar.

The green rectangle shows the current *cell*. Enter the following:

    pi = 3.1415927
    r = 3
    p = 2 * pi * r
    print(p)

For this example to work, you must be careful not to introduce any space/indentation at the beginning of a line, because **indentation is important in Python**.

Execute that cell by pressing `Shift-Enter`. The result appears (the perimeter of a circumference of radius 3), and a new cell is created. You can also press `Control-Enter` if you do not want to create a new cell.

Type more code into the second cell:

```python
print(5*r)
```

As you can see, the variables are preserved from cell to cell.

# 2. Language basics: from C to Python

## Filename

In C, source files were named `*.c` or `*.h` for headers.

In Python, files are named `*.py` (for source files) or `*.ipynb` (for notebooks).

## Numbers

In Python you have basically the same operations as in C: `a+b`, `a-b`, `a*b`, `a/b`, `a%b`, and `a**b`; the last one means *a* to the power of *b*.

In Python there is no `++` or `--` operators as in C, so if you want to increase a variable by one, you should do: `a += 1` (`a++` works in C, but not in Python).

## Numeric types

In Python you do not need to declare a variable type, not even if it is a number or a string. For example, instead of `int x=10` you simply say `x=10`.

The two main numeric types we will use are *int*, which are implemented typically using long integers, and *float*, which are implemented typically using double. You can convert between these types:

```python
x = 1
y = 2
print(type(x))
print(type(y))
print(type(x+y))
print(type(x/y))
```

Now try executing the same but changing `y=2` to `y=float(2)` or `y=2.0`. The second is a common way of forcing a number to be interpreted as a float. You can convert easily between types using functions `int()`, `float()`, `str()`, e.g., `x=(int)y` in C becomes `x=int(y)` in Python.

## Printing and formatting

Printing is done using the `print()` function, which from Python 3 onwards must use parenthesis (Python 2 allowed `print "hello"`, but in Python 3 you must say `print("hello")`). Note that `print()` generates a newline:

```python
print("hello")
```

The `print()` function accepts a single parameter. To format numbers, one must use the `%` operator. This operator takes a string containing formatting instructions (in the same way as `printf` in C), and a tuple with one element per formatting, examples:

```python
fruit = "oranges"
amount = 16
print("Quantity of %s: %d" % (fruit, amount))

pi = 3.141592653589793
print("Pi with 4 decimals: %.4f" % pi)
```

## Strings

In C single quotes were used to represent characters, while double quotes represented strings.

In Python single and double quotes both represent strings, so you can just do `word = "hello"` or `word='hello'`. They are the same.

For string constants, in C you would say:

```C
char c[] = "this is a phrase"
```

In Python:

```python
c = "this is a phrase"
```

### String concatenation

In Python, strings are concatenated using `+`:

```python
z = "hello" + " " + "world"
print(z)
```

### String splitting

In Python, strings can be separated using `str.split(separator)`. The result is an array:

```python
x = "hello this,is to be,separated"
print(x.split(","))
```

### String joining

In Python, an array of strings can be joined using `joiner.join(array)`:

```python
y = ["these", "must", "be", "joined"]
print(",".join(y))
```

## Arrays

In C you would say:

```C
char days[][10] = {"Monday", "Tuesday", ..., "Sunday"}
```

In Python you say:

```python
days = ["Monday", "Tuesday", ..., "Sunday"]
```

As you can see, in Python, as in C, arrays are represented by brackets, and numbered from zero, for instance:

```python
x = ["a", "b", "c", "d"]
print(x[2])
```

Sub-arrays can be extracted easily using Python's slice notation, which in simplified form is `array[start:end]`, with both `start` and `end` optional (there are more options):

```python
print(x[1:])     # ["b", "c", "d"]
print(x[1:3])    # ["b", "c"]
print(x[2:4])    # ["c", "d"]
print(x[:3])     # ["a", "b", "c"]
```

The length of an array is obtained with `len(x)`.

## Dictionaries

Python has powerful expressions for managing dictionaries. Dictionaries are declared using `{ ... }` to distinguish them from arrays which use `[ ... ]`.

```python
person = { "name": "Jack", "age": 21 }
print(person["name"])
print(person["age"])
print(person["phone"])   # Error
```

Keys can be added simply by specifying them, or deleted using `del`:

```python
person["yob"] = 1998
del person["age"]
print(person)
```

## Booleans

In C the `stdbool` library defined TRUE and FALSE.

In Python these are built-in types `True` and `False`.

## Null values

In C a null pointer was represented by `NULL` which also has the value zero.

In Python there is the built-in `None` which represents something inexistent or missing and has no value.

## Pointers

In Python almost everything is a reference so no need to deal with pointers (yay!).

# 2. Program structure

## Main function

In Python and specially in IPython you do not need a main method. Whatever you type will be executed once you type `shift-enter` or `control-enter`.

## Comments

In Python comments start with a `#` if it's a single line, and with `'''` if it's multiple lines. Example:

```
    # This is a single line comment

    ''' This is a comment
        that uses several lines
    '''
```

## Brackets and semi-colons

In Python there are no brackets, but indentation, and statements end with the end-of-line, not with a semicolon. All statements in a block must be indented.

## Conditionals

In C a conditional had the structure:

    if(condition) {
      printf(TRUE);
    } else {
      printf(FALSE);
    }

In Python this conditional is written as:

    if condition:
        print(True)
    else:
        print(False)

Instead of `elsif`, in Python one uses `elif`:

```python
a = 4
b = 40

if a < b:
    print("a is less than b")
elif a == b:
    print("a is equal to b")
elif a > b:
    print("a is greater than b")
else:
    print("Something is very wrong")
```

## For loop (sequence of numbers)

In C this prints 0..9:

```C
for(int i=0; i<10; i++) {
  print("%d\n", i);
}
```

The equivalent in Python is:

```python
for i in range(0,10):
    print("%d" % i)
```

The `range` function is compatible with the numbering used in array slices, so the first number is inclusive and the second number is exclusive. The following print the same:

```python
# Using slice
print(x[1:3])

# Using range
for i in range(1,3):
    print("x[%d]=%s" % (i, x[i]))
```

## For loop (array)

In Python one can also loop through an array:

```python
days = ["Monday", "Tuesday", "Wednesday"]

for day in days:
    print day
```

## While loop

Example in C:

```C
int a = 10
while(a>0) {
    printf("a=%d\n", a);
    a--;
}
```

Example in Python:

```python
a = 10
while a > 0:
    print(a)
    a -= 1
```

## Functions

Function don't have a return type in Python, they assume the return type of the variable you return.

```python
def factorial(x):
    if x == 1:
        return 1
    else:
        return x * factorial(x-1)

print("%d! == %d" % (6, factorial(6)))
```

# 3. Reading files

## Modules

In C you would say:

```C
#include <module.h>
```

In Python this is done with:

```python
import module
```


Python also offers to import only some functions from a module, e.g.:

```python
from module import function1, function2, function3
```

## The io module

In C you used the `stdio` module. In Python there is an `io` module.

We are going to test this module. First, create a file named `test.csv` containing a few lines of text. Place it in the same directory as the Python notebook. You can create it from within Jupyter's file selector by selecting "New > Text file ..." in the upper-right corner (not from within an open notebook, but from within the list of files.

In this file, enter a list of comma-separated values like this:

    person,age,color
    Myriam,24,red
    John,21,blue
    Hector,32,red
    Jin,27,blue

Now, read this file with the following:

```python
import io

FILENAME = "test.csv"

with io.open(FILENAME) as file:
    for line in file:
        # Remove trailing newlines
        line = line.rstrip()

        # Print
        print("Read line '%s' of length %d characters" % (line, len(line)))
```

Now we have only read the lines, we need to split them using commas. However, it is much easier and error-proof to use a module for this.

## The csv module

Python's csv module provides a powerful mechanism for parsing comma-separated files.

```python
import io
import csv

FILENAME = "test.csv"

with io.open(FILENAME) as file:
    reader = csv.DictReader(file, delimiter=',')
    for row in reader:
        print("%s is %d years old" % (row['name'], int(row['age'])))
```

Note that you can also store the people being read in an array, and even the distinct values of a variable:

```python
people = []
colors_dict = {}
with io.open(FILENAME) as file:
    reader = csv.DictReader(file, delimiter=',')
    for row in reader:
        people.append(row)
        if row["color"] not in colors_dict:
            colors_dict[row["color"]] = True

colors = colors_dict.keys()
print(people)
print(colors)
```

Note that `people` is an array of dictionaries, `colors_dict` is a dictionary where keys are the colors seen, and `colors` is an array of strings, containing all the different colors seen.

# DELIVER (individually)

At the end of the session, deliver a zip file containing the file `test.csv`, and a clean Python notebook `test.ipynb` containing code to read the file and compute, for each different color, the average age of people having that color, for instance, in the example above, it should print:

    Average age of red: 28.00
    Average age of blue: 24.00

# References

* https://www.stormingrobots.com/prod/tutorial/C2Python.pdf

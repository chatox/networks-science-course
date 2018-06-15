# Practice Session 03: Python for C Programmers

So far you have programmed mostly in C. During this course, we will use Python, which you will find much more suitable for data and graph management tasks. Most of the time we will be using Python to:

* Read from files to create a graph that Cytoscape can read.
* Run an algorithm over a graph.

The particular version of Python we will use is Python 3, and in particular we will use IPython, its interactive version, through an environment named the Jupyter Notebook. Jupyter is a web-based application that can contain code, visualizations, and text.

# 1. Notebooks

## 1.1. Creating a notebook

* In Unix, you can run "ipython3 notebook".
* Then, create a new Python 3 notebook.

## 1.2. Understanding the notebook

You can name your notebook by clicking on "Untitled" on the top-left. Similarly to Google Docs documents, they notebooks are auto-saved. You can also save them with File > Save and Checkpoint, or with the "Save" icon in the toolbar.

The green rectangle shows the current *cell*. Enter the following:

    pi = 3.1415927
    r = 3
    p = 2 * pi * r
    print(p)

Note that you must be careful not to introduce any space/indentation at the beginning of a line, because **indentation is important in Python**.

Execute that cell by pressing `Shift-Enter`. The result appears (the perimiter of a circumference of radius 3), and a new cell is created.

Type more code into the second cell:

    print(5*r)

As you can see, the variables are preserved from cell to cell.

# 2. Language basics: from C to Python

## Filename

In Python files are named `*.py` (for source files) or `*.ipynb` (for notebooks).

## Numbers

In Python you have basically the same operations as in C: `a+b`, `a-b`, `a*b`, `a/b`, `a%b`, and `a**b`; the last one means *a* to the power of *b*.

Numbers can be float ... integer ...

## Strings

In Python single and double quotes are the same, so you can just do `word = "hello"` or `word='hello'`. They are the same.

For string constants, in C you would say:

    char c[] = "this is a phrase"

In Python:

    c = "this is a phrase"

## Types

In Python you don't need to declare a variable type, so instead of `int x=10` you simply say `x=10`.

You can convert easily between types using functions `int()`, `float()`, `str()`, e.g., `x=(int)y` in C becomes `x=int(y)` in Python.

## Pointers

In Python almost everything is a reference so no need to deal with pointers (yay!).

## Main function

In Python and specially in IPython you do not need a main method. Whatever you type will be executed.

## Comments

In Python comments start with a `#` if it's a single line, and with `'''` if it's multiple lines. Example:

    # This is a single line comment

    ''' This is a comment
        that uses several lines
    '''

## Brackets and semi-colons

In Python there are no brackets, but indentation, and statements end with the end-of-line, not with a semicolon. All statements in a block must be indented.

## Modules

In C you would say:

    #include <module.h>

In Python this is done with:

    import module

Python also offers to import only some functions from a module, e.g.:

    from module import function1, function2, function3

# 3. Simple examples

## Conditional

TBD

## Printing

Newline ...

Formatting % ...

## For loop

Example in C:

    for(int i=0; i<10; i++) {
      print("%d\n", i);
    }

Equivalent in Python:

    for i in range(0,10):
        print("%d" % i)

## While loop

Example in C:

    while(condition) {
      do_something();
    }

Example in Python:

    while condition:
        do_something()

## Functions

Function don't have a return type in Python, they assume the return type of the variable you return.

Example in C:

    int factorial(int num) {
        ...
        return result;
    }

Example in Python:

    def factorial(num):
        ...
        return result

# 4. Arrays

## Arrays and elements of Arrays

Arrays are made with brackets `[` and `]`.

## Array constants

In C you would say:

    char days[][10] = {"Monday", "Tuesday", ..., "Sunday"}

In Python you say:

    days = ["Monday", "Tuesday", ..., "Sunday"]

## Array length

...

## Extracting and manipulating elements

# 5. Dictionaries

Dictionaries are created with curly braces `{` and `}`.

....

# 6. Using the module io to read a file

... simple example (more in the next session) ...

... perhaps I can use `personajes.txt` from GoT in EDA1.

1. Write program to transform to another format
2. Read from the other format

# References

* https://www.stormingrobots.com/prod/tutorial/C2Python.pdf

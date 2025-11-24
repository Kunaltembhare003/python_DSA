# python function
```python
def function_name(parameter):
    '''docstring'''
    # function body
    # Python function
    ```python
    def function_name(parameter):
        """docstring"""
        # function body
        return expression
    ```

    ## positional and keyword arguments

    ```python
    def print_numbers(*args):
        for number in args:
            print(number)
    ```
```

## Lambda function
Small anonymous functions defined using the `lambda` keyword. They can have any number of arguments but only a single expression. They're commonly used for short operations or as arguments to higher-order functions.

```python
lambda arguments: expression
```

## map function
`map()` applies a function to every item of an iterable (or multiple iterables) and returns an iterator in Python 3.

```python
def square(x):
    return x * x

numbers = [1, 2, 3, 4, 5]

# map returns an iterator — convert to list to view results
list(map(square, numbers))  # [1, 4, 9, 16, 25]
```

### Lambda with map

```python
numbers = [1, 2, 3, 4, 5]
list(map(lambda x: x * x, numbers))
```

### Map with multiple iterables

```python
number1 = [1, 2, 3]
number2 = [4, 5, 6]


added_number = list(map(lambda x, y: x + y, number1, number2))
# [5, 7, 9]
```

### map() vs for-loop — why and when to use map

Brief contract:
- Input: an iterable (or several iterables) and a callable
- Output: an iterator (in Python 3) that yields the transformed items
- Error modes: callable raises exceptions the same as in a loop; mismatched iterable lengths stop at shortest iterable

Why `map()` can be preferable to an explicit `for` loop:

- Conciseness and declarative style: `map()` expresses "apply this function to every item" without manual loop boilerplate (initialize list, append, etc.). This can make intent clearer for simple transformations.
- Laziness / memory efficiency: `map()` returns an iterator in Python 3, so it doesn't build the whole output list in memory. This is useful for very large inputs or when chaining transforms.
- Composition: `map()` composes nicely with other iterator-based tools like `filter()`, `itertools` functions, or another `map()` without materializing intermediate lists.
- Potential performance: when the function applied is a built-in implemented in C (for example `str.upper`, `math.sqrt`, or `int`), `map()` can be slightly faster because the iteration and function-call overhead is lower than equivalent Python-level loops. However, performance depends on the callable and CPython implementation details.

When a `for` loop (or a list comprehension) may be better:

- Readability for complex logic: if the transformation requires multiple statements, error handling, or complex control flow, a `for` loop is clearer and more maintainable.
- List comprehensions often offer similar readability and are idiomatic in Python; for many cases a list comprehension is preferred over `map(lambda ...)` because it's more obvious to readers.
- Benchmarks vary: in CPython, list comprehensions are often as fast or faster than `map()` with a `lambda` because the lambda is still a Python function. So prefer the most readable option and only optimize after measuring.

Equivalent examples

Using `map()`:

```python
def square(x):
    return x * x

numbers = [1, 2, 3, 4, 5]
squares_map = list(map(square, numbers))  
# [1, 4, 9, 16, 25]
```

Using a `for` loop:

```python
squares_loop = []
for x in numbers:
    squares_loop.append(square(x))
# [1, 4, 9, 16, 25]
```

Using a list comprehension (idiomatic Python):

```python
squares_comp = [x * x for x in numbers]
# [1, 4, 9, 16, 25]
```

Notes and edge cases:
- `map()` stops when the shortest input iterable is exhausted when multiple iterables are provided.
- Because `map()` returns an iterator, if you need to use the results multiple times consider storing them (e.g., `list(map(...))`) or using `itertools.tee` to duplicate the iterator.
- Prefer clarity: choose `map`, `for` loop, or list comprehension based on readability and measured performance for your use case.

## Filter function
`filter()` constructs an iterator from elements of an iterable for which a function returns True.

```python
def even(num):
    if num%2==0:
        return True
# use filter
lst = [1,2,3,4,5,6,7,8,9,10,11]
filter(even,lst)
# [2,4,6,8,10]

## filter with lambda
grater_than_five= list(filter(lambda x:x>5 and x%2==0,lst))
# [6,8,10]
```
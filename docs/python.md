# Python Sets

A set in Python is an unordered collection of unique elements. Sets are defined by enclosing elements in curly braces `{}` or using the `set()` constructor. Sets are mutable, but their elements must be immutable (numbers, strings, tuples).

## Creating Sets

```python
# Using curly braces
fruits = {'apple', 'banana', 'orange'}

# Using set() constructor
numbers = set([1, 2, 3, 4, 5])

# Empty set
empty_set = set()  # Note: {} creates an empty dictionary, not a set
```

## Key Characteristics

1. **Unique Elements**: Sets automatically remove duplicates
2. **Unordered**: Elements have no defined order
3. **Mutable**: The set itself can be modified
4. **Hashable Elements**: Set elements must be immutable

## Common Set Operations

### 1. Adding Elements

```python
my_set = {1, 2, 3}
my_set.add(4)        # Adds a single element
my_set.update([5, 6]) # Adds multiple elements
```

### 2. Removing Elements

```python
my_set = {1, 2, 3, 4}
my_set.remove(4)     # Raises KeyError if element not found
my_set.discard(4)    # No error if element not found
my_set.pop()         # Removes and returns an arbitrary element
my_set.clear()       # Removes all elements
```

### 3. Set Mathematical Operations

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union (all unique elements from both sets)
union_set = set1.union(set2)  # or set1 | set2
# Result: {1, 2, 3, 4, 5}

# Intersection (elements present in both sets)
intersection_set = set1.intersection(set2)  # or set1 & set2
# Result: {3}

# Difference (elements in set1 but not in set2)
difference_set = set1.difference(set2)  # or set1 - set2
# Result: {1, 2}

# Symmetric Difference (elements in either set, but not in both)
symmetric_diff = set1.symmetric_difference(set2)  # or set1 ^ set2
# Result: {1, 2, 4, 5}
```

### 4. Set Comparisons

```python
set1 = {1, 2}
set2 = {1, 2, 3}

# Subset (is set1 contained within set2?)
is_subset = set1.issubset(set2)  # True

# Superset (does set1 contain all elements of set2?)
is_superset = set2.issuperset(set1)  # True

# Disjoint (do sets have no elements in common?)
are_disjoint = set1.isdisjoint({4, 5})  # True
```

## Common Use Cases

1. **Removing Duplicates**: Convert a list to a set and back to remove duplicates
   ```python
   list_with_duplicates = [1, 2, 2, 3, 3, 4]
   unique_list = list(set(list_with_duplicates))
   ```

2. **Membership Testing**: Sets provide fast O(1) membership testing
   ```python
   numbers = {1, 2, 3, 4, 5}
   if 3 in numbers:  # Fast membership test
       print("3 is in the set")
   ```

3. **Finding Unique Elements**: Useful for data cleaning and analysis
   ```python
   data = ['apple', 'banana', 'apple', 'cherry']
   unique_fruits = set(data)
   ```

## Performance Characteristics

- Membership testing: O(1)
- Adding elements: O(1)
- Removing elements: O(1)
- Union/Intersection: O(min(len(s), len(t)))

Sets are particularly useful when:
- You need to ensure elements are unique
- You need to perform set operations (union, intersection, etc.)
- You need fast membership testing
- You want to remove duplicates from a sequence

Remember that while sets are powerful, they can only contain immutable elements, and they don't maintain any specific order of elements.

# Python Dictionaries

A dictionary in Python is an unordered collection of key-value pairs. It is one of the most useful and widely used data structures in Python. Dictionaries are defined using curly braces `{}` with key-value pairs separated by commas.

## Creating Dictionaries

```python
# Empty dictionary
empty_dict = {}
empty_dict2 = dict()

# Dictionary with initial key-value pairs
person = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# Creating dictionary using dict() constructor
person2 = dict(name="Jane", age=25, city="London")
```

## Accessing Dictionary Elements

### 1. Using Square Brackets
```python
person = {"name": "John", "age": 30}
print(person["name"])  # Output: John

# Raises KeyError if key doesn't exist
# print(person["address"])  # KeyError
```

### 2. Using get() Method
```python
# get() with default value
age = person.get("age")  # Returns 30
address = person.get("address", "Not Found")  # Returns "Not Found"
```

### 3. Accessing Multiple Elements
```python
# Get all values
values = person.values()  # dict_values(['John', 30])

# Get all keys
keys = person.keys()  # dict_keys(['name', 'age'])

# Get all key-value pairs
items = person.items()  # dict_items([('name', 'John'), ('age', 30)])
```

## Modifying Dictionaries

### 1. Adding/Updating Elements
```python
person = {"name": "John"}

# Add new key-value pair
person["age"] = 30

# Update existing value
person["name"] = "John Smith"

# Update multiple key-value pairs
person.update({"age": 31, "city": "New York"})
```

### 2. Removing Elements
```python
# Remove specific key-value pair
del person["age"]

# Remove and return value
city = person.pop("city", "Not Found")  # Second argument is default value

# Remove and return last inserted item
last_item = person.popitem()

# Remove all items
person.clear()
```

## Dictionary Methods

```python
dict1 = {"a": 1, "b": 2}

# Copy dictionary
dict2 = dict1.copy()  # Creates a shallow copy

# Get length
length = len(dict1)  # Returns number of key-value pairs

# Check if key exists
has_key = "a" in dict1  # Returns True
```

## Iterating Over Dictionaries

```python
person = {"name": "John", "age": 30, "city": "New York"}

# Iterate over keys
for key in person.keys():
    print(key)

# Iterate over values
for value in person.values():
    print(value)

# Iterate over key-value pairs
for key, value in person.items():
    print(f"{key}: {value}")
```

## Dictionary Comprehension

```python
# Create dictionary using comprehension
squares = {x: x**2 for x in range(5)}
# Result: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

## Merging Dictionaries

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}

# Using dictionary unpacking (Python 3.5+)
merged_dict = {**dict1, **dict2}  # {"a": 1, "b": 3, "c": 4}

# Using update() method
dict1.update(dict2)  # dict1 is now {"a": 1, "b": 3, "c": 4}
```

## Common Use Cases

1. **Configuration Settings**
   ```python
   config = {
       "host": "localhost",
       "port": 8080,
       "debug": True
   }
   ```

2. **Caching/Memoization**
   ```python
   cache = {}
   def fibonacci(n):
       if n in cache:
           return cache[n]
       if n <= 1:
           return n
       cache[n] = fibonacci(n-1) + fibonacci(n-2)
       return cache[n]
   ```

3. **Counting Elements**
   ```python
   from collections import Counter
   words = ["apple", "banana", "apple", "cherry"]
   word_count = Counter(words)
   # Result: Counter({'apple': 2, 'banana': 1, 'cherry': 1})
   ```

## Performance Characteristics

- Access by key: O(1) average case
- Insertion/Deletion: O(1) average case
- Search by value: O(n)
- Space complexity: O(n)

Remember that:
- Dictionary keys must be immutable (strings, numbers, tuples)
- As of Python 3.7+, dictionaries maintain insertion order
- Dictionary values can be of any type
- Keys must be unique within a dictionary
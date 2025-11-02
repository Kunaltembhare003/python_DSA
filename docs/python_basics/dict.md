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
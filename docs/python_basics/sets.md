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


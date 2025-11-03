# Data Manipulation Interview Questions

### NumPy Questions
1. **What is NumPy and why is it used in data manipulation?**
   - NumPy is a library for the Python programming language that provides support for large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays. It is widely used in data manipulation because of its efficiency and speed in handling numerical data.
   ```python
   import numpy as np
   # Example of basic NumPy array operations
   arr = np.array([1, 2, 3, 4, 5])
   print(arr * 2)  # Output: [2 4 6 8 10]
   ```

2. **Explain the difference between a list and a NumPy array.**
   - A list is a built-in Python data structure that can hold a collection of items of different types, while a NumPy array is a homogeneous collection of items of the same type, which allows for more efficient storage and operations.
   ```python
   # Python list
   lst = [1, 'hello', 3.14]  # Can hold different types
   
   # NumPy array
   import numpy as np
   arr = np.array([1, 2, 3])  # All elements are same type (int)
   ```

3. **How do you create a NumPy array from a list?**
   - You can create a NumPy array from a list using the `np.array()` function.
   ```python
   import numpy as np
   
   # 1D array
   lst = [1, 2, 3, 4, 5]
   arr = np.array(lst)
   print(arr)  # Output: [1 2 3 4 5]
   
   # 2D array
   lst_2d = [[1, 2, 3], [4, 5, 6]]
   arr_2d = np.array(lst_2d)
   print(arr_2d)
   ```

4. **What are the advantages of using NumPy arrays over Python lists?**
   - NumPy arrays are more memory efficient, allow for faster computations, and provide a wide range of mathematical functions.
   ```python
   import numpy as np
   import time
   
   # Performance comparison
   # Python list operation
   lst = list(range(1000000))
   start = time.time()
   lst_squared = [x**2 for x in lst]
   print(f"List time: {time.time() - start}")
   
   # NumPy array operation
   arr = np.array(lst)
   start = time.time()
   arr_squared = arr**2
   print(f"NumPy time: {time.time() - start}")  # Much faster!
   ```

5. **How can you perform element-wise operations on NumPy arrays?**
   - Element-wise operations can be performed using standard arithmetic operators (+, -, *, /) directly on NumPy arrays.
   ```python
   import numpy as np
   
   arr1 = np.array([1, 2, 3])
   arr2 = np.array([4, 5, 6])
   
   # Element-wise operations
   print(arr1 + arr2)  # Output: [5 7 9]
   print(arr1 * arr2)  # Output: [4 10 18]
   print(arr1 ** 2)    # Output: [1 4 9]
   ```

6. **Explain broadcasting in NumPy.**
   - Broadcasting is a feature that allows NumPy to perform operations on arrays of different shapes by automatically expanding the smaller array to match the shape of the larger array.
   ```python
   import numpy as np
   
   # Broadcasting with scalar
   arr = np.array([[1, 2, 3],
                   [4, 5, 6]])
   scalar = 2
   print(arr * scalar)  # Broadcasts scalar to every element
   
   # Broadcasting with arrays
   row_vector = np.array([1, 2, 3])
   col_vector = np.array([[1],
                         [2]])
   print(arr + row_vector)  # Broadcasts row vector across rows
   print(arr + col_vector)  # Broadcasts column vector across columns
   ```

7. **How do you handle missing values in a NumPy array?**
   - You can handle missing values by using `np.nan` to represent them and functions like `np.nanmean()` to compute statistics while ignoring these values.
   ```python
   import numpy as np
   
   # Create array with missing values
   arr = np.array([1, 2, np.nan, 4, 5])
   
   # Calculate statistics ignoring nan values
   print(f"Mean (ignoring nan): {np.nanmean(arr)}")
   print(f"Sum (ignoring nan): {np.nansum(arr)}")
   
   # Find and replace nan values
   arr[np.isnan(arr)] = 0
   print(f"Array after replacing nan: {arr}")
   ```

8. **What is the purpose of the `reshape` function in NumPy?**
   - The `reshape` function is used to change the shape of an array without changing its data.
   ```python
   import numpy as np
   
   # Create a 1D array
   arr = np.array([1, 2, 3, 4, 5, 6])
   print(f"Original array: {arr}")
   
   # Reshape to 2x3 matrix
   matrix_2x3 = arr.reshape(2, 3)
   print(f"Reshaped to 2x3:\n{matrix_2x3}")
   
   # Reshape to 3x2 matrix
   matrix_3x2 = arr.reshape(3, 2)
   print(f"Reshaped to 3x2:\n{matrix_3x2}")
   
   # Using -1 to automatically calculate dimension
   matrix_auto = arr.reshape(-1, 2)  # Automatically calculates rows
   print(f"Auto-reshaped:\n{matrix_auto}")
   ```

9. **How can you concatenate two NumPy arrays?**
   - You can concatenate two NumPy arrays using the `np.concatenate()` function.
   ```python
   import numpy as np
   
   # 1D arrays
   arr1 = np.array([1, 2, 3])
   arr2 = np.array([4, 5, 6])
   
   # Concatenate horizontally
   horizontal = np.concatenate((arr1, arr2))
   print(f"Horizontal concatenation: {horizontal}")
   
   # 2D arrays
   a = np.array([[1, 2], [3, 4]])
   b = np.array([[5, 6], [7, 8]])
   
   # Concatenate vertically (along rows)
   vertical = np.concatenate((a, b), axis=0)
   print(f"Vertical concatenation:\n{vertical}")
   
   # Concatenate horizontally (along columns)
   horizontal_2d = np.concatenate((a, b), axis=1)
   print(f"Horizontal concatenation 2D:\n{horizontal_2d}")
   ```

10. **Explain the difference between `np.arange` and `np.linspace`.**
    - `np.arange()` generates values within a specified range with a specified step size, while `np.linspace()` generates a specified number of evenly spaced values between two endpoints.
    ```python
    import numpy as np
    
    # arange: start, stop, step
    arr1 = np.arange(0, 10, 2)
    print(f"arange with step 2: {arr1}")  # [0 2 4 6 8]
    
    # linspace: start, stop, num_points
    arr2 = np.linspace(0, 10, 5)
    print(f"linspace with 5 points: {arr2}")  # [0. 2.5 5. 7.5 10.]
    
    # Comparison with floating point steps
    arr3 = np.arange(0, 1, 0.3)  # Might have floating point issues
    print(f"arange with float step: {arr3}")
    
    arr4 = np.linspace(0, 1, 4)  # Precise number of points
    print(f"linspace with 4 points: {arr4}")
    ```

11. **How do you calculate the mean, median, and standard deviation of a NumPy array?**
    - You can use `np.mean()`, `np.median()`, and `np.std()` functions to calculate these statistics.
    ```python
    import numpy as np
    
    # Create sample array
    arr = np.array([1, 2, 3, 4, 5])
    print(f"Array: {arr}")
    
    # Basic statistics
    print(f"Mean: {np.mean(arr)}")
    print(f"Median: {np.median(arr)}")
    print(f"Standard Deviation: {np.std(arr)}")
    
    # 2D array example
    arr_2d = np.array([[1, 2, 3],
                       [4, 5, 6]])
    print(f"\n2D Array:\n{arr_2d}")
    
    # Statistics along different axes
    print(f"Mean of each column: {np.mean(arr_2d, axis=0)}")
    print(f"Mean of each row: {np.mean(arr_2d, axis=1)}")
    print(f"Overall mean: {np.mean(arr_2d)}")
    ```

12. **What is the purpose of the `np.where` function?**
    - The `np.where` function returns the indices of elements in an array that satisfy a given condition.
    ```python
    import numpy as np
    
    # Create a sample array
    arr = np.array([1, 2, 3, 4, 5])
    
    # Find indices where elements are greater than 3
    indices = np.where(arr > 3)
    print(f"Original array: {arr}")
    print(f"Indices where elements > 3: {indices[0]}")
    
    # Use where for conditional assignment
    result = np.where(arr > 3, arr * 2, arr)
    print(f"Array with elements > 3 doubled: {result}")
    
    # 2D array example
    arr_2d = np.array([[1, 2, 3],
                       [4, 5, 6]])
    print(f"\n2D array:\n{arr_2d}")
    
    # Find indices in 2D array
    rows, cols = np.where(arr_2d > 3)
    print(f"Positions where elements > 3: rows={rows}, cols={cols}")
    ```

13. **How can you sort a NumPy array?**
    - You can sort a NumPy array using the `np.sort()` function.
    ```python
    import numpy as np
    
    # 1D array sorting
    arr = np.array([3, 1, 4, 1, 5, 9, 2, 6])
    print(f"Original array: {arr}")
    print(f"Sorted array: {np.sort(arr)}")
    
    # 2D array sorting
    arr_2d = np.array([[3, 1, 4],
                       [1, 5, 9],
                       [2, 6, 5]])
    print(f"\nOriginal 2D array:\n{arr_2d}")
    
    # Sort along rows (axis=1)
    print(f"Sorted along rows:\n{np.sort(arr_2d, axis=1)}")
    
    # Sort along columns (axis=0)
    print(f"Sorted along columns:\n{np.sort(arr_2d, axis=0)}")
    
    # Get sorted indices
    indices = np.argsort(arr)
    print(f"\nIndices that would sort the array: {indices}")
    ```

14. **Explain how to use boolean indexing with NumPy arrays.**
    - Boolean indexing allows you to select elements from an array based on a condition, using a boolean array of the same shape.
    ```python
    import numpy as np
    
    # Create a sample array
    arr = np.array([1, 2, 3, 4, 5])
    
    # Create boolean mask
    mask = arr > 3
    print(f"Original array: {arr}")
    print(f"Boolean mask: {mask}")
    
    # Apply mask to array
    filtered = arr[mask]
    print(f"Filtered array (elements > 3): {filtered}")
    
    # Multiple conditions
    complex_mask = (arr > 2) & (arr < 5)
    print(f"Complex filtered (2 < elements < 5): {arr[complex_mask]}")
    
    # 2D array example
    arr_2d = np.array([[1, 2, 3],
                       [4, 5, 6]])
    print(f"\n2D array:\n{arr_2d}")
    
    # Filter rows based on condition
    row_mask = np.any(arr_2d > 4, axis=1)
    print(f"Rows containing elements > 4:\n{arr_2d[row_mask]}")
    ```

15. **How do you save and load NumPy arrays to and from files?**
    - You can save NumPy arrays using `np.save()` and load them using `np.load()`.
    ```python
    import numpy as np
    
    # Create sample arrays
    arr1 = np.array([1, 2, 3, 4, 5])
    arr2 = np.array([[1, 2, 3], [4, 5, 6]])
    
    # Save arrays to files
    np.save('array1.npy', arr1)
    np.save('array2.npy', arr2)
    
    # Load arrays from files
    loaded_arr1 = np.load('array1.npy')
    loaded_arr2 = np.load('array2.npy')
    
    print(f"Loaded 1D array: {loaded_arr1}")
    print(f"Loaded 2D array:\n{loaded_arr2}")
    
    # Save multiple arrays in a single file
    np.savez('arrays.npz', a=arr1, b=arr2)
    
    # Load multiple arrays
    loaded = np.load('arrays.npz')
    print(f"\nLoaded from npz:")
    print(f"Array 'a': {loaded['a']}")
    print(f"Array 'b':\n{loaded['b']}")
    ```

16. **What is the difference between `np.copy` and `np.view`?**
    - `np.copy` creates a new array that is a copy of the original, while `np.view` creates a new view of the same data without copying it.
    ```python
    import numpy as np
    
    # Create original array
    arr = np.array([1, 2, 3, 4, 5])
    
    # Create a view
    view = arr.view()
    
    # Create a copy
    copy = arr.copy()
    
    print(f"Original array: {arr}")
    print(f"View: {view}")
    print(f"Copy: {copy}")
    
    # Modify original array
    arr[0] = 10
    print(f"\nAfter modifying original:")
    print(f"Original array: {arr}")
    print(f"View (also changed): {view}")
    print(f"Copy (unchanged): {copy}")
    
    # Memory location
    print(f"\nMemory address:")
    print(f"Original: {arr.__array_interface__['data'][0]}")
    print(f"View: {view.__array_interface__['data'][0]}")
    print(f"Copy: {copy.__array_interface__['data'][0]}")
    ```

17. **How can you find unique elements in a NumPy array?**
    - You can find unique elements using the `np.unique()` function.
    ```python
    import numpy as np
    
    # Create array with duplicate values
    arr = np.array([1, 2, 2, 3, 3, 3, 4, 5, 5])
    
    # Get unique values
    unique = np.unique(arr)
    print(f"Original array: {arr}")
    print(f"Unique values: {unique}")
    
    # Get unique values and their counts
    values, counts = np.unique(arr, return_counts=True)
    print(f"\nValues: {values}")
    print(f"Counts: {counts}")
    
    # 2D array example
    arr_2d = np.array([[1, 2, 3],
                       [3, 2, 1],
                       [2, 3, 1]])
    print(f"\n2D array:\n{arr_2d}")
    
    # Get unique values from 2D array
    unique_2d = np.unique(arr_2d)
    print(f"Unique values in 2D array: {unique_2d}")
    ```

18. **Explain the concept of a structured array in NumPy.**
    - A structured array allows you to create arrays with different data types for each column, similar to a database table.
    ```python
    import numpy as np
    
    # Define structured array data type
    dt = np.dtype([('name', 'U20'),     # Unicode string, max length 20
                   ('age', 'i4'),        # 32-bit integer
                   ('salary', 'f8')])    # 64-bit float
    
    # Create structured array
    employees = np.array([
        ('John Doe', 35, 75000.00),
        ('Jane Smith', 28, 65000.00),
        ('Bob Johnson', 42, 85000.00)
    ], dtype=dt)
    
    print("Employee Records:")
    print(employees)
    
    # Access columns
    print(f"\nNames: {employees['name']}")
    print(f"Ages: {employees['age']}")
    print(f"Salaries: {employees['salary']}")
    
    # Access a single record
    print(f"\nFirst employee: {employees[0]}")
    
    # Filter data
    high_salary = employees[employees['salary'] > 70000]
    print(f"\nEmployees with high salary:\n{high_salary}")
    ```

19. **How do you perform matrix multiplication using NumPy?**
    - You can perform matrix multiplication using the `np.dot()` function or the `@` operator.
    ```python
    import numpy as np
    
    # Create two matrices
    A = np.array([[1, 2],
                  [3, 4]])
    B = np.array([[5, 6],
                  [7, 8]])
    
    print(f"Matrix A:\n{A}")
    print(f"\nMatrix B:\n{B}")
    
    # Matrix multiplication using dot
    C1 = np.dot(A, B)
    print(f"\nMatrix multiplication using dot:\n{C1}")
    
    # Matrix multiplication using @ operator
    C2 = A @ B
    print(f"\nMatrix multiplication using @:\n{C2}")
    
    # Compare with element-wise multiplication
    C3 = A * B
    print(f"\nElement-wise multiplication:\n{C3}")
    
    # Matrix-vector multiplication
    v = np.array([1, 2])
    result = A @ v
    print(f"\nMatrix-vector multiplication:\n{result}")
    ```

20. **What are some common performance optimizations when using NumPy?**
    - Common optimizations include using vectorized operations, avoiding loops, and using in-place operations when possible.
    ```python
    import numpy as np
    import time
    
    # Example 1: Vectorization vs loops
    arr = np.random.rand(1000000)
    
    # Using loop (slow)
    start = time.time()
    result1 = []
    for x in arr:
        result1.append(x * 2 + 1)
    print(f"Loop time: {time.time() - start}")
    
    # Using vectorization (fast)
    start = time.time()
    result2 = arr * 2 + 1
    print(f"Vectorized time: {time.time() - start}")
    
    # Example 2: In-place operations
    start = time.time()
    arr *= 2  # In-place multiplication
    print(f"In-place operation time: {time.time() - start}")
    
    # Example 3: Pre-allocation vs append
    start = time.time()
    result = np.zeros(1000000)  # Pre-allocate
    result += arr
    print(f"Pre-allocation time: {time.time() - start}")
    
    # Example 4: Using built-in functions
    start = time.time()
    mean = np.mean(arr)  # Using built-in function
    print(f"Built-in function time: {time.time() - start}")
    ```

### Pandas Questions
1. **What is Pandas and how does it differ from NumPy?**
   - Pandas is a data manipulation and analysis library for Python that provides data structures like Series and DataFrames. It is built on top of NumPy and offers more functionality for handling labeled data.
   ```python
   import numpy as np
   import pandas as pd
   
   # NumPy array (homogeneous data type)
   np_arr = np.array([1, 2, 3])
   print("NumPy array:", np_arr)
   
   # Pandas Series (can have labels)
   series = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
   print("\nPandas Series:")
   print(series)
   
   # Pandas DataFrame (can have multiple columns with different types)
   df = pd.DataFrame({
       'numbers': [1, 2, 3],
       'letters': ['a', 'b', 'c'],
       'floats': [1.1, 2.2, 3.3]
   })
   print("\nPandas DataFrame:")
   print(df)
   
   # Type handling
   mixed_df = pd.DataFrame({
       'numbers': [1, 2, 3],
       'text': ['hello', 'world', '!'],
       'dates': pd.date_range('2023-01-01', periods=3)
   })
   print("\nMixed types in DataFrame:")
   print(mixed_df.dtypes)
   ```

2. **Explain the difference between a Series and a DataFrame in Pandas.**
   - A Series is a one-dimensional labeled array, while a DataFrame is a two-dimensional labeled data structure with columns of potentially different types.

3. **How do you create a DataFrame from a dictionary?**
   - You can create a DataFrame from a dictionary using `pd.DataFrame()`.

4. **What are the different ways to read data into a Pandas DataFrame?**
   - You can read data from various sources like CSV files, Excel files, SQL databases, and JSON using functions like `pd.read_csv()`, `pd.read_excel()`, etc.

5. **How can you handle missing data in a DataFrame?**
   - You can handle missing data using methods like `dropna()` to remove missing values or `fillna()` to fill them with a specified value.

6. **Explain how to filter rows in a DataFrame based on a condition.**
   - You can filter rows by using boolean indexing, e.g., `df[df['column'] > value]`.

7. **How do you group data in a DataFrame and perform aggregation?**
   - You can group data using the `groupby()` method and then apply aggregation functions like `sum()`, `mean()`, etc.

8. **What is the purpose of the `apply` function in Pandas?**
   - The `apply` function allows you to apply a function along an axis of the DataFrame (rows or columns).

9. **How can you merge two DataFrames?**
   - You can merge two DataFrames using the `merge()` function.

10. **Explain the difference between `concat` and `merge` in Pandas.**
    - `concat` is used to concatenate DataFrames along a particular axis, while `merge` is used to combine DataFrames based on common columns or indices.

11. **How do you change the index of a DataFrame?**
    - You can change the index using the `set_index()` method.

12. **What is the purpose of the `pivot_table` function?**
    - The `pivot_table` function is used to create a spreadsheet-style pivot table from a DataFrame.

13. **How can you sort a DataFrame by multiple columns?**
    - You can sort a DataFrame by multiple columns using the `sort_values()` method with a list of column names.

14. **Explain how to use the `loc` and `iloc` indexers in Pandas.**
    - `loc` is used for label-based indexing, while `iloc` is used for position-based indexing.

15. **How do you convert a DataFrame to a NumPy array?**
    - You can convert a DataFrame to a NumPy array using the `to_numpy()` method.
## Introduction

Python is a versatile, high-level programming language known for its simplicity and readability. This paper explores various aspects of Python programming through a series of examples, covering string manipulations, data structures, and file operations.

## Python Basics

### String Manipulation

1. **Basic Operations**:
    ```python
    msg = "Hello world"
    print("Hello world")
    print(r'\name')  # raw string
    print('string'[1:-4])  # slicing strings
    ```

2. **Raw Strings**:
    - `r'\name'` treats backslashes as literal characters, preventing escape sequences from being processed.

3. **Slicing**:
    - `'string'[1:-4]` extracts a substring from index 1 to the fourth-last index.

### Lists

1. **Creation and Operations**:
    ```python
    array = [1, 2, 3, 4, 5]
    print(array)
    ```
   
2. **Concatenation**:
    ```python
    fruits = ['apple', 'banana', 'carrot']
    print(array + fruits)  # Concatenates two lists
    print(array, fruits)   # Prints two lists separately
    print([array, fruits])  # Nested list
    ```

3. **Modifications**:
    ```python
    array.append(34)           # Adds 34 to the end
    array.insert(0, 4)         # Inserts 4 at index 0
    array.remove(4)            # Removes the first occurrence of 4
    array.count(4)             # Counts occurrences of 4
    array.extend([1, 2, 3])    # Extends list with another list
    print(array.pop())         # Pops the last element
    print(array.pop(0))        # Pops the first element
    del array[3:]              # Deletes elements from index 3 to end
    array.reverse()           # Reverses the list
    array.sort()              # Sorts the list
    print(array.index(3))     # Finds index of element 3
    array.clear()             # Empties the list
    ```

### Tuples

1. **Characteristics**:
    ```python
    tup = (1, 2, 3, 3)
    print(tup[1])             # Accesses tuple elements
    print(tup)
    print(type(tup))          # <class 'tuple'>
    print(len(tup))           # Length of the tuple
    ```
    - Tuples are immutable and their length can be obtained with `len()`.

### Sets

1. **Properties and Operations**:
    ```python
    sets = {1, 2, 3}
    sets = {4, 3, 2, 1}       # Sets automatically sort and remove duplicates
    sets = {"apple", "banana", "addle", "axe", "apple"}  # Ignored duplicate values
    print(sets)
    ```
    - Sets do not support indexing and automatically handle duplicates.

### Dictionaries

1. **Creation and Access**:
    ```python
    data = {"name": "buffalo", 1: "Banana"}
    print(data)
    print(data["name"])       # Access value by key
    print(data[1])
    print(data.get(1))        # Safely access value by key
    print(data.get(2))        # Returns None if key doesn't exist
    print(data.get(2, "Not Found"))  # Returns default value if key not found
    ```

2. **Dictionary Comprehension**:
    ```python
    keys = ['C++', 'Python', 'Java']
    values = ['Harsh', 'Kiran', 'Vikram']
    dictionary = dict(zip(keys, values))
    print(dictionary)
    ```
    - Creates a dictionary by zipping two lists of keys and values.

## Memory Management

1. **Memory Addresses**:
    ```python
    a = 10
    b = a
    print(id(a), id(b))      # b points to the same memory address as a
    b = 10
    print(id(a), id(b))      # Both a and b point to the same address
    a = 5
    print(a, b)
    print(id(a), id(b))      # Different addresses after reassignment
    ```

## Data Types

1. **Basic Types**:
    ```python
    print(None)               # NoneType
    print(type(None))         # <class 'NoneType'>
    print(type(2))            # <class 'int'>
    print(type(2.14))         # <class 'float'>
    print(type(True))         # <class 'bool'>
    print(type(6+9j))         # <class 'complex'>
    ```

2. **Type Casting**:
    ```python
    a = 5.6
    b = int(a)
    print(b, type(b))
    print(complex(1))        # Converts integer to complex
    print(float(b))          # Converts integer to float
    print(int(True))         # Converts boolean to integer
    print(int(False))        # Converts boolean to integer
    ```

3. **Range Function**:
    ```python
    print(type(range(10)))   # <class 'range'>
    print(list(range(10)))   # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```

## Number Formatting

1. **Base Conversion**:
    ```python
    print(bin(25))           # Decimal to binary
    print(oct(25))           # Decimal to octal
    print(hex(25))           # Decimal to hexadecimal
    print(0b10101)           # Binary to decimal
    print(0o31)              # Octal to decimal
    print(0x19)              # Hexadecimal to decimal
    ```

## Bitwise Operators

1. **Operations**:
    ```python
    print(~12)               # Bitwise NOT
    print(bin(~2))
    print(12 & 13)           # Bitwise AND
    print(12 | 13)           # Bitwise OR
    print(12 ^ 13)           # Bitwise XOR
    print(10 << 2)          # Bitwise left shift
    print(10 >> 2)          # Bitwise right shift
    ```

## Mathematical Functions

1. **Using `math` Module**:
    ```python
    import math
    print(math.sqrt(5))      # Square root
    print(math.ceil(2.323))  # Ceiling value
    print(math.floor(2.345)) # Floor value
    print(round(2.34, 0))    # Rounded to nearest integer
    print(round(2.346, 2))   # Rounded to 2 decimal places
    print(math.pow(2, 2))    # Power function
    print(2 ** 2)            # Exponentiation operator
    print(math.pi)           # Value of π
    print(math.e)            # Value of e
    ```

## Swapping Variables

1. **Methods**:
    ```python
    a = 10
    b = 20
    a, b = b, a              # Tuple unpacking for swapping
    a = a + b
    b = a - b
    a = a - b                # Alternative method
    ```

## User Input and File Handling

1. **Getting Input**:
    ```python
    import sys
    # x = sys.argv[1]
    # y = sys.argv[2]
    # print(sys.argv[0], x, y)
    ```

2. **Reading Files**:
    ```python
    with open('data/matches.csv', "r") as file:
        print(file.readlines()[-1])  # Reads the last line of the file
    ```


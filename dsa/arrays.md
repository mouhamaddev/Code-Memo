### Arrays

An array is a linear data structure that stores elements in contiguous memory locations. It allows **random access** to elements using an index. Arrays are fixed in size (in low-level languages), but Python’s lists provide dynamic resizing.

#### Types of Arrays

1. **Static Array**: Fixed-size arrays using `array` module or third-party packages like NumPy.
2. **Dynamic Array**: Python’s built-in `list` type, which resizes automatically.

#### Basic Operations

**1. Insertion**

- **At the Beginning**

```python
arr.insert(0, 10)  # Insert 10 at index 0
```

- **At the End**

```python
arr.append(20)  # Append 20 to the end
```

- **At Any Position**

```python
arr.insert(2, 15)  # Insert 15 at index 2
```

**2. Deletion**

- **From the Beginning**

```python
arr.pop(0)  # Remove element at index 0
```

- **From the End**

```python
arr.pop()  # Removes and returns the last element
```

- **Specific Value**

```python
arr.remove(15)  # Removes the first occurrence of 15
```

**3. Access**

```python
print(arr[1])  # Access element at index 1
```

**4. Update**

```python
arr[2] = 99  # Update the element at index 2 to 99
```

**5. Traversal**

```python
for item in arr:
    print(item, end=' ')
```

**6. Searching**

- **Linear Search**

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

**7. Slicing**

```python
sub_array = arr[1:4]  # From index 1 to 3
```

**8. Length**

```python
n = len(arr)  # Number of elements
```

**9. Sorting**

```python
arr.sort()  # In-place sort
sorted_arr = sorted(arr)  # Returns new sorted list
```

**10. Reversing**

```python
arr.reverse()  # In-place reverse
rev_arr = arr[::-1]  # Sliced reverse
```

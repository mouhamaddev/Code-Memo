### HashSet

A **HashSet** is a data structure that stores **unique elements only** and offers **O(1)** average time complexity for insertion, deletion, and lookup.
It’s backed by a **hash table** just like a Hashmap, but only stores **keys**, no values.

It's implemented using the built-in `set` type.

### Initialization

```python
# Empty set
s = set()

# With values
s = {1, 2, 3}
```

### Basic Operations

#### 1. Insert (Add Element)

```python
s.add(4)        # Adds 4
s.add(2)        # Already exists, no effect
```

#### 2. Remove Element

```python
s.remove(2)     # Removes 2 (raises KeyError if not found)
s.discard(5)    # Safe remove (no error if 5 not present)
```

#### 3. Check Existence

```python
if 3 in s:
    print("Exists")
```

#### 4. Traversal

```python
for item in s:
    print(item)
```

#### 5. Size

```python
len(s)  # Number of unique elements
```

#### 6. Clear Set

```python
s.clear()
```

### Set Operations

Useful for solving problems involving **duplicates**, **intersections**, or **differences**.

#### 1. Union (OR)

```python
a = {1, 2, 3}
b = {3, 4, 5}
a | b      # {1, 2, 3, 4, 5}
```

#### 2. Intersection (AND)

```python
a & b      # {3}
```

#### 3. Difference (A - B)

```python
a - b      # {1, 2}
```

#### 4. Symmetric Difference (A XOR B)

```python
a ^ b      # {1, 2, 4, 5}
```

### Use Cases

- Removing duplicates
- Checking membership fast
- Performing math set operations
- Solving problems like:

  - "Contains Duplicate"
  - "Intersection of Two Arrays"
  - "First Missing Positive"

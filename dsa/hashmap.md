### Hashmaps (Dictionaries in Python)

A **Hashmap** (also called a **Hash Table**) is a data structure that stores key-value pairs.
It uses a **hash function** to map keys to indices in an internal array, allowing **average O(1) time complexity** for insertion, deletion, and lookup.

In Python, hashmaps are implemented using the built-in `dict` type.

### Initialization

```python
# Empty hashmap
hm = {}

# With values
hm = {"apple": 3, "banana": 5}
```

### Basic Operations

#### 1. Insert / Update

```python
hm["grape"] = 7        # Insert
hm["apple"] = 10       # Update
```

#### 2. Access / Get Value

```python
print(hm["apple"])     # Raises KeyError if not found
print(hm.get("apple")) # Returns None if not found
print(hm.get("kiwi", 0))  # Default value if key doesn't exist
```

#### 3. Check Existence

```python
"banana" in hm         # True
"kiwi" in hm           # False
```

#### 4. Delete

```python
del hm["banana"]       # Raises KeyError if not found
hm.pop("grape")        # Returns value and removes key
hm.pop("kiwi", None)   # Safe pop with default
```

#### 5. Traversal

```python
# Keys
for key in hm:
    print(key)

# Values
for value in hm.values():
    print(value)

# Key-Value pairs
for key, value in hm.items():
    print(key, value)
```

#### 6. Size

```python
len(hm)  # Number of key-value pairs
```

#### 7. Clear All Entries

```python
hm.clear()
```

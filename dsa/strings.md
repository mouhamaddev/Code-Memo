### Strings

A string is a **sequence of characters** enclosed in quotes. Strings are **immutable**, meaning once created, they cannot be changed. Strings support indexing, slicing, and a rich set of built-in methods for manipulation.

#### Initialization

```python
s = "hello"
s2 = 'world'
s3 = """multi
line"""
```

#### Basic Operations

**1. Access Characters**

```python
print(s[0])     # 'h'
print(s[-1])    # 'o' (last character)
```

**2. Slicing**

```python
print(s[1:4])   # 'ell'
print(s[:3])    # 'hel'
print(s[::-1])  # 'olleh' (reverse string)
```

**3. Concatenation**

```python
s = "hello"
s += " world"
print(s)  # 'hello world'
```

**4. Repetition**

```python
print("ha" * 3)  # 'hahaha'
```

**5. Length**

```python
print(len(s))  # Number of characters
```

**6. Iteration**

```python
for char in s:
    print(char)
```

**7. Search**

- **Check substring**

```python
"ell" in s  # True
```

- **Find index**

```python
s.find("l")       # Returns 2 (first occurrence)
s.rfind("l")      # Returns 3 (last occurrence)
s.index("l")      # Like find(), but raises error if not found
```

**8. Modification (via new string)**

- **Replace**

```python
s = s.replace("world", "there")  # 'hello there'
```

- **Upper/Lower**

```python
s.upper()     # 'HELLO THERE'
s.lower()     # 'hello there'
```

- **Strip**

```python
"  hello  ".strip()   # 'hello'
"hello\n".rstrip()    # 'hello'
```

**9. Splitting and Joining**

```python
words = s.split()       # ['hello', 'there']
joined = "-".join(words)  # 'hello-there'
```

**10. Formatting**

- **f-Strings**

```python
name = "Ortie"
f"Hello, {name}!"  # 'Hello, Ortie!'
```

- **Old style**

```python
"Hello, %s!" % name
```

- **`str.format()`**

```python
"Hello, {}!".format(name)
```

**11. String Comparison**

```python
"apple" < "banana"   # True (lexicographical)
```

**12. Useful String Methods**

```python
s.isalpha()     # All letters?
s.isdigit()     # All digits?
s.startswith("he")  # True
s.endswith("e")     # True
```

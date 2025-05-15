### Trie (Prefix Tree)

A **Trie** is a tree-like data structure used to efficiently store and retrieve keys in a dataset of strings.
It is commonly used for **autocomplete**, **spell checking**, and **prefix matching**.

Each node typically represents a **single character** of a word, and paths from the root to a node spell out a prefix or full word.

### Trie Node Structure

```python
class TrieNode:
    def __init__(self):
        self.children = {}  # Maps char -> TrieNode
        self.is_end_of_word = False
```

### Trie Class

```python
class Trie:
    def __init__(self):
        self.root = TrieNode()
```

### Basic Operations

#### 1. Insert a Word

```python
def insert(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            node.children[char] = TrieNode()
        node = node.children[char]
    node.is_end_of_word = True
```

Usage:

```python
trie = Trie()
trie.insert("apple")
trie.insert("app")
```

#### 2. Search for a Word

```python
def search(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            return False
        node = node.children[char]
    return node.is_end_of_word
```

#### 3. Check if Prefix Exists

```python
def starts_with(self, prefix):
    node = self.root
    for char in prefix:
        if char not in node.children:
            return False
        node = node.children[char]
    return True
```

#### 4. Autocomplete Suggestions (Words Starting With Prefix)

```python
def get_words_with_prefix(self, prefix):
    def dfs(node, path, result):
        if node.is_end_of_word:
            result.append("".join(path))
        for char, next_node in node.children.items():
            dfs(next_node, path + [char], result)

    node = self.root
    for char in prefix:
        if char not in node.children:
            return []
        node = node.children[char]

    result = []
    dfs(node, list(prefix), result)
    return result
```

Example:

```python
trie = Trie()
words = ["apple", "app", "apt", "bat", "bad"]
for word in words:
    trie.insert(word)

print(trie.get_words_with_prefix("ap"))  # ['apple', 'app', 'apt']
```
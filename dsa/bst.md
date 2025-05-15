### Binary Search Trees (BST)

A **Binary Search Tree** is a type of binary tree where each node follows the **BST property**:

* Left subtree contains values **less than** the node.
* Right subtree contains values **greater than** the node.
* No duplicates (by default).

This structure allows **efficient searching, insertion, and deletion** in `O(log n)` time on average (if balanced).

#### BST Node Structure

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None
```

#### BST Class

```python
class BST:
    def __init__(self):
        self.root = None
```

### Basic Operations

#### 1. Insertion

```python
def insert(self, root, key):
    if root is None:
        return Node(key)
    if key < root.data:
        root.left = self.insert(root.left, key)
    else:
        root.right = self.insert(root.right, key)
    return root
```

Usage:

```python
bst = BST()
bst.root = bst.insert(bst.root, 10)
bst.insert(bst.root, 5)
bst.insert(bst.root, 15)
```

#### 2. Search

```python
def search(self, root, key):
    if not root:
        return False
    if root.data == key:
        return True
    elif key < root.data:
        return self.search(root.left, key)
    else:
        return self.search(root.right, key)
```

#### 3. Deletion

```python
def delete(self, root, key):
    if not root:
        return None
    if key < root.data:
        root.left = self.delete(root.left, key)
    elif key > root.data:
        root.right = self.delete(root.right, key)
    else:
        # Node found
        if not root.left:
            return root.right
        elif not root.right:
            return root.left
        # Node with 2 children
        min_larger_node = self.get_min(root.right)
        root.data = min_larger_node.data
        root.right = self.delete(root.right, min_larger_node.data)
    return root

def get_min(self, root):
    while root.left:
        root = root.left
    return root
```

#### 4. Traversals

Same as Binary Tree:

* `inorder()` will return values **in sorted order**.

```python
def inorder(self, root):
    if root:
        self.inorder(root.left)
        print(root.data, end=' ')
        self.inorder(root.right)
```

#### 5. Min / Max Value

```python
def get_min(self, root):
    while root.left:
        root = root.left
    return root.data

def get_max(self, root):
    while root.right:
        root = root.right
    return root.data
```

#### 6. Validate BST

```python
def is_valid_bst(self, root, low=float('-inf'), high=float('inf')):
    if not root:
        return True
    if not (low < root.data < high):
        return False
    return (self.is_valid_bst(root.left, low, root.data) and
            self.is_valid_bst(root.right, root.data, high))
```
### AVL Trees

An **AVL Tree** is a **self-balancing Binary Search Tree** where the difference in height between the left and right subtrees (called the **balance factor**) is **at most 1** for every node.
If this condition is violated after insertion or deletion, the tree **performs rotations** to rebalance itself.

#### AVL Node Structure

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None
        self.height = 1  # New node is initially at height 1
```

#### AVL Tree Class

```python
class AVLTree:
    def __init__(self):
        self.root = None
```

### Key Helper Functions

#### 1. Get Height

```python
def get_height(self, node):
    if not node:
        return 0
    return node.height
```

#### 2. Get Balance Factor

```python
def get_balance(self, node):
    if not node:
        return 0
    return self.get_height(node.left) - self.get_height(node.right)
```

#### 3. Right Rotate

```python
def right_rotate(self, z):
    y = z.left
    T3 = y.right

    # Perform rotation
    y.right = z
    z.left = T3

    # Update heights
    z.height = 1 + max(self.get_height(z.left), self.get_height(z.right))
    y.height = 1 + max(self.get_height(y.left), self.get_height(y.right))

    return y  # New root
```

#### 4. Left Rotate

```python
def left_rotate(self, z):
    y = z.right
    T2 = y.left

    # Perform rotation
    y.left = z
    z.right = T2

    # Update heights
    z.height = 1 + max(self.get_height(z.left), self.get_height(z.right))
    y.height = 1 + max(self.get_height(y.left), self.get_height(y.right))

    return y  # New root
```

### Insertion with Balancing

```python
def insert(self, node, key):
    if not node:
        return Node(key)

    # Normal BST insert
    if key < node.data:
        node.left = self.insert(node.left, key)
    else:
        node.right = self.insert(node.right, key)

    # Update height
    node.height = 1 + max(self.get_height(node.left), self.get_height(node.right))

    # Check balance
    balance = self.get_balance(node)

    # Rebalance cases
    # Case 1 - Left Left
    if balance > 1 and key < node.left.data:
        return self.right_rotate(node)

    # Case 2 - Right Right
    if balance < -1 and key > node.right.data:
        return self.left_rotate(node)

    # Case 3 - Left Right
    if balance > 1 and key > node.left.data:
        node.left = self.left_rotate(node.left)
        return self.right_rotate(node)

    # Case 4 - Right Left
    if balance < -1 and key < node.right.data:
        node.right = self.right_rotate(node.right)
        return self.left_rotate(node)

    return node
```

Usage:

```python
avl = AVLTree()
avl.root = avl.insert(avl.root, 10)
avl.root = avl.insert(avl.root, 20)
avl.root = avl.insert(avl.root, 30)  # Triggers left rotation
```

### Inorder Traversal (Sorted Output)

```python
def inorder(self, root):
    if root:
        self.inorder(root.left)
        print(root.data, end=' ')
        self.inorder(root.right)
```

### Binary Trees

A **Binary Tree** is a hierarchical data structure in which each node has **at most two children**, commonly referred to as the **left** and **right** child. It is the foundation for more complex trees like Binary Search Trees (BSTs), Heaps, and AVL Trees.

#### Structure of a Binary Tree Node

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None
```

#### Binary Tree Class (with root)

```python
class BinaryTree:
    def __init__(self):
        self.root = None
```

### Basic Operations

#### 1. Insertion (Manual)

```python
tree = BinaryTree()
tree.root = Node(1)
tree.root.left = Node(2)
tree.root.right = Node(3)
tree.root.left.left = Node(4)
```

> For dynamic/level-wise insertion, you can use a queue (BFS logic).

#### 2. Traversals

Traversal means visiting all nodes in a specific order.

**Inorder (Left → Root → Right)**

```python
def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=' ')
        inorder(root.right)
```

**Preorder (Root → Left → Right)**

```python
def preorder(root):
    if root:
        print(root.data, end=' ')
        preorder(root.left)
        preorder(root.right)
```

**Postorder (Left → Right → Root)**

```python
def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=' ')
```

**Level Order (Breadth-First Search)**

```python
from collections import deque

def level_order(root):
    if not root:
        return
    queue = deque([root])
    while queue:
        node = queue.popleft()
        print(node.data, end=' ')
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
```

#### 3. Height of Tree

```python
def height(root):
    if not root:
        return 0
    return 1 + max(height(root.left), height(root.right))
```

#### 4. Count Nodes / Sum of Nodes

```python
def count_nodes(root):
    if not root:
        return 0
    return 1 + count_nodes(root.left) + count_nodes(root.right)

def sum_nodes(root):
    if not root:
        return 0
    return root.data + sum_nodes(root.left) + sum_nodes(root.right)
```

#### 5. Search for Value

```python
def search(root, value):
    if not root:
        return False
    if root.data == value:
        return True
    return search(root.left, value) or search(root.right, value)
```

#### 6. Print All Leaf Nodes

```python
def print_leaf_nodes(root):
    if root:
        if not root.left and not root.right:
            print(root.data, end=' ')
        print_leaf_nodes(root.left)
        print_leaf_nodes(root.right)
```
### N-ary Trees

An **N-ary Tree** is a tree data structure where each node can have **at most N children**, as opposed to binary trees where nodes have at most 2 children.
Used in scenarios like representing **file systems**, **organization charts**, and **XML/HTML parsing**.

### N-ary Tree Node Structure

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.children = []
```

### N-ary Tree Class

```python
class NaryTree:
    def __init__(self):
        self.root = None
```

### Basic Operations

#### 1. Insert (Manual Construction)

```python
tree = NaryTree()
tree.root = Node(1)

child1 = Node(2)
child2 = Node(3)
child3 = Node(4)

tree.root.children.extend([child1, child2, child3])

child1.children.append(Node(5))
child1.children.append(Node(6))
```

#### 2. Traversals

**Preorder (Root → Children)**

```python
def preorder(root):
    if not root:
        return
    print(root.data, end=' ')
    for child in root.children:
        preorder(child)
```

**Postorder (Children → Root)**

```python
def postorder(root):
    if not root:
        return
    for child in root.children:
        postorder(child)
    print(root.data, end=' ')
```

**Level Order (BFS)**

```python
from collections import deque

def level_order(root):
    if not root:
        return
    queue = deque([root])
    while queue:
        node = queue.popleft()
        print(node.data, end=' ')
        for child in node.children:
            queue.append(child)
```

#### 3. Count Nodes

```python
def count_nodes(root):
    if not root:
        return 0
    total = 1
    for child in root.children:
        total += count_nodes(child)
    return total
```

#### 4. Height of Tree

```python
def height(root):
    if not root or not root.children:
        return 1
    return 1 + max(height(child) for child in root.children)
```

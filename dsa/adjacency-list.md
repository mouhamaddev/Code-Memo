### Adjacency List

A **graph** is a collection of **nodes (vertices)** and **edges** connecting them.
An **Adjacency List** is one of the most common and space-efficient ways to represent a graph, especially when the graph is **sparse** (fewer edges).

Each node maps to a list of its **neighboring nodes**.

### Example Graph:

```
A -- B
|    |
C -- D
```

Adjacency List Representation:

```python
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D'],
    'C': ['A', 'D'],
    'D': ['B', 'C']
}
```

#### Using `defaultdict` for Dynamic Graph

```python
from collections import defaultdict

class Graph:
    def __init__(self):
        self.adj = defaultdict(list)

    def add_edge(self, u, v):
        self.adj[u].append(v)
        self.adj[v].append(u)  # Remove this line for directed graphs
```

#### Traversal Methods

##### 1. Breadth-First Search (BFS)

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])

    while queue:
        node = queue.popleft()
        if node not in visited:
            print(node, end=' ')
            visited.add(node)
            for neighbor in graph[node]:
                if neighbor not in visited:
                    queue.append(neighbor)
```

##### 2. Depth-First Search (DFS)

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node not in visited:
        print(node, end=' ')
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)
```

#### Use Cases

* BFS: Shortest path in unweighted graphs, level-order processing
* DFS: Connectivity checks, cycle detection, topological sort (in directed graphs)

#### Weighted Graph

```python
graph = {
    'A': [('B', 4), ('C', 2)],
    'B': [('A', 4)],
    ...
}
```

#### Directed:
Just remove the symmetric edge (don’t add both `u → v` and `v → u`).

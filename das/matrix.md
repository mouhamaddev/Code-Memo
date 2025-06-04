### Adjacency Matrix

An **Adjacency Matrix** is a 2D array used to represent a graph.
It’s ideal for **dense graphs** where most pairs of nodes are connected.

- If there is an edge between node `i` and node `j`, then `matrix[i][j] = 1` (or weight `w`).
- For **undirected graphs**, the matrix is **symmetric**.
- For **directed graphs**, `matrix[i][j] = 1` means there’s a **one-way edge** from `i` to `j`.

#### Example Graph:

```
0 -- 1
|    |
2 -- 3
```

Adjacency Matrix:

```
   0 1 2 3
0 [0 1 1 0]
1 [1 0 0 1]
2 [1 0 0 1]
3 [0 1 1 0]
```

#### Matrix Representation

```python
class GraphMatrix:
    def __init__(self, num_nodes):
        self.V = num_nodes
        self.matrix = [[0] * num_nodes for _ in range(num_nodes)]

    def add_edge(self, u, v):
        self.matrix[u][v] = 1
        self.matrix[v][u] = 1  # Remove this for directed graphs
```

#### Print the Matrix

```python
def print_matrix(graph):
    for row in graph.matrix:
        print(row)
```

#### Weighted Graph Matrix

```python
def add_weighted_edge(self, u, v, weight):
    self.matrix[u][v] = weight
    self.matrix[v][u] = weight  # Remove for directed graph
```

#### Traversals (BFS / DFS)

##### BFS using Matrix

```python
from collections import deque

def bfs_matrix(graph, start):
    visited = [False] * graph.V
    queue = deque([start])

    while queue:
        node = queue.popleft()
        if not visited[node]:
            print(node, end=' ')
            visited[node] = True
            for neighbor in range(graph.V):
                if graph.matrix[node][neighbor] and not visited[neighbor]:
                    queue.append(neighbor)
```

##### DFS using Matrix

```python
def dfs_matrix(graph, node, visited=None):
    if visited is None:
        visited = [False] * graph.V
    if not visited[node]:
        print(node, end=' ')
        visited[node] = True
        for neighbor in range(graph.V):
            if graph.matrix[node][neighbor] and not visited[neighbor]:
                dfs_matrix(graph, neighbor, visited)
```

#### Space & Time Complexity

- **Space**: O(V²)
- **Insert/Delete Edge**: O(1)
- **Check if edge exists**: O(1)
- **Inefficient for sparse graphs** (many 0s)

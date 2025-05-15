### Heaps

A **Heap** is a special **binary tree-based** data structure that satisfies the **Heap Property**:

* **Min Heap**: The value of the parent is **less than or equal to** its children.
* **Max Heap**: The value of the parent is **greater than or equal to** its children.

A heap is always a **complete binary tree**, meaning all levels are fully filled except possibly the last, which is filled from left to right.

#### Implementation Using `heapq` (Min Heap)

```python
import heapq

heap = []

# Push elements
heapq.heappush(heap, 10)
heapq.heappush(heap, 4)
heapq.heappush(heap, 15)

# Pop the smallest
print(heapq.heappop(heap))  # 4

# Peek the smallest
print(heap[0])  # 10
```

> `heapq` only supports **Min Heaps**. For Max Heap, use negative numbers.

#### Max Heap Using `heapq`

```python
heap = []

# Push negated values
heapq.heappush(heap, -10)
heapq.heappush(heap, -4)
heapq.heappush(heap, -15)

# Pop and negate back
print(-heapq.heappop(heap))  # 15
```

#### Custom Object in Heap

```python
class Task:
    def __init__(self, priority, name):
        self.priority = priority
        self.name = name

    def __lt__(self, other):
        return self.priority < other.priority

heap = []
heapq.heappush(heap, Task(1, "Clean"))
heapq.heappush(heap, Task(3, "Sleep"))
heapq.heappush(heap, Task(2, "Code"))

task = heapq.heappop(heap)
print(task.name)  # Clean
```

#### Heap as a List

A **heap is represented as a list** (array-based), using the following index relationships:

* Parent at `i`
* Left child at `2*i + 1`
* Right child at `2*i + 2`

#### Building a Heap

```python
nums = [5, 3, 8, 1, 2]
heapq.heapify(nums)  # Rearranges to heap in-place

print(nums)  # [1, 2, 8, 5, 3]
```

#### Heap Sort (Ascending)

```python
def heap_sort(nums):
    heapq.heapify(nums)
    sorted_nums = []
    while nums:
        sorted_nums.append(heapq.heappop(nums))
    return sorted_nums
```

#### Manual Implementation of Min Heap (Using Class)

```python
class MinHeap:
    def __init__(self):
        self.heap = []

    def insert(self, val):
        self.heap.append(val)
        self._heapify_up(len(self.heap) - 1)

    def pop(self):
        if not self.heap:
            return None
        if len(self.heap) == 1:
            return self.heap.pop()

        root = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._heapify_down(0)
        return root

    def _heapify_up(self, idx):
        parent = (idx - 1) // 2
        if idx > 0 and self.heap[idx] < self.heap[parent]:
            self.heap[idx], self.heap[parent] = self.heap[parent], self.heap[idx]
            self._heapify_up(parent)

    def _heapify_down(self, idx):
        smallest = idx
        left = 2 * idx + 1
        right = 2 * idx + 2

        if left < len(self.heap) and self.heap[left] < self.heap[smallest]:
            smallest = left
        if right < len(self.heap) and self.heap[right] < self.heap[smallest]:
            smallest = right
        if smallest != idx:
            self.heap[smallest], self.heap[idx] = self.heap[idx], self.heap[smallest]
            self._heapify_down(smallest)
```

#### Time Complexities

| Operation      | Time Complexity |
| -------------- | --------------- |
| Insert         | O(log n)        |
| Delete Min/Max | O(log n)        |
| Peek           | O(1)            |
| Heapify        | O(n)            |
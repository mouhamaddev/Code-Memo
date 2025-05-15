### Queues

A **queue** is a linear data structure that follows the **First-In-First-Out (FIFO)** principle. The element inserted first is the one to be removed first. It is used in scenarios like task scheduling, buffering, and breadth-first search.

#### Types of Queues

1. **Simple Queue**: Basic FIFO behavior.
2. **Circular Queue**: Connects the last position back to the first to efficiently use space.
3. **Deque (Double-Ended Queue)**: Allows insertion and deletion from both ends.
4. **Priority Queue**: Elements are served based on priority rather than arrival time.

#### 1. Simple Queue Using List

```python
queue = []
```

**Enqueue (Add to end)**

```python
queue.append(10)
queue.append(20)
```

**Dequeue (Remove from front)**

```python
queue.pop(0)  # Removes 10
```

> ! Inefficient for large queues due to O(n) time on pop(0)

#### 2. Queue Using `collections.deque`

```python
from collections import deque

queue = deque()
```

**Enqueue**

```python
queue.append(10)
queue.append(20)
```

**Dequeue**

```python
queue.popleft()  # Removes 10
```

**Check if empty**

```python
if not queue:
    print("Queue is empty")
```

**Peek (front element)**

```python
print(queue[0])
```

#### 3. Circular Queue (Custom Implementation)

```python
class CircularQueue:
    def __init__(self, size):
        self.queue = [None] * size
        self.head = self.tail = -1
        self.size = size
```

**Enqueue**

```python
def enqueue(self, value):
    if (self.tail + 1) % self.size == self.head:
        print("Queue is full")
        return
    if self.head == -1:
        self.head = self.tail = 0
    else:
        self.tail = (self.tail + 1) % self.size
    self.queue[self.tail] = value
```

**Dequeue**

```python
def dequeue(self):
    if self.head == -1:
        print("Queue is empty")
        return
    removed = self.queue[self.head]
    if self.head == self.tail:
        self.head = self.tail = -1
    else:
        self.head = (self.head + 1) % self.size
    return removed
```

#### 4. Deque (Double-Ended Queue)

```python
from collections import deque

dq = deque()
```

**Insert Front / Rear**

```python
dq.appendleft(10)
dq.append(20)
```

**Remove Front / Rear**

```python
dq.popleft()  # Removes 10
dq.pop()      # Removes 20
```

#### 5. Priority Queue

```python
import heapq

pq = []
heapq.heappush(pq, 2)
heapq.heappush(pq, 1)
heapq.heappush(pq, 3)
```

**Pop with highest priority (smallest number)**

```python
heapq.heappop(pq)  # Returns 1
```

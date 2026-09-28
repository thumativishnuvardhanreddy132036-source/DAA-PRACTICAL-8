# BFS and DFS in Python

## Aim

To implement **Breadth First Search (BFS)** and **Depth First Search (DFS)** algorithms using Python.

## Introduction

Graph traversal means visiting the vertices or nodes of a graph.

The two common graph traversal algorithms are:

- Breadth First Search (BFS)
- Depth First Search (DFS)

---

# 1. Breadth First Search (BFS)

## Definition

BFS is a graph traversal algorithm that visits nodes **level by level**.

BFS uses a **Queue** data structure.

### Example Graph

```text
        A
       / \
      B   C
     / \   \
    D   E   F
```

### BFS Traversal

```text
A B C D E F
```

## Python Code

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)

    while queue:
        node = queue.popleft()
        print(node, end=" ")

        for neighbour in graph[node]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)


graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': [],
    'F': []
}

bfs(graph, 'A')
```

### Output

```text
A B C D E F
```

### Complexity

- **Time Complexity:** O(V + E)
- **Space Complexity:** O(V)

Where:
- `V` = Number of vertices
- `E` = Number of edges

---

# 2. Depth First Search (DFS)

## Definition

DFS is a graph traversal algorithm that explores a node **as deeply as possible** before backtracking.

DFS uses a **Stack**. It can also be implemented using **recursion**.

### Example Graph

```text
        A
       / \
      B   C
     / \   \
    D   E   F
```

### DFS Traversal

```text
A B D E C F
```

## Python Code

```python
def dfs(graph, node, visited):
    if node not in visited:
        print(node, end=" ")
        visited.add(node)

        for neighbour in graph[node]:
            dfs(graph, neighbour, visited)


graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': [],
    'F': []
}

visited = set()

dfs(graph, 'A', visited)
```

### Output

```text
A B D E C F
```

### Complexity

- **Time Complexity:** O(V + E)
- **Space Complexity:** O(V)

---

# 3. BFS vs DFS

| Feature | BFS | DFS |
|---|---|---|
| Full Form | Breadth First Search | Depth First Search |
| Traversal | Level by level | Depth first |
| Data Structure | Queue | Stack / Recursion |
| Principle | FIFO | LIFO |
| Time Complexity | O(V + E) | O(V + E) |
| Shortest Path | Yes, in unweighted graphs | Not necessarily |

---

# 4. Applications

## BFS

- Finding shortest paths in unweighted graphs
- Network broadcasting
- Social network connections
- Web crawling
- Level-order tree traversal

## DFS

- Maze solving
- Path finding
- Cycle detection
- Topological sorting
- Finding connected components

---

# 5. Conclusion

BFS and DFS are important graph traversal techniques.

### BFS

```text
Queue → Level by Level
```

### DFS

```text
Stack / Recursion → Go Deep → Backtrack
```

Both BFS and DFS have a time complexity of:

```text
O(V + E)
```

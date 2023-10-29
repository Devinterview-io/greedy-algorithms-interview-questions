# ⚫ Greedy Algorithms in Tech Interviews 2024: 6 Must-Know Questions & Answers

**Greedy Algorithms** make locally optimal choices at each step in the hope of finding a global optimum. They're effective for certain problems where this **local-to-global strategy** works, such as the coin change or activity selection problems. In coding interviews, they assess a candidate's ability to identify when a problem can be solved with a **greedy approach** and to implement efficient solutions.

Check out our carefully selected list of **basic** and **advanced** Greedy Algorithms questions and answers to be well-prepared for your tech interviews in 2024.

![Greedy Algorithms Decorative Image](https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/blogImg%2FgreedyAlgorithms.png?alt=media&token=da947af7-9b48-43bc-a3f0-ef2aca12f631&_gl=1*m7x0tq*_ga*OTYzMjY5NTkwLjE2ODg4NDM4Njg.*_ga_CW55HF8NVT*MTY5ODYwNTk1NS4xOTAuMS4xNjk4NjA3MjM0LjQyLjAuMA..)

👉🏼 You can also find all answers here: [Devinterview.io - Greedy Algorithms](https://devinterview.io/data/greedyAlgorithms-interview-questions)

---

## 🔹 1. What is a _Greedy Algorithm_?

### Answer

A **greedy algorithm** aims to solve optimization problems by making the **best local choice** at each step. While this often leads to an **optimal global solution**, it's not guaranteed in all cases. These algorithms are generally easier to implement and faster than other methods like Dynamic Programming but may not always yield the most accurate solution.

### Key Features
1. **Greedy-Choice Property**: Each step aims for a local optimum with the expectation that this will lead to a global optimum.
2. **Irreversibility**: Once made, choices are not revisited.
3. **Efficiency**: Greedy algorithms are usually faster, particularly for problems that don't require a globally optimal solution.

### Example Algorithms

#### Fractional Knapsack Problem
Here, the goal is to maximize the value of items in a knapsack with a fixed capacity. The greedy strategy chooses items based on their **value-to-weight ratio**.

```python
def fractional_knapsack(items, capacity):
    items.sort(key=lambda x: x[1]/x[0], reverse=True)
    max_value = 0
    knapsack = []
    for item in items:
        if item[0] <= capacity:
            knapsack.append(item)
            capacity -= item[0]
            max_value += item[1]
        else:
            fraction = capacity / item[0]
            knapsack.append((item[0] * fraction, item[1] * fraction))
            max_value += item[1] * fraction
            break
    return max_value, knapsack

items = [(10, 60), (20, 100), (30, 120)]
capacity = 50
print(fractional_knapsack(items, capacity))
```

#### Dijkstra's Shortest Path
This algorithm **finds the shortest path** in a graph by selecting the vertex with the minimum distance at each step.

```python
import heapq

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    priority_queue = [(0, start)]

    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)
        if current_distance > distances[current_node]:
            continue
        for neighbour, weight in graph[current_node].items():
            distance = current_distance + weight
            if distance < distances[neighbour]:
                distances[neighbour] = distance
                heapq.heappush(priority_queue, (distance, neighbour))
    return distances

graph = {'A': {'B': 1, 'C': 4},'B': {'A': 1, 'C': 2, 'D': 5},'C': {'A': 4, 'B': 2, 'D': 1},'D': {'B': 5, 'C': 1}}
print(dijkstra(graph, 'A'))
```

In summary, **greedy algorithms** offer a fast and intuitive approach to optimization problems, although they may sacrifice optimal solutions for speed.

---

## 🔹 2. What are _Greedy Algorithms_ used for?

### Answer

**Greedy algorithms** are often the algorithm of choice for problems where the optimal solution can be built incrementally and **local decisions** lead to a **globally optimal solution**.

### Applications of Greedy Algorithms

#### Shortest Path Algorithms
- **Dijkstra's Algorithm**: Finds the shortest path from a source vertex to all vertices in a weighted graph. 

  Use-Case: Navigation systems.

#### Minimum Spanning Trees
- **Kruskal's Algorithm**: Finds the minimum spanning tree in a weighted graph by sorting edges and choosing the smallest edge without a cycle.

  Use-Case: LAN setup.

- **Prim's Algorithm**: Starts from a random vertex and selects the smallest edge connecting to the growing tree.

  Use-Case: Superior for dense graphs.

#### Data Compression
- **Huffman Coding**: Used for data compression by building a binary tree with frequent characters closer to the root. 

  Use-Case: ZIP compression.

#### Job Scheduling
- **Interval Scheduling**: Selects the maximum number of non-overlapping intervals or tasks.

  Use-Case: Classroom or conference room organization.

#### Set Cover
- **Set Cover Problem**: Finds the smallest set collection covering all elements in a universal set.

  Use-Case: Efficient broadcasting in networks.

#### Knapsack Problem
- **Fractional Knapsack**: A variant that allows parts of items to be taken, with greedy methods giving an optimal solution.

  Use-Case: Resource distribution with partial allocations.

#### Other Domains
- **Text Justification** and **Cache Management**.

---

## 🔹 3. Compare _Greedy_ vs _Divide & Conquer_ vs _Dynamic Programming_ algorithms.

### Answer

Let's explore how **Greedy**, **Divide & Conquer**, and **Dynamic Programming** algorithms differ across key metrics such as optimality, computational complexity, and memory usage. 

### Key Metrics

- **Optimality**: Greedy may not guarantee optimality, while both Divide & Conquer and Dynamic Programming do.
- **Computational Complexity**: Greedy is generally the fastest; Divide & Conquer varies, and Dynamic Programming can be slower but more accurate.
- **Memory Usage**: Greedy is most memory-efficient, Divide & Conquer is moderate, and Dynamic Programming can be memory-intensive due to caching.

### Greedy Algorithms

Choose Greedy algorithms when a **local** best choice leads to a **global** best choice.

#### Use Cases
- **Shortest Path Algorithms**: Dijkstra's Algorithm for finding the shortest path in a weighted graph.
- **Text Compression**: Huffman Coding for compressing text files.
- **Network Routing**: For minimizing delay or cost in computer networks.
- **Task Scheduling**: For scheduling tasks under specific constraints to optimize for time or cost.

### Divide & Conquer Algorithms

Opt for Divide & Conquer when you can solve **independent subproblems** and combine them for the **global optimum**.

#### Use Cases

- **Sorting Algorithms**: Quick sort and Merge sort for efficient sorting of lists or arrays.
- **Search Algorithms**: Binary search for finding an element in a sorted list.
- **Matrix Multiplication**: Strassen's algorithm for faster matrix multiplication.
- **Computational Geometry**: Algorithms for solving geometric problems like finding the closest pair of points.

### Dynamic Programming Algorithms

Choose Dynamic Programming when overlapping subproblems can be **solved once and reused**.

#### Use Cases

- **Optimal Path Problems**: Finding the most cost-efficient path in a grid or graph, such as in the Floyd-Warshall algorithm.
- **Text Comparison**: Algorithms like the Levenshtein distance for spell checking and DNA sequence alignment.
- **Resource Allocation**: Knapsack problem for optimal resource allocation under constraints.
- **Game Theory**: Minimax algorithm for decision-making in two-player games.

---

## 🔹 4. Is _Dijkstra's_ algorithm a _Greedy_ or _Dynamic Programming_ algorithm?

### Answer

**Dijkstra's algorithm** utilizes a combination of greedy and dynamic programming techniques.

### Greedy Component: Immediate Best Choice
The algorithm selects the closest neighboring vertex at each step, reflecting the greedy approach of optimizing for immediate gains.

#### Example
Starting at vertex A, the algorithm picks the nearest vertex based on current known distances. 

![Dijkstra's Algorithm](https://upload.wikimedia.org/wikipedia/commons/5/57/Dijkstra_Animation.gif)

### Dynamic Programming Component: Global Optimization
Dijkstra's algorithm updates vertex distances based on previously calculated shortest paths, embodying the dynamic programming principle of optimal substructure.

#### Example
Initially, all vertices have infinite distance from the source, A. After the first iteration, distances to neighbors are updated, and the closest one is chosen for the next step.

```plaintext
Initial State: A: 0, B: inf, C: inf, D: inf, E: inf
After first iteration: A: 0, B: 2, C: 3, D: 8, E: inf
```

### Primarily Dynamic Programming
Despite combining both strategies, the algorithm aligns more closely with dynamic programming for several reasons:

1. **Guaranteed Optimality**: It provides the best solution, a hallmark of dynamic programming.
2. **Comprehensive Exploration**: The algorithm reviews all vertices to ensure the shortest path.

---
## 🔹 5. What is the difference between _Greedy_ and _Heuristic_ algorithms?

### Answer

👉🏼 Check out all 6 answers here: [Devinterview.io - Greedy Algorithms](https://devinterview.io/data/greedyAlgorithms-interview-questions)

---

## 🔹 6. Is there a way to _Mathematically Prove_ that a _Greedy Algorithm_ will yield the _Optimal Solution_?

### Answer

👉🏼 Check out all 6 answers here: [Devinterview.io - Greedy Algorithms](https://devinterview.io/data/greedyAlgorithms-interview-questions)

---


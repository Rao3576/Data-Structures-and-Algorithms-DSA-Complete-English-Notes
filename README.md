# Data-Structures-and-Algorithms-DSA-Complete-English-Notes
Learn Data Structures and Algorithms (DSA) in an easy way — with Python examples, clear diagrams, and detailed explanations of Linked List, Stack, Queue, and more.



## 📘 1. What is DSA?

**DSA (Data Structures and Algorithms)** is the foundation of programming.
It defines **how data is stored, managed, and processed efficiently**.

### 🔹 Data Structure:

The way data is organized and stored in memory for easy access and modification.

### 🔹 Algorithm:

A step-by-step process or procedure to solve a problem.

---

## ⚙️ 2. Types of Data Structures

### **Linear Data Structures**

* Array
* Linked List
* Stack
* Queue

### **Non-Linear Data Structures**

* Tree
* Graph

---

##  3. Array

An **array** is a collection of elements stored **contiguously in memory**.
All elements are of the **same data type**.

### Example

```python
arr = [10, 20, 30, 40]
```

| Index | 0  | 1  | 2  | 3  |
| ----- | -- | -- | -- | -- |
| Value | 10 | 20 | 30 | 40 |

### Operations

* **Insert** → Add new element at the end or a specific index
* **Delete** → Remove an element

---

## 🔗 4. Linked List

A **Linked List** is a **dynamic data structure**, meaning it can grow or shrink in size.
It is made up of **nodes**, where each node has two parts:

* **Data** → stores actual value
* **Next** → stores address (reference) of the next node

### Structure

```
[Data | Next] → [Data | Next] → [Data | None]
```

### Example

```
10 → 20 → 30 → None
```

---

## Node Structure (Python Example)

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

---

## 🔧 Linked List Class

```python
class LinkedList:
    def __init__(self):
        self.head = None

    def print_list(self):
        current = self.head
        while current:
            print(f"{current.data} → ", end="")
            current = current.next
        print("None")
```

---

## ➕ Insertion in Linked List

### 1️⃣ Insert at Beginning

```python
def insert_at_beginning(self, data):
    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
```

**Example:**
Before → `10 → 20 → 30 → None`
After inserting **5 at beginning** → `5 → 10 → 20 → 30 → None`

**Traversal explanation:**

| Step | Current Node | Data | Next   |
| ---- | ------------ | ---- | ------ |
| 1    | Head         | 5    | → 10   |
| 2    | Node2        | 10   | → 20   |
| 3    | Node3        | 20   | → 30   |
| 4    | Node4        | 30   | → None |

---

### 2️⃣ Insert at End

```python
def insert_at_end(self, data):
    new_node = Node(data)
    if not self.head:
        self.head = new_node
        return
    last = self.head
    while last.next:
        last = last.next
    last.next = new_node
```

**Example:**
Before → `10 → 20 → 30 → None`
After inserting **40 at end** → `10 → 20 → 30 → 40 → None`

---

### 3️⃣ Insert in the Middle (Between Two Nodes)

```python
def insert_after(self, prev_data, new_data):
    current = self.head
    while current and current.data != prev_data:
        current = current.next
    if not current:
        print("Node not found!")
        return
    new_node = Node(new_data)
    new_node.next = current.next
    current.next = new_node
```

**Example:**
Before → `10 → 20 → 30 → 40 → None`
Insert **25 after 20** → `10 → 20 → 25 → 30 → 40 → None`

---

##  Deletion in Linked List

### Delete First Node

```python
def delete_first(self):
    if self.head:
        self.head = self.head.next
```

Before → `10 → 20 → 30 → None`
After → `20 → 30 → None`

---

### Delete Last Node

```python
def delete_last(self):
    if not self.head:
        return
    if not self.head.next:
        self.head = None
        return
    second_last = self.head
    while second_last.next.next:
        second_last = second_last.next
    second_last.next = None
```

Before → `10 → 20 → 30 → None`
After → `10 → 20 → None`

---

## 🔁 Traversing a Linked List

To **visit** each node and **print its data**, we move from the head node to the end.

```
Head → [10|●] → [20|●] → [30|X]
```

Each arrow (`→`) represents the `next` reference to the following node.

---

## 5. Double Linked List (DLL)

Each node contains **three parts**:

1. `Prev` → address of the previous node
2. `Data` → actual information
3. `Next` → address of the next node

**Structure:**

```
None ← [10 | ● | 20] ↔ [20 | ● | 30] ↔ [30 | ● | None]
```

**Advantages:**

* Can move **forward** and **backward**

---

## 🔁 6. Triple / Circular Linked List

In this type, the **last node connects back to the first node** — forming a circle.

```
[10] → [20] → [30]
   ↑             ↓
   ←–––––––––––––––
```

---

## 7. Stack

A **Stack** follows **LIFO (Last In First Out)** order.

### Example:

Push(10), Push(20), Push(30)

Stack = [10, 20, 30]

Pop() → Removes 30

```
| 30 |  ← Top
| 20 |
| 10 |
```

**Python Example:**

```python
stack = []
stack.append(10)
stack.append(20)
stack.append(30)
stack.pop()  # Removes 30
```

---

## 8. Queue

A **Queue** follows **FIFO (First In First Out)** order.

### Example:

Enqueue(10), Enqueue(20), Enqueue(30)

Queue = [10, 20, 30]

Dequeue() → Removes 10

```
Front → 10 → 20 → 30 → Rear
```

**Python Example:**

```python
from collections import deque

queue = deque()
queue.append(10)
queue.append(20)
queue.append(30)
queue.popleft()  # Removes 10
```

---

## 🧾 Summary Table

| Data Structure     | Order         | Example                          | Operation                |
| ------------------ | ------------- | -------------------------------- | ------------------------ |
| Linked List        | Dynamic       | 10 → 20 → 30                     | Insert, Delete, Traverse |
| Stack              | LIFO          | Push(10,20,30) → Pop()=30        | Push / Pop               |
| Queue              | FIFO          | Enqueue(10,20,30) → Dequeue()=10 | Enqueue / Dequeue        |
| Double Linked List | Bidirectional | 10 ↔ 20 ↔ 30                     | Move Both Ways           |

---

### ✅ Author

**Created by:** *Rao Kashif*

**Language:** Python + Markdown

**Purpose:** Easy DSA understanding for beginners with diagrams and examples.


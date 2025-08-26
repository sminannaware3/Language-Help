## LeetCode Python Data Structures Reference

This document provides a quick reference for the most common Python data structures used in solving LeetCode problems. Understanding the syntax and complexity of these structures is crucial for writing efficient code.

## 1. Lists (Dynamic Arrays)
Lists are the most versatile built-in data structure. They are dynamic, meaning their size can change.

### Creation & Basic Operations
```
# Create an empty list
my_list = []

# Create a list with elements
numbers = [1, 2, 3, 4]

# Access elements (0-indexed)
first_item = numbers[0]  # Output: 1. Time: O(1)
last_item = numbers[-1]  # Output: 4. Time: O(1)

# Add elements
my_list.append(5)         # Adds 5 to the end. Time: O(1) amortized, Space: O(1)
my_list.insert(0, 10)     # Inserts 10 at index 0. Time: O(n), Space: O(1)

# Remove elements
my_list.pop()             # Removes and returns the last item. Time: O(1), Space: O(1)
my_list.remove(5)         # Removes the first occurrence of 5. Time: O(n), Space: O(1)
del my_list[0]            # Deletes item at index 0. Time: O(n), Space: O(1) 
```

### Common List Methods & Functions
```
# Sorting
unsorted_list = [3, 1, 4, 1, 5]
unsorted_list.sort()      # Sorts in-place (ascending). Time: O(n log n), Space: O(n) for Timsort
sorted_list = sorted(unsorted_list, reverse=True) # Returns a new sorted list. Time: O(n log n), Space: O(n)

# Length of the list
length = len(unsorted_list) # Time: O(1)

# Slicing
subset = unsorted_list[1:3] # Returns a new list from index 1 to 2. Time: O(k), where k is the slice length. Space: O(k)
```

## 2. Dictionaries (Hash Maps)

Dictionaries store key-value pairs and offer O(1) average time complexity for lookups, insertions, and deletions.

### Creation & Operations
```
# Create an empty dictionary
my_dict = {}

# Create with initial values
person = {"name": "Alice", "age": 30, "city": "New York"}

# Access values
name = person["name"]    # Output: 'Alice'. Time: O(1) average, O(n) worst case. Space: O(1)
age = person.get("age")  # Safer access, returns None if key not found. Time: O(1) average. Space: O(1)

# Add or update a key
person["age"] = 31       # Updates age. Time: O(1) average, O(n) worst case. Space: O(1)
person["email"] = "alice@example.com" # Adds new key-value pair. Time: O(1) average. Space: O(1)

# Remove a key
del person["city"]       # Time: O(1) average. Space: O(1)

# Check for key existence
if "name" in person:     # Time: O(1) average. Space: O(1)
    print("Name exists!")

# Iteration
for key, value in person.items():  # Time: O(n). Space: O(1) if iterating directly.
    print(f"{key}: {value}")
```

## 3. Strings
Strings are immutable sequences of characters. You cannot change a string in-place; methods always return a new string.

### Common Methods
```
my_string = "hello world"

# Slicing
substring = my_string[6:11] # Output: 'world'. Time: O(k), where k is slice length. Space: O(k)

# Splitting and Joining
words = my_string.split(" ")     # Output: ['hello', 'world']. Time: O(n). Space: O(n)
joined_string = "-".join(words)  # Output: 'hello-world'. Time: O(n). Space: O(n)

# Other useful methods
index = my_string.find('o')      # Returns the first index of 'o'. Time: O(n). Space: O(1)
new_string = my_string.replace('l', 'L') # Replaces all 'l's. Time: O(n). Space: O(n)
```

## 4. Sets
Sets store a collection of unique and unordered elements. They are optimized for checking membership with O(1) average time complexity.

### Creation & Operations
```
# Create an empty set
my_set = set()

# Create a set from a list (duplicates are removed)
numbers = [1, 2, 2, 3, 4, 4]
unique_numbers = set(numbers)  # Output: {1, 2, 3, 4}. Time: O(n), Space: O(n)

# Add and remove elements
unique_numbers.add(5)         # Time: O(1) average. Space: O(1)
unique_numbers.remove(1)      # Time: O(1) average. Space: O(1)

# Check for existence
if 2 in unique_numbers:    # Time: O(1) average. Space: O(1)
    print("2 is in the set.")

# Set operations
set_a = {1, 2, 3}
set_b = {3, 4, 5}
union_set = set_a.union(set_b)       # Output: {1, 2, 3, 4, 5}. Time: O(len(a) + len(b)). Space: O(len(a) + len(b))
intersection = set_a.intersection(set_b) # Output: {3}. Time: O(min(len(a), len(b))). Space: O(min(len(a), len(b)))
```

## 5. Stacks & Queues
While not a native data structure, Python's `collections.deque` can be used to implement both stacks and queues efficiently.

### Stacks (LIFO)
```
from collections import deque

stack = deque()

stack.append(1)   # Push. Time: O(1). Space: O(1)
stack.append(2)   # Push. Time: O(1). Space: O(1)
item = stack.pop()  # Pop, returns 2. Time: O(1). Space: O(1)
```

### Queues (FIFO)
```
from collections import deque

queue = deque()

queue.append(1)   # Enqueue. Time: O(1). Space: O(1)
queue.append(2)   # Enqueue. Time: O(1). Space: O(1)
item = queue.popleft() # Dequeue, returns 1. Time: O(1). Space: O(1)
```

## 6. Heaps (Priority Queues)
Python's `heapq` module provides an implementation of the heap queue algorithm. It is a min-heap by default.

### Using `heapq`
```
import heapq

# Create a min-heap from a list
heap = [3, 1, 4, 1, 5]
heapq.heapify(heap) # In-place conversion. Time: O(n). Space: O(1)

# Push and pop
heapq.heappush(heap, 0) # Pushes 0, maintains heap property. Time: O(log n). Space: O(1)
smallest = heapq.heappop(heap) # Pops and returns the smallest item. Time: O(log n). Space: O(1)

# To simulate a max-heap, store items as their negative
max_heap = []
values = [3, 1, 4]
for val in values:
    heapq.heappush(max_heap, -val) # Time: O(n log n) total.

largest = -heapq.heappop(max_heap) # Pop and negate to get the largest. Time: O(log n). Space: O(1)
```

### 7. Linked Lists
Linked lists are a common concept in LeetCode. You'll often need to define a `ListNode` class to work with them.

### Node Definition
```
# Definition for a singly-linked list node.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

### Example Usage
```
# Create a simple linked list: 1 -> 2 -> 3
node3 = ListNode(3)
node2 = ListNode(2, node3)
node1 = ListNode(1, node2)

# Head of the list
head = node1

# Traversal (common operation)
current = head
while current:
    # Traverses the list from head to tail. Time: O(n). Space: O(1)
    print(current.val)
    current = current.next
```


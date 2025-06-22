
# Common Data Structures and Their Operations

This document provides a quick reference for common data structures, including their declaration, common operations, sorting considerations, and general time complexities.

---

## 1. Arrays

Fixed-size, contiguous block of memory.

```

import java.util.Arrays; // For Arrays.sort()
import java.util.Collections; // For Collections.reverseOrder() if sorting objects
import java.util.Comparator; // For custom comparators

````

* **Declaration and Initialization:**
    ```
    int[] arr = new int[size];
    ```
* **Accessing Elements:**
    ```
    arr[index]
    ```
* **Length:**
    ```
    arr.length
    ```
* **Sorting:**
    * **Ascending (primitive or Comparable objects):**
        ```
        Arrays.sort(arr);
        ```
    * **Descending (for wrapper objects like Integer[], String[]):**
        ```
        Integer[] arr = {3, 1, 4, 1, 5, 9};
        Arrays.sort(arr, Collections.reverseOrder());
        ```
    * **Custom Sorting (with Comparator):**
        ```
        String[] words = {"apple", "banana", "kiwi"};
        Arrays.sort(words, (s1, s2) -> s1.length() - s2.length()); // Sort by length
        ```

## 2. ArrayList (Dynamic Array)

Resizable array implementation.

````

import java.util.ArrayList;
import java.util.Collections; // For Collections.sort()
import java.util.Comparator;  // For custom comparators

````

* **Creation:**
    ```
    ArrayList<Integer> list = new ArrayList<>();
    ```
* **Adding Elements:**
    ```
    list.add(element);
    ```
* **Accessing Elements:**
    ```
    list.get(index);
    ```
* **Removing Elements:**
    ```
    list.remove(index); // by index
    list.remove(Object); // by object
    ```
* **Size:**
    ```
    list.size();
    ```
* **Sorting:**
    * **Ascending (Comparable objects):**
        ```
        Collections.sort(list);
        ```
    * **Descending:**
        ```
        Collections.sort(list, Collections.reverseOrder());
        ```
    * **Custom Sorting (with Comparator):**
        ```
        list.sort((s1, s2) -> s1.length() - s2.length()); // From 8+
        // OR
        Collections.sort(list, new Comparator<Integer>() {
            @Override
            public int compare(Integer i1, Integer i2) {
                return i1 - i2; // Example: ascending
            }
        });
        ```

## 3. LinkedList

Doubly-linked list implementation.

````

import java.util.LinkedList;
import java.util.Collections; // For Collections.sort()
import java.util.Comparator;  // For custom comparators

````

* **Creation:**
    ```
    LinkedList<Integer> list = new LinkedList<>();
    ```
* **Adding Elements:**
    ```
    list.addFirst(element);
    list.addLast(element);
    list.add(index, element);
    ```
* **Accessing Elements:**
    ```
    list.getFirst();
    list.getLast();
    list.get(index);
    ```
* **Removing Elements:**
    ```
    list.removeFirst();
    list.removeLast();
    list.remove(index);
    ```
* **Sorting:**
    * **Ascending (Comparable objects):**
        ```
        Collections.sort(list);
        ```
    * **Descending:**
        ```
        Collections.sort(list, Collections.reverseOrder());
        ```
    * **Custom Sorting (with Comparator):**
        ```
        list.sort((s1, s2) -> s1.length() - s2.length()); // From 8+
        // OR
        Collections.sort(list, new Comparator<Integer>() {
            @Override
            public int compare(Integer i1, Integer i2) {
                return i1 - i2; // Example: ascending
            }
        });
        ```

## 4. HashMap (Hash Table/Map)

Stores key-value pairs; does **not** maintain insertion order or sorted order.

````

import java.util.HashMap;
import java.util.Map;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.LinkedHashMap; // To preserve insertion order after sorting
import java.util.TreeMap;      // For naturally sorted keys

````

* **Creation:**
    ```
    HashMap<String, Integer> map = new HashMap<>();
    ```
* **Adding/Updating:**
    ```
    map.put(key, value);
    ```
* **Getting Value:**
    ```
    map.get(key);
    ```
* **Checking Key Existence:**
    ```
    map.containsKey(key);
    ```
* **Checking Value Existence:**
    ```
    map.containsValue(value);
    ```
* **Removing:**
    ```
    map.remove(key);
    ```
* **Size:**
    ```
    map.size();
    ```
* **Sorting (Indirectly):**
    * **By Key (into a new sorted Map - TreeMap):**
        ```
        TreeMap<String, Integer> sortedByKeyMap = new TreeMap<>(map);
        // keys are sorted naturally or by a custom constructor comparator
        ```
    * **By Value (into a List of Entries, then sort):**
        ```
        ArrayList<Map.Entry<String, Integer>> entryList = new ArrayList<>(map.entrySet());
        Collections.sort(entryList, (e1, e2) -> e1.getValue().compareTo(e2.getValue())); // Sort by value
        // To put into a map that retains order (LinkedHashMap):
        LinkedHashMap<String, Integer> sortedByValueMap = new LinkedHashMap<>();
        for (Map.Entry<String, Integer> entry : entryList) {
            sortedByValueMap.put(entry.getKey(), entry.getValue());
        }
        ```

## 5. HashSet (Hash Set)

Stores unique elements; does **not** maintain any order.

````

import java.util.HashSet;
import java.util.TreeSet; // For naturally sorted elements
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

````

* **Creation:**
    ```
    HashSet<Integer> set = new HashSet<>();
    ```
* **Adding Elements:**
    ```
    set.add(element);
    ```
* **Checking Existence:**
    ```
    set.contains(element);
    ```
* **Removing Elements:**
    ```
    set.remove(element);
    ```
* **Size:**
    ```
    set.size();
    ```
* **Sorting (Indirectly):**
    * **Into a naturally sorted Set (TreeSet):**
        ```
        TreeSet<Integer> sortedSet = new TreeSet<>(set);
        ```
    * **Into a sorted List:**
        ```
        List<Integer> listFromSet = new ArrayList<>(set);
        Collections.sort(listFromSet);
        ```

## 6. Stack

Last-In, First-Out (LIFO) data structure. `Stack` extends `Vector` and implements `List`, so it can be sorted, but this usually violates its conceptual LIFO nature.

````

import java.util.Stack;
import java.util.Collections; // For Collections.sort()
import java.util.Comparator;  // For custom comparators

````

* **Creation:**
    ```
    Stack<Integer> stack = new Stack<>();
    ```
* **Adding (push):**
    ```
    stack.push(element);
    ```
* **Removing (pop):**
    ```
    stack.pop();
    ```
* **Peeking (top element):**
    ```
    stack.peek();
    ```
* **Checking Empty:**
    ```
    stack.empty();
    ```
* **Sorting (Directly, but against typical usage):**
    * You *can* technically sort a `Stack` because it extends `Vector` (a `List`).
        ```
        Collections.sort(stack); // Sorts elements within the stack
        // This changes the LIFO order!
        ```
    * **More common for sorting elements from a Stack:**
        ```
        List<Integer> tempList = new ArrayList<>(stack); // Copy elements
        Collections.sort(tempList); // Sort the copied elements
        // If you need the stack sorted, you'd clear and push sorted elements back
        // stack.clear();
        // for (Integer element : tempList) {
        //     stack.push(element);
        // }
        ```

## 7. Queue

First-In, First-Out (FIFO) data structure. Does **not** inherently maintain a sorted order.

````

import java.util.Queue;
import java.util.LinkedList;   // Common Queue implementation
import java.util.ArrayDeque;   // Another common Queue implementation
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

````

* **Creation:**
    ```
    Queue<Integer> queue = new LinkedList<>();
    // OR
    Queue<Integer> queue = new ArrayDeque<>();
    ```
* **Adding (offer/add):**
    ```
    queue.offer(element); // Preferred: returns false if full, doesn't throw exception
    queue.add(element);   // Throws IllegalStateException if full
    ```
* **Removing (poll/remove):**
    ```
    queue.poll();   // Preferred: returns null if empty, doesn't throw exception
    queue.remove(); // Throws NoSuchElementException if empty
    ```
* **Peeking (front element):**
    ```
    queue.peek();    // Preferred: returns null if empty
    queue.element(); // Throws NoSuchElementException if empty
    ```
* **Sorting (Indirectly):**
    * Queues themselves are not designed for direct sorting in place. To get sorted elements, you'd typically:
        ```
        List<Integer> tempList = new ArrayList<>(queue); // Copy elements
        Collections.sort(tempList); // Sort the copied elements
        // If you need to re-populate the queue in sorted order:
        // queue.clear();
        // for (Integer element : tempList) {
        //     queue.offer(element);
        // }
        ```

## 8. PriorityQueue

A queue where elements are ordered according to their natural ordering, or by a `Comparator`. It's inherently a heap-based sorted structure. You don't "sort" it, you extract elements in sorted order or define its sorting behavior at creation.

````

import java.util.PriorityQueue;
import java.util.Collections; // For Collections.reverseOrder()
import java.util.Comparator;
import java.util.ArrayList;
import java.util.List;

````

* **Creation (min-heap - natural order):**
    ```
    PriorityQueue<Integer> pq = new PriorityQueue<>();
    ```
* **Creation (max-heap - reverse natural order):**
    ```
    PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
    ```
* **Creation (with custom Comparator):**
    ```
    // Min-heap based on string length
    PriorityQueue<String> pqByLength = new PriorityQueue<>((s1, s2) -> s1.length() - s2.length());
    ```
* **Adding:**
    ```
    pq.offer(element);
    ```
* **Removing (min/max element, depending on heap type):**
    ```
    pq.poll(); // Retrieves and removes the head of the queue (highest priority)
    ```
* **Peeking:**
    ```
    pq.peek(); // Retrieves, but does not remove, the head of the queue
    ```
* **Sorting (How to get sorted elements from it):**
    * Elements are naturally sorted when `poll()`ed:
        ```
        // While loop to retrieve elements in sorted order:
        // while (!pq.isEmpty()) {
        //     System.out.println(pq.poll());
        // }
        ```
    * To get a sorted `List` without emptying the `PriorityQueue`:
        ```
        List<Integer> sortedList = new ArrayList<>(pq); // Copies elements (order not guaranteed here)
        Collections.sort(sortedList); // Sorts the copied list explicitly
        // OR using the PQ's own comparator:
        // Collections.sort(sortedList, pq.comparator());
        ```

---

## Time Complexities (General)

* **Arrays/ArrayLists:**
    * `O(1)` for access (`get`).
    * `O(N)` for insertion/deletion in the middle (requires shifting elements).
    * `O(1)` amortized for `ArrayList.add()` at the end (due to resizing).
    * `O(N log N)` for `Arrays.sort()` and `Collections.sort()`.

* **HashMaps/HashSets:**
    * Average `O(1)` for most operations (`put`, `get`, `contains`, `remove`).
    * Worst case `O(N)` in case of poor hash function leading to excessive hash collisions.
    * Sorting these typically involves converting to a `List` or `TreeMap/TreeSet`, resulting in `O(N log N)` for the sorting step.

* **LinkedLists:**
    * `O(1)` for adding/removing at ends (`addFirst`, `addLast`, `removeFirst`, `removeLast`).
    * `O(N)` for access (`get(index)`) or adding/removing in the middle (requires traversal).
    * `O(N log N)` for `Collections.sort()`.

* **Stacks/Queues:**
    * `O(1)` for push/pop (stack) and offer/poll (queue) operations (when using `ArrayDeque` or `LinkedList` appropriately).
    * Direct `Collections.sort()` on `Stack`/`Queue` (if technically possible) would be `O(N log N)`. Converting to `List` then sorting is also `O(N log N)`.

* **PriorityQueue:**
    * `O(log N)` for `offer` (adding an element) and `poll` (removing the top element).
    * `O(N)` to iterate through all elements (e.g., for `toArray()` or `iterator()`) where order isn't guaranteed until `poll()`ed.
````
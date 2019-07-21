
## Data Structure Basics

### Arrays

##### Definition

* Stores data elements based on an sequential, most commonly 0 based, index.
* Based on Tuples from set theory.
* They are one of the oldest, most commonly used data structure.

##### What you need to know

* Optimal for indexing; bad at searching, inserting, and deleting (except at the end).
* **Linear Arrays**, or one dimensional arrays are the most basic.
    * Are static in size, meaning that they are declared with a fixed size.
* **Dynamic Arrays** are like one dimensional arrays, but have reserved space for additional elements.
    * If a dynamic array is full, it copies it's contents to a larger array.
* **Two Dimensional Arrays** have x and y indices like a grid or nested arrays.

##### Big O Efficiency

* **Indexing** Linear Array: O(1), Dynamic Array: O(1)
* **Search** Linear Array: O(n), Dynamic Array: O(n)
* **Optimized Search** Linear Array: O(log n), Dynamic Array: O(log n)
* **Insertion** Linear Array: N/A, Dynamic Array: O(n)

### Linked List

##### Definition

* Stores data with **nodes** that points to other nodes.
    * Nodes, at its most basic it has one datum and one reference (another node).
    * A linked list *chains* nodes together by pointing one node's reference towards another node.

##### What you need to know

* Designed to optimize insertion and deletion, slow at indexing and searching.
* **Doubly linked list** has nodes that reference the previous node.
* **Circular linked list** is simple linked list whose **tail**, the last node, references the **head**, the first node.
* **Stack**, commonly implemented with linked lists but can be made from arrays too.
    * Stack are **last in, first out** (LIFO) data structures.
    * Made with a linked list by having the head be the only place for insertion and removal.
* **Queues**, too can be implemented with an linked list or an array.
    * Queues are a **first in, first out** (FIFO) data structure.
    * Made with a doubly linked list that only removes from head and adds to tail.

##### Big O Efficiency

* **Indexing** Linked Lists: O(n)
* **Search** Linked Lists: O(n)
* **Optimized Search** Linked Lists: O(n)
* **Insertion** Linked Lists: O(1)

### Hash Table or Hash Map

##### Definition

* Stores data with key value pairs.
* **Hash functions** accept a key and return an output unique only to that specific key.
    * This is known as **hashing**, which is the concept that an input and an output have a one-to-one correspondence to map information.
    * Hash functions return a unique address in memory for that data.

##### What you need to know

* Designed to optimize searching, insertion, and deletion
* **Hash collisions** are when a hash function returns the same output for two distinct inputs.
    * All hash functions have this problem.
    * This is often accommodated for by having the hash tables be very large.
* Hashes are important for associated arrays and database indexing.

##### Big O Efficiency

* **Indexing** Hash Tables: O(1)
* **Search** Hash Tables: O(1)
* **Insertion** Hash Tables: O(1)

### Binary Tree

##### Definition

* Is a tree like data structure where every node has at most two children.
    * There is one left and right child node.

##### What you need to know

* Designed to optimize searching and sorting.
* A **degenerate tree** is an unbalanced tree, which if entirely one-sided is an essentially a linked list.
* They are comparably simple to implement than other data structures.
* Used to make **binary search trees**.
    * A binary tree that uses comparable keys to assign which direction a child is.
    * Left child has a key smaller than it's parent node.
    * Right child has a key greater than it's parent node.
    * There can be no duplicate node.
    * Because of the above it is more likely to be used as a data structure than a binary tree.

##### Big O Efficiency

* **Indexing** Binary Search Tree: O(log n)
* **Search** Binary Search Tree: O(log n)
* **Insertion** Binary Search Tree: O(log n)

## Search Basics

### Breadth First Search

##### Definition

* An algorithm that searches a tree (or graph) by searching levels of the tree first, starting at the root.
    * It finds every node on the same level, most often moving left to right.
    * While doing this, it tracks the children nodes of the nodes on the current level.
    * When finishing examining a level it moves to the left most node on the next level.
    * The bottom-right most node is evaluated last (the node that is deepest and is farthest right of it's level).

##### What you need to know

* Optimal for searching a tree that is wider than it is deep.
* Uses a queue to store information about the tree while it traverses a tree.
    * Because it uses a queue it is more memory intensive than **depth first search**.
    * The queue uses more memory because it needs to store pointers.

##### Big O Efficiency

* **Search** Breadth First Search: O(|E| + |V|)
* E is number of edges
* V is number of vertices

### Depth First Search

* An algorithm that searches a tree (or graph) by searching depth of the tree first, starting at the root.
    * It traverses left down a tree until it cannot go further.
    * Once it reaches the end of a branch it traverses back up trying the right child of nodes on that branch, and if possible left from that right children.
    * When finished examining a branch it moves to the node right of the root then tries to go left on all it's children until it reaches the bottom.
    * The right most node is evaluated last (the node that is right of all it's ancestors).

##### What you need to know

* Optimal for searching a tree that is deeper than it is wide.
* Uses a stack to push nodes onto.
    * Because a stack is LIFO it does not need to keep track of the nodes pointers and is therefore less memory intensive than **breadth first search**.
    * Once it cannot go further left it begins evaluating the stack.

##### Big O Efficiency

* **Search** Depth First Search: O(|E| + |V|)
* E is number of edges.
* V is number of vertices.

#### Breadth First Search Vs Depth First Search

* The simple to this question is that it depends on the size and shape of the tree.
    * For wide, shallow trees use Breadth First Search
    * For deep, narrow trees use Depth First Search

#### Nuances:

* Because BFS uses queues to store information about the nodes and it's children, it could use more memory than is available on your computer. (But you probably won't have to worry about this.)
* If using a DFS on a tree that is very deep you might go unnecessarily deep in the search.
* Breadth First Search tends to be a looping algorithm.
* Depth First Search tends to be a recursive algorithm.
         
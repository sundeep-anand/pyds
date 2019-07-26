
## Data Structure Basics

### Arrays

##### Definition

* Stores data elements based on an sequential, most commonly 0 based, index.
* Based on Tuples from set theory.
* They are one of the oldest, most commonly used data structure.
* Can be many-dimensional to represent matrices

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
* **Optimized Search** Linear Array: O(log n), Dynamic Array: O(log n) is Binary Search
* **Insertion** Linear Array: N/A, Dynamic Array: O(n)

### Linked List

##### Definition

* Stores data with **nodes** that points to other nodes.
    * Nodes, at its most basic it has one datum and one reference (another node).
    * A linked list *chains* nodes together by pointing one node's reference towards another node.

##### What you need to know

* Designed to optimize insertion and deletion, slow at indexing and searching.
* **Doubly linked list** has nodes that also reference the previous node.
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
* **Insertion** Linked Lists: O(n)

### Hash Table or Hash Map

##### Definition

* Stores data with key value pairs. And don't generally have an order.
* **Hash functions** accept arbitrary sized data and map it to fixed size data. The mapping is not guaranteed to be unique.
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
* Breadth-first search is guaranteed to find a shortest possible path through a graph. Depth-first search is not (and usually does not).
* DFS and BFS have no defined order in which the elements are searched.

(*In the specific case of searching a tree for a specific node, there is only one possible path, so both will return the same result, but search algorithms are very rarely used this way; typically, they operate on arbitrary graphs.*

*Additionally worth knowing is that most practically-used searching and pathfinding algorithms (e.g. Dijkstra's algorithm, A) are specializations of breadth-first search.*)

#### Worst case space complexity:

##### Data Structures:
* Array: O(n)
* Linked List: O(n)
* Hash Table: O(n)
* BST: O(n)

##### Sorting:
* Quick Sort: O(log(n))
* Merge Sort: O(n)
* Bubble Sort: O(1)

## Efficient Sorting Basics

### Merge Sort

##### Definition

* A comparision based sorting algorithm
    * Divides entire data set into groups of at most two.
    * Compares each number one at a time, moving the smallest number to left of the pair.
    * Once all pairs sorted then, it compares left most elements of the two left most pairs creating a sorted group of four with the smallest numbers on the left and the largest ones on the right.
    * This process is repeated until there is only one set.

##### What you need to know

* This is one of the most basic sorting algorithms.
* Know that it divides all the data into as small possible sets then compares them.

##### Big O Efficiency

* Best Case Sort: Merge Sort O(n log n)
* Average Case Sort: Merge Sort O(n log n)
* Worst Case Sort: Merge Sort O(n log n)

### Quick Sort

##### Definition

* A comparision based sorting algorithm
    * Divides entire dataset in half by selecting the middle element and putting all smaller elements to the left of the average.
    * It repeats this process on the left side until it is comparing only two elements at which point the left side is sorted.
    * When the left side is finished sorting it performs the same operation on the right side.
* Computer architecture favours the quicksort process.

(Edit: *Quicksort picks a random element from the dataset as the pivot element, then sorts all elements smaller before that and all greater than the pivot after it.
Then quicksort is executed on the part left of the pivot and right of it*.)

##### What you need to know

* While it has the same Big O as (or worse in some cases) many other sorting algorithms it is often faster in practice than merge sort.
* Know that it halves the data set by the average continuously until all the information is sorted.

##### Big O Efficiency

* Best Case Sort: Quick Sort: O(n)
* Average Case Sort: Quick Sort: O(n log n)
* Worst Case Sort: Quick Sort: O(n^2)

### Bubble Sort

##### Definition

* A comparision based sorting algorithm
    * It iterates left to right comparing every couplet, moving the smaller element to the left.
    * It repeats this process until it no longer moves an element to the left.

##### What you need to know

* While it is very simple to implement, it is the least efficient of these three sorting methods.
* Know that it moves one space to the right comparing two elements at a time and moving the smaller on to left.

##### Big O Efficiency

* Best Case Sort: Bubble Sort: O(n)
* Average Case Sort: Bubble Sort: O(n^2)
* Worst Case Sort: Bubble Sort: O(n^2)

#### Merge Sort vs Quick Sort

* Quick Sort is likely faster in practice.
* Merge Sort divides the set into the smaller possible groups immediately then reconstructs the incrementally as it sorts the groupings.
* Quick Sort continually divides the set by the average, until the set is recursively sorted.

## Basic Types of Algorithms

### Recursive Algorithms

##### Definition

* An algorithm that calls itself in it's definition.
    * **Recursive case** is a conditional statement that is used to trigger the recursion.
    * **Base case** is a conditional statement that is used to break the recursion.

##### What you need to know

* **Stack level too deep** and **stack overflow**
    * If you have seen either of these from a recursive algorithm, you messed up.
    * It means that your base case was never triggered because it was faulty or the problem was so massive you ran out of stack before reaching it.
    * Knowing weather or not you will reach a base case is integral to correctly using recursion.
    * Often used in **Depth First Search**.

### Iterative Algorithms

##### Definition

* An algorithm that is called repeatedly but for a finite number of times, each time being a single iteration.
    * Often used to move incrementally through a data set.

##### What you need to know

* Generally you will see iteration as loops: for, while and until statements.
* Think of iteration as moving one at a time through a set.
* Often used to move through an array.

##### Recursion vs Iteration

* The differences between recursion and iteration can be confusing to distinguish since both can be used to implement the other. But know that,
    * Recursion is, usually, more expressive and easier to implement.
    * Iteration uses less memory. (*that's not true when the compiler or interpreter supports tail-call elimination, or can otherwise optimize recursive functions.*)
* **Functional languages** tend to use recursion. (i.e. Haskell)
* **Imperative languages** tend to use iteration. (i.e. Ruby)

### Greedy Algorithm

##### Definition

* An algorithm that, while executing, selects only the information that meets a certain criteria.
* The general five components:
    * A candidate set, from which a solution is created.
    * A selection function, which chooses the best candidate to be added to the solution.
    * A feasibility function, that is used to determine if a candidate can be used to contribute to a solution.
    * An objective function, which assigns a valve to a solution, or a partial solution.
    * A solution function, which indicate when we have discovered a complete solution.

##### What you need to know

* Used to find the optimal solution to a given problem.
* Generally used on sets of data where only a small proportion of the information evaluated meets the desired result.
* Often a greedy algorithm can help reduce the Big O of an algorithm.

##### Pseudo Code of a Greedy Algorithm to find largest difference of any two numbers in an array

```bash
greedy algorithm (array)
    var largest difference = 0
    var new difference = find next difference (array[n], array[n+1])
    largest difference = new difference if new difference is > largest difference
    repeat above two steps until all the differences have been found
    return largest difference
``` 

This algorithm never needed to compare all the differences to one another, saving it an entire iteration.

### Stream I/O

##### Definition

* A stream is an abstract representation of sequence of bytes.
* It is usually buffered to prevent representing the entire sequence of bytes in memory at one time.
* Generally one-way and forward-only
* Has significant advantages over a standard array of bytes

##### What you need to know

* Can be stored:
    * In memory
    * Transferred over a network
    * On disk
    * In a database

* Advantages over byte arrays
    * Efficient use of memory
    * Smaller memory footprint

* Uses
    * Transferring files between persistence locations
    * Compression / Decompression
    * Encryption / Decryption
    * Throttling

* Can be chained
* Some are one-way (NetworkStream, CipherStream, etc), others can seek in either direction.


### Summary

S.No. | Name | Indexing | Search | Insertion | Optimized Search
----- | ---- | -------- | ------ | --------- | ----------------
1 | Linear Array | O(1) | O(n) | N/A | O(log n)
2 | Dynamic Array | O(1) | O(n) | o(n) | O(log n)
3 | Linked List | O(n) | O(n) | O(1) | O(n)
4 | Hash Table | O(1) | O(1) | O(1) | 
5 | Binary Tree | O(log n) | O(log n) | O(log n) | 
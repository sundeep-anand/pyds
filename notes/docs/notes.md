# Notes

## CH 1: Introduction

*find the complexity of any given algorithm*

#### 1.1 Variables

Variables are names (x and y) of the placeholders for representing data.

#### 1.2 Data Types

A set of data with predefined values, example: integer, floating point, unit number, character, string, etc. In memory we combine 2 bytes (16 bits) and call it an integer. Similarly, 4 bytes (32 bits) for float.

* System defined data types (Primitive data types) `int`, `float`, `char`, `double`, `bool`, etc.
* User defined data types `structures`, `union`, `classes`

#### 1.3 Data Structures

A special format for organizing and storing data so that it can be used efficiently. Example `arrays`, `files`, `linked list`, `stacks`, `queues`, `trees`, `graphs` and so on.

* Linear data structure: Linked List, Stacks and Queues.
* Non-linear data structure: Trees and Graphs.

#### 1.4 Abstract Data Types (ADTs)

When we combine the data structures with their operations.
An ADT has two parts:

  * Declaration of data
  * Declaration of operations.
 
Few examples are `Linked Lists`, `Stacks`, `Queues`, `Priority Queues`, `Binary Trees`, `Dictionaries`, `Disjoint Sets (Union and Find)`, `Hash Tables`, `Graphs` and many others.

#### 1.5 What is an Algorithm? 1.6 Why the Analysis of Algorithms?

The step-by-step unambiguous instructions to solve a given problem. Criteria:

* Correctness (*Does the algorithm give solution to the problem in a finite number of steps?*)
* Efficiency (*How much resources - memory and time - does it take to execute?*)

Helps us to determine which algorithm is most efficient in terms of time and space consumed.

#### 1.8 What is Running Time Analysis?

The process of determining how processing time increases as the size of the problem (input size) increases. Common types:

* Size of an array
* Polynomial degree
* Number of elements in a matrix
* Number of bits in the binary representation of the input
* Vertices and edges in a graph

#### 1.9 How to compare Algorithms

Let us assume that we express the running time of a given algorithm as a function of the input size **n** (*i.e. f(n)*) and compare these different functions corresponding to running times. This kind of comparison is independent of machine time, programming style, etc.

#### 1.10 What is rate of growth?

The rate at which the running time increases as a function of input is called *rate of growth*. n<sup>4</sup> + 2n<sup>2</sup> + 100n + 500 ~ n<sup>4</sup>

#### 1.11 Commonly Used Rates of Growth

Time Complexity | Name | Example
--- | --- | ---
1 | Constant | Adding an element to the front of the linked list
log n | Logarithmic | Finding an element in a sorted array
n | Linear | Finding an element in a unsorted array
n log n | Linear Logarithmic | Sorting n items by `divide-n-conquer` - MergeSort
n<sup>2</sup> | Quadratic | Shortest path between two nodes in a graph
n<sup>3</sup> | Cubic | Matrix Multiplication
2<sup>n</sup> | Exponential | The Towers of Hanoi problem





___

## CH 0: Organization of Chapters

#### Three things required to build good understanding of data structure are:

* How the information is arranged in the memory of the computer?
* Become familiar with the algorithms for manipulating the information contained in the data structure.
* Understand the performance characteristics of the data structure.
    * to select a suitable data structure for a particular application.

### Definitions

**Recursion** is the process of defining a function or calculating a number by the repeated application of an algorithm.

**Backtracking** The solution process consists of working through a sequence of decision points in which each choice leads further along some path (example Trees or Graphs). In case of incorrect choice somewhere along the way, developer has to backtrack to a previous decision point and try a different path. Backtracking algorithms use this approach, moreover, it's a form of recursion.

**Linked Lists** (dynamic) Number of nodes can grow and shrink on demand. Used to create trees, graphs, hashing, etc.

**Stacks** (abstract) A container of objects that are inserted and removed according to the last-in-first-out `LIFO` principle. Applications:

* Internal creation of function parameters and local variables.
* Compiler's syntax check for matching braces; Support for recursion.
* Can act as an auxiliary data structure for other abstract data types.

**Queues** (abstract) Similar to *stacks* but follow `FIFO`. Applications:

* In OS, for controlling access to shared system resources such as printers, files, communication lines, disks and tapes.
* Computer systems must often provide a holding area `buffer` for messages between two processes, two programs, or even two systems.
* Can act as an auxiliary data structure for other abstract data types.

**Trees** (abstract) Data organization to make the data insertion or deletion or search faster. Applications:

* Library db, School's student db, employ or patient db; any db would be implemented using trees.
* OS file systems; Can act as an auxiliary data structure for other abstract data types.

Tree variants are classified by the number of children and the way of interconnecting them.

**Priority Queues** (abstract) Maintain a collection of prioritized elements. Application: operating systems often use a priority queue for the ready queue of processes to run on the CPU.

**Graphs** (fundamental - non linear) Collection of nodes `vertices` and their connections `edges`. Used to model many types of relations and processes.

**Disjoint Set** (abstract) Collection of disjoint sets `partition`. Example: *Motorola*, *YouTube*, and *Android* are all members of the *Google* set.
Two operations:

* Union: merging of two sets into one!
* Find Query: takes an item and returns which set it belongs to. Application: Maze generation and Kruskal's algo for computing the minimum spanning tree of a graph.

**Sorting** Arranges the elements of a list in a certain order; sometimes reduces the complexity of problem significantly. Applications: searching elements and db algorithms.

**Searching** The process of finding an item with specified properties from a collection of items. Data organization improves the searching process.

**Selection Algo** (*k<sup>th</sup>* order statistic) Finding the minimum, maximum and median elements in a given list.

**Symbol Tables** (dictionaries) Examples: spelling checker, data dictionary found in DBMS, symbol tables generated by loaders, assemblers, and compilers, as well as routing tables in networking components (DNS Lookup).

**Hashing** Technique used for storing and retrieving information as fast as possible. Used in optimal search and symbol tables. The worst case complexity of hashing is O(n), but it gives O(1) on the average.

**String Algo** Operations like auto completion (on CLI or browser) or string matching need a data structure which stores the string data efficiently.

**Algo Design Techniques** There are different ways of classifying the algorithms like Greedy, Divide and Conquer, and Dynamic Programming.

**Greedy Algo** (*single-minded* algorithm) Process that looks for a simple, easy to implement solutions to complex, multi-step problems by deciding which next step will provide the most obvious benefit. Example: selection sort, Prim's algorithms, Kruskal's algorithms, Dijkstra algorithm, Huffman coding algorithm etc.

**Divide and Conquer** Principles: (examples include binary search, merge sort, etc.)

* Divide - break the problem into several subproblems that are similar to the original problem but smaller in size.
* Conquer - solve the subproblems recursively.
* Base case - If the subproblem size is small enough then solve the subproblem directly without more recursion.
* Combine - the solutions to create a solution for the original problem.

**Dynamic Programming** (optimization over plain recursion) Breaking down a complex problem into a collection of simpler subproblems. Solving each of those and storing their solutions using a memory-based data structure (array, map, etc).

**Complexity Classes** (resources required during computation - time vs space) Classification is done based on the running time (or memory) that an algorithm takes for solving the problem.

**Bit-wise Hacking** Applications:

* Kind of file format or network protocol that uses individual bits or group of bits to represent pieces of information.
* Setting individual pixels on the screen by directly manipulating the video memory, where every pixel's color is represented by 1 or 4 bits.
* Compute some kind of checksum (possibly, parity or CRC) or hash value.

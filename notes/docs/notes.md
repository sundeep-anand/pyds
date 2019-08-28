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

The rate at which the running time increases as a function of input is called *rate of growth*. <code>n<sup>4</sup> + 2n<sup>2</sup> + 100n + 500 ~ n<sup>4</sup></code>

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

#### 1.12 Types of Analysis

Algorithm can be represented with multiple expressions: one for the case where it takes less time (*best case*) and another for the case where it takes more time (*worst case*).

* Worst case: Defines the input for which the algorithm takes a long time (slowest time to complete). f(n) = n<sup>2</sup> + 500
* Best case: Defines the input for which the algorithm takes the least time (fastest time to complete). f(n) = n + 100n + 500
* Average case: Run the algorithm many times, using many different inputs that come from some distribution that generates these inputs, compute the total running time (by adding the individual times), and divide by the number of trails.

```text
Lower Bound <= Average Time <= Upper Bound
```

#### 1.13 Big-O Notation

Represented as `f(n) = O(g(n))`, where g(n) gives the maximum rate of growth for f(n) at larger values of n. n<sub>0</sub>, called as threshold, is the point from which we need to consider the rate of growth for a given algorithm. Defined as 

<code>O(g(n)) = {f(n): there exist positive constants c and n<sub>0</sub> such that 0 <= f(n) <= cg(n) for all n >= n<sub>0</sub>}</code>

#### 1.15 Omega-Ω Notation

This notation gives the tighter lower bound of the given algorithm and we represent it as `f(n) = Ω(g(n))`. That means, at larger values of n, the tighter lower bound of f(n) is g(n). 2n = Ω(n), n<sup>3</sup> = Ω(n<sup>3</sup>), logn = Ω(logn) Defined as

<code>Ω(g(n)) = {f(n): there exist positive constants c and n<sub>0</sub> such that 0 <= cg(n) <= f(n) for all n >= n<sub>0</sub>}</code>

#### 1.16 Theta-Θ Notation

This notation decides whether the upper and lower bounds of a given function (algorithm) are the same. If the upper bound (O) and the lower bound (Ω) give the same result, then the Θ notation will also have the same rate of growth. Defined as

<code>Θ(g(n)) = {f(n): there exist positive constants c<sub>1</sub>, c<sub>2</sub> and n<sub>0</sub> such that 0 <= c<sub>1</sub>g(n) <= f(n) <= c<sub>2</sub>g(n) for all n >= n<sub>0</sub>}</code>

##### For analysis (`best case`, `worst case` and `average`), we try to give the upper bound (O) and lower bound (Ω) and average running time (Θ). We generally focus on upper bound (O). g(n) is the asymptotic curve for f(n).

#### 1.18 Guidelines for Asymptotic Analysis

* **Loops**: The running time of a loop is the running time of the statements inside the loop (including tests) multiplied by the number of iterations. `Total time = a constant c x n = cn = O(n)`
* **Nested Loops**: Total running time is the product of the sizes of all the loops. <code>Total time = c x n x n = cn<sup>2</sup> = O(n<sup>2</sup>)</code>
* **Consecutive statements**: Add the time complexities of each statement. <code>Total time = c<sub>0</sub> + c<sub>1</sub>n + c<sub>2</sub>n<sup>2</sup> = O(n<sup>2</sup>)</code>
* **If-then-else statements**: Worst-case running time: the test, plus either the *then* part *or* the else part. <code>Total time = c<sub>0</sub> + c<sub>1</sub> * n = O(n)</code>
* **Logarithmic complexity**: An algorithm is O(logn) if it takes a constant time to cut the problem size by a fraction (usually by <sup>1</sup>/<sub>2</sub>). <code>Total time = log(2<sup>k</sup>) = klog2 = O(logn)</code> An example: binary search (finding a word in a dictionary of n pages) (**1**) Look at the center point in the dictionary (**2**) Is the word towards the left or right of the center? (**3**) Repeat the process with the left or right part of the dictionary until the word is found.

#### 1.21 Master Theorem for Divide and Conquer Recurrences

Divide and conquer algorithms divide the problem into sub-problems, each of which is a part of the original problem, and then perform some additional work to compute the final answer. Example: for a merge sort algorithm, running time equation could be <code>T(n) = 2T(<sup>n</sup>/<sub>2</sub>) + O(n)</code>

#### 1.26 Amortized Analysis

Amortized analysis is a worst-case analysis, but for a sequence of operations rather than for individual operations. It generally applies to a method that consists of a sequence of operations, where the vast majority of the operations are cheap, but some of the operations are expensive.

When one event in a sequence affects the cost of later events:

* One particular task may be expensive.
* But it may leave data structure in a state that the next few operations become easier.

**Example**: Let us consider an array of elements from which we want to find the k<sup>th</sup> smallest element. We can solve this problem using sorting. After sorting the given array, we just need to return the k<sup>th</sup> element from it. The cost of performing the sort (assuming comparison based sorting algorithm) is O(nlogn). If we perform *n* such selections then the average cost of each selection is O(nlogn/n) = O(logn). This clearly indicates that sorting once is reducing the complexity of subsequent operations.

*Observations*:

* While the recurrence relation looks exponential, the solution to the recurrence relation here gives a different result.

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

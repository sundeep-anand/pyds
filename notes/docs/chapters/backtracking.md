# CH 2: Recursion and Backtracking

---

#### 2.2 2.3 What is recursion? and Why?

A recursive method solves a problem by calling a copy of itself to work on a smaller problem. It is important to ensure that the recursion terminates. The sequence of smaller problems must eventually converge on the base case. Generally, loops are turned into recursive functions when they are compiled or interpreted.

#### 2.5 Recursion and Memory

Each recursive call makes a new copy of that method (actually only the variables) in memory. Once a method ends (that is, returns some data), the copy of that returning method is removed from memory.

#### 2.6 Recursion versus Iteration

<strong>Recursion</strong>

* Terminates when base case is reached.
* Each recursive call requires extra space on the stack frame (memory).
* If we get infinite recursion, the program may run out of memory and result in stack overflow.
* Solutions to some problems are easier to formulate recursively.

Examples: Fibonacci Series, Factorial Finding, Merge Sort, Quick Sort, Binary Search, Tree Traversals, Graph Traversals, Dynamic Programming, Divide and Conquer, Towers of Hanoi, and Backtracking Algorithms

<strong>Iteration</strong>

* Terminates when a condition proven to be false.
* Each iteration does not require an extra space.
* An infinite loop could loop forever since there is no extra memory being created.
* Iterative solutions to a problem may not always be as obvious as a recursive solution.

#### 2.10 What is Backtracking?

Backtracking systematically searches for a solution to a problem among all available options. We start with one possible option out of many available options and try to solve the problem if we are able to solve the problem with the selected move then we will print the solution else we will backtrack and select some other option and try to solve it. Backtracking can be thought of as a selective tree/graph traversal method.

* Sometimes the best algorithm for a problem is to try all possibilities.
* This is always slow, but there are standard tools that can be used to help.
* Tools: algorithms for generating basic objects, such as binary strings [2<sup>n</sup> possibilities for n-bit string], permutations `[n!]`, combinations `[n!/r!(n-1)!]`, general strings [k -ary strings of length n has k<sup>n</sup> possibilities], etc...
* Backtracking speeds the exhaustive search by pruning.

Example Algorithms:

* Binary Strings: generating all binary strings
* Generating k -ary Strings
* N-Queens Problem
* The Knapsack Problem
* Generalized Strings
* Hamiltonian Cycles
* Graph Coloring Problem

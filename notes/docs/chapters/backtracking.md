# CH 2: Recursion and Backtracking

---

## Notes
<div style="padding: 1%;background-color: #f2fafc;margin-bottom: 1%"></div>

#### 2.2 What is Recursion?

A recursive method solves a problem by calling a copy of itself to work on a smaller problem. It is important to ensure that the recursion terminates. The sequence of smaller problems must eventually converge on the base case. 

#### 2.3 Why Recursion?

Generally, loops are turned into recursive functions when they are compiled or interpreted.

#### 2.5 Recursion and Memory

Each recursive call makes a new copy of that method (actually only the variables) in memory. Once a method ends (that is, returns some data), the copy of that returning method is removed from memory.

```
def print_func(n):
    if n == 0:                  # this is the terminating base case
        return 0
    else:
        print n
        return print_func(n-1)  # recursive call to itself again
    print(print_func(4))
```

#### 2.6 Recursion versus Iteration

<strong>Recursion</strong>

* Terminates when base case is reached.
* Each recursive call requires extra space on the stack frame (memory).
* If we get infinite recursion, the program may run out of memory and result in stack overflow.
* Solutions to some problems are easier to formulate recursively.

<strong>Iteration</strong>

* Terminates when a condition proven to be false.
* Each iteration does not require an extra space.
* An infinite loop could loop forever since there is no extra memory being created.
* Iterative solutions to a problem may not always be as obvious as a recursive solution.

#### 2.7 Notes on Recursion

* Recursive algorithms have two types of cases: **recursive** cases and **base** cases. 
* Every recursive function case must terminate at a base case.
* Generally, iterative solutions are more efficient than recursive solutions (*due to overhead of function calls*).
* A recursive algorithm can be implemented without recursive function calls using a stack, but it's usually more trouble than its worth.
* For some problems, there are no obvious iterative algorithms. They're best suited for recursive solutions.

#### 2.8 Example Algorithms of Recursion

* Fibonacci Series, Factorial Finding
* Merge Sort, Quick Sort
* Binary Search
* Tree Traversals and other problems: InOrder, PreOrder, PostOrder
* Graph Traversals: Depth First Search and Breadth First Search
* Dynamic Programming Examples
* Divide and Conquer Algorithms
* Tower of Hanoi
* Backtracking Algorithms

#### 2.10 What is Backtracking?

Backtracking systematically searches for a solution to a problem among all available options. We start with one possible option out of many available options and try to solve the problem if we are able to solve the problem with the selected move then we will print the solution else we will backtrack and select some other option and try to solve it. Backtracking can be thought of as a selective tree/graph traversal method.

* Sometimes the best algorithm for a problem is to try all possibilities.
* This is always slow, but there are standard tools that can be used to help.
* Tools: algorithms for generating basic objects, such as binary strings [2<sup>n</sup> possibilities for n-bit string], permutations `[n!]`, combinations `[n!/r!(n-1)!]`, general strings [k -ary strings of length n has k<sup>n</sup> possibilities], etc...
* Backtracking speeds the exhaustive search by pruning.

<strong>Example Algorithms:</strong>

* Binary Strings: generating all binary strings
* Generating k -ary Strings
* N-Queens Problem
* The Knapsack Problem
* Generalized Strings
* Hamiltonian Cycles
* Graph Coloring Problem

## Problems
<div style="padding: 1%;background-color: #f2fafc;margin-bottom: 1%"></div>

#### Problem-1: Discuss Towers of Hanoi puzzle.

The Towers of Hanoi consists of three rods (or pegs or towers) and a number of disks of different sizes which can slide onto any rod. The puzzle starts with the disks on one rod in ascending order of size, the smallest at the top, thus making a conical shape. The objective of the puzzle is to move the entire stack to another rod, satisfying the following rules:

* Only one disk may be moved at a time.
* Each move consists of taking the upper disk from one of the rods and sliding it onto another rod, on top of the other disks that may already be present on that rod.
* No disk may be placed on top of a smaller disk.

Algorithm:

* Move the top `n-1` disks from Source to Auxiliary tower,
* Move the n<sup>th</sup> disk from Source to Destination tower,
* Move the `n-1` disks from Auxiliary tower to Destination tower.
* Transferring the top `n-1` disks from Source to Auxiliary tower can again be thought of as a fresh problem and can be solved in the same manner.

```python

def towers_of_hanoi(numberOfDisks, startPeg=1, endPeg=3):
    if numberOfDisks:
        towers_of_hanoi(numberOfDisks-1, startPeg, 6-startPeg-endPeg)
        print("Move disk %d from peg %d to peg %d" % (numberOfDisks, startPeg, endPeg))
        towers_of_hanoi(numberOfDisks-1, 6-startPeg-endPeg, endPeg)

towers_of_hanoi(numberOfDisks=4)

```

#### Problem-4: Generate all the strings of length n drawn from 0... k-1.

Let us assume we keep current k-ary string in an array A[0.. n-1].

```python

def range_to_list(k):
    result = []
    for i in range(0, k):
        result.append(str(i))
    return result

def base_k_strings(n, k):
    if n == 0: return []
    if n == 1: return range_to_list(k)
    return [digit+bitstring for digit in base_k_strings(1, k) for bitstring in base_k_strings(n-1, k)]

print base_k_strings(4, 3)

```
Complexity would be O(k<sup>n</sup>).

#### Problem-6: Finding the length of connected cells of 1s (regions) in a matrix of 0s and 1s.

```python

def getval(A, i, j, L, H):
    if(i < 0 or i >= L or j < 0 or j >= H):
        return 0
    else:
        return A[i][j]

def find_max_block(A, r, c, L, H, size):
    global maxsize
    global cntarr
    if(r >= L or c >= H):
        return
    cntarr[r][c] = 1
    size += 1
    if (size > maxsize):
        maxsize = size
    # search in eight directions
    direction = [[-1, 0], [-1, -1], [0, -1], [1, -1], [1, 0], [1, 1], [0, 1], [-1, 1]]
    for i in range(0,7):
        newi = r + direction[i][0]
        newj = c + direction[i][1]
        val = getval(A, newi, newj, L, H)
        if (val > 0 and (cntarr[newi][newj] == 0)):
            find_max_block(A, newi, newj, L, H, size)
    cntarr[r][c] = 0

def get_max_ones(A, rmax, colmax):
    global maxsize
    global size
    global cntarr

    for i in range(0, rmax):
        for j in range(0, colmax):
            if(A[i][j] == 1):
                find_max_block(A, i, j, rmax, colmax, 0)

    return maxsize

```

#### Problem-7: Path finding problem

Given an n*n matrix of blocks with a source upper left block, we want to find the path from the source to the destination (_the lower right block_). We can only move downwards and to the left. Also a path is given by 1 and a wall is given by 0.

**Algorithm**:

If we have reached the destination point return an array containing only the position of the destination else

1. Move in the forwards direction and check if this leads to a solution.
2. If option a does not work, then move down.
3. If either work, add the current position to the solution obtained at either 1 or 2.

```python

def path_finder(Matrix, position, N):
    # returns a list of the paths taken
    if position == (N-1, N-1):
        return [(N-1, N-1)]
    x, y = position
    if x + 1 < N and Matrix[x+1][y] == 1:
        a = path_finder(Matrix, (x + 1, y), N)
        if a != None:
            return [(x, y)] + a

    if y + 1 < N and Matrix[x][y+1] == 1:
        b = path_finder(Matrix, (x, y + 1), N)
        if b != None:
            return [(x, y)] + b

Matrix = [[1,1,1,1,0],[0,1,0,1,0],[0,1,0,1,0],[0,1,0,0,0],[1,1,1,1,1]]
print(path_finder(Matrix, (0,0), 5))

```

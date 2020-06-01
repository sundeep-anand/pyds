# Problems

### CH 2: Recursion and Backtracking

#### Problem-1: Discuss Towers of Hanoi puzzle.

The Towers of Hanoi consists of three rods (or pegs or towers) and a number of disks of different sizes which can slide onto any rod. The puzzle starts with the disks on one rod in ascending order of size, the smallest at the top, thus making a conical shape. The objective of the puzzle is to move the entire stack to another rod, satisfying the following rules:

* Only one disk may be moved at a time.
* Each move consists of taking the upper disk from one of the rods and sliding it onto another rod, on top of the other disks that may already be present on that rod.
* No disk may be placed on top of a smaller disk.

Algorithm:

* Move the top `n-1` disks from Source to Auxiliary tower,
* Move the n<sup>th<sup> disk from Source to Destination tower,
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

#### Problem-7: Path finding problem

Given an nxn matrix of blocks with a source upper left block, we want to find the path from the source to the destination (the lower right block). We can only move downwards and to the left. Also a path is given by 1 and a wall is given by 0.

Algorithm:

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
print path_finder(Matrix, (0,0), 5)

```

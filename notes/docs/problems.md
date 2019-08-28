# Problems

## CH 1: Introduction

#### Problem-28: Write a recursive function for the running time T(n) of the function given below.

```python

def function(n):
    count = 0
    if n <= 0:
        return
    for i in range(0, n):           # Outer loop executes n times
        for j in range(0, n):       # Inner loop executes n times
            count = count + 1
    function(n-3)                   # Recursive call
    print(count)

function(20)

```

The recursive for this call is <code>T(n) = T(n-3) + cn<sup>2</sup></code> for some constant c > 0. Using Substraction and Conquer master theorem, we get <code>T(n) = Θ(n<sup>3</sup>)</code>

#### Problem-34: Consider the following program.

```python

def Fib(n):
    if n == 0: return 0
    elif n == 1: return 1
    else: return Fib(n-1) + Fib(n-2)

print(Fib(3))

```

The recurrence relation for the running time of this program is: `T(n) = T(n-1) + T(n-2) + c`. Note T(n) has two recurrence calls indicating a binary tree. Each step recursively calls the program for n reduced by 1 and 2, so the depth of the recurrence tree is O(n). The number of leaves at depth n is 2<sup>n</sup> since this is a full binary tree, and each leaf takes at least O(1) computations for the constant factor. Running time is clearly exponential in n and it is O(2<sup>n</sup>).

#### Problem-38: What is the running time of the following recursive function?

```python

def function(n):
    if n <= 0:
        return 0
    for i in range(0, 3):
        function(n-1)

function(20)

```

<code>T(n) = c + 3T(n-1), if n > 1 = Θ(3<sup>n</sup>)</code>


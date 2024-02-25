# Lecture 1 Analysis

##### Algorithms
A set of instructions to oslva a problem

##### Data Structures
A format for manipulating (storing, working with, managing or structuring) data or information.

###### Arrays
An array is a collection of items of same data type (int, str, bool, etc.) 
```
array = [2, 4, 10, 5, 15, 3]
         0  1  2   3  4   5     //Array Indexes
```

In C language, arrays have fixed sizes.

###### Linked Lists
A linked list is a method that uses a list of nodes to store data and can store many different data types (Object Oriented Programming). It is not restrained in the sense that it can be dynamically sized, however, it is much less efficient to access elements in the linked list compared to accessing elements in an array.


##### Pseudocode
There is no particular fixed syntax for pseudocode because the main purpose is to communicate/explain code. By doing this, we can focus on explaining the logic of an algorithm.
Here is an example of an algorithm that sorts an unsorted list into a sorted list in ascending order:
```
// Sorting using Insertion Sort Algorithm

for i = 1 to size(A) - 1 do
    key = A[i]
    j = i - 1
    while j >= 0 and A[j] > key do
        A[j+1] = A[j]
        j = j - 1
    A[j+1] = key
```

###### General Syntax
Control Flow
- if ... then ... [else ...]
- while ... do ...
- repeat ... until ...
- for ... do ...

Method call
- method(arg, arg[arg ..., arg ...])

Return Value
- return _expression_

##### Three Steps Before Implementation
1. Computational Problem
    - Define the computational task
    - Specify the expected input and output
2. Algorithm
    - Step-by-step instructions to turn input into output
    - Usually uses pseudocode to explain the logic
    - NOT implementation
    - There will always be many solutions to every problem
3. Correctness and Complexity Analysis
    - Formal proof that the algorithm completes te computational task
    - Analysis on the resources it uses

###### Example
Computational Problem:
Given an array A of integers, we need to return the maximum value
    - Input: array A
    - Output: Maximum Value

Algorithm
```
max = - infinity
for i = 0 to n - 1 do
    if A[i] > max then
        max = A[i]
return max
```
Correctness and Complexity Analysis
Proof by Induction: After the second iteration, max stores the maximum value of the first two elements as the algorithm compares the first two values and stores the largest value in max. If we maintain that this is true for second iteration, we show that it holds after the (2 + 1)th iteration. In the (2 + 1)th iteration we compare max to A[2 + 1], and update max if A[2 + 1] is larger. This can be applies to the (2 + 1 + 1)th iteration and so on. Hence, it can be said that max is the maximum of the first x + 1 elements.
This implies that after size(A) iterations, max contains the maximum value of all elements in array A.

The initialization, comparison and assignment inside the loop and return statement run in O(1) time. The for loop has a constant number of operations per iteration, therefore the loop has a time complexity of O(n). Summing up these complexities gives us O(n). Hence the time complexity is O(n).

###### Example
Computational Problem:
Given an array A with _n_ integer values A[0], A[1], ..., A[n - 1], find indices $0 \leq i \leq j < n$ maximizing A[i] + A[i + 1] + ... + A[j].

Algorithm
- Naive Algorithm (Brute force method, trying all combinations)
```
curr_val = 0
curr_ans = (None, None)

for i = 0 to n - 1 do
    for j = i to n - 1 do
        // Compute A[i] + A[i + 1] + ... + A[j]
        s = 0
        for k = i to j do
            s = s + A[k]
        // Compare to current maximum
        if s > curr_val then
            curr_val = s
            curr_ans = (i, j)
return curr_ans
```
- Naive with Preprocessing Algorithm (Brute force method, but more efficient)
```
curr_val = 0
curr_ans = (None, None)
B = new array with size n - 1
B[0] = 0
for i = 1 to n - 1
    B[i] = B[i - 1] + A[i - 1]
for i = 0 to n - 1 do
    for j = i to n - 1 do
        // Compute A[i] + A[i + 1] + ... + A[j]
        s = B[j + 1] - B[i]
        if s > curr_val then
            curr_val = s
            curr_ans = (i, j)
return curr_ans
```

Correctness and Complexity Analysis
Simply put, in the naive algorithm, there are 3 for loops scanning the same array, meaning that the algorithm will run iterations over iterations to the third degree. Hence, it has a time complexity of $O(n^3)$.

In the Naive with Preprocessing Algorithm, there are 3 for loops, 2 of which scan array B and 1 of which scans array A. Hence,the time complexity for scanning array B would be $O(n^2)$ and the time complexity for scanning array A would be $O(n)$. Given that Big-O Notation represents the asymptotic upper bound, the concluded time complexity for this algorithm is $O(n^2)$.


##### Time Complexity

###### Time Complexity Definitions
Time complexity is a concept that describes the growth rate of an algorithm's resource usage.
- Big-O Notation
    - Written as: $O(n)$
    - This notation is most commonly used as it describes the "worst case scenario", professionally called the asymptotic upper bound, of an algorithm's time complexity.
- Omega Notation
    - Written as $\Omega(n)$ 
    - This notation represents the "best case scenario", professionally called the asymptotic lower bound, of an algorithms time complexity.
- Theta Notation
    - Written as $\Theta(n)$
    - This notation represents a "balanced/expected scenario", where it provides a range where the actual performance of the algorithm will lie.


###### Common Time Complexities

|Name        |Condition         |
|------------|------------------|
|Constant    |$T(n)=O(1)$       |
|Logarithmic |$T(n)=O(\log n)$  |
|Linear      |$T(n)=O(n)$       |
|Quasi-Linear|$T(n)=O(n \log n)$|
|Quadratic   |$T(n)=O(n^2)$     |
|Cubic       |$T(n)=O(n^3)$     |
|Exponential |$T(n)=O(c^n)$     |



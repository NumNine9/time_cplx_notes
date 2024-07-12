# time_cplx_notes

### Notes on Time and Space Complexity

#### **Introduction**
Time and space complexity are critical concepts in computer science, particularly in the analysis of algorithms. They help determine the efficiency of an algorithm in terms of time (how long it takes to run) and space (how much memory it requires).

#### **Time Complexity**

**1. Definition**
Time complexity is a measure of the amount of time an algorithm takes to complete as a function of the size of its input. It's usually expressed using Big O notation, which describes the upper limit of the algorithm's running time.

**2. Big O Notation**
Big O notation describes how the runtime of an algorithm grows with the input size, \( n \). Common time complexities include:
- \( O(1) \): Constant time
- \( O(\log n) \): Logarithmic time
- \( O(n) \): Linear time
- \( O(n \log n) \): Linearithmic time
- \( O(n^2) \): Quadratic time
- \( O(2^n) \): Exponential time
- \( O(n!) \): Factorial time

**3. Examples and Analysis**

**Example 1: Constant Time Complexity (O(1))**

```python
def constant_time_example(arr):
    return arr[0]
```
- **Analysis**: This function always takes the same amount of time to execute, regardless of the size of `arr`. It accesses a single element directly.

**Example 2: Linear Time Complexity (O(n))**

```python
def linear_time_example(arr):
    for element in arr:
        print(element)
```
- **Analysis**: The function iterates over each element of the array `arr` exactly once. Therefore, the time it takes to run grows linearly with the size of the input `arr`.

**Example 3: Quadratic Time Complexity (O(n^2))**

```python
def quadratic_time_example(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            print(arr[i], arr[j])
```
- **Analysis**: This function contains a nested loop, where each loop iterates over `arr`. If `arr` has `n` elements, the inner loop runs `n` times for each of the `n` iterations of the outer loop, resulting in \( n \times n = n^2 \) iterations.

#### **Space Complexity**

**1. Definition**
Space complexity is a measure of the amount of memory an algorithm uses relative to the size of the input data. Like time complexity, it is often expressed using Big O notation.

**2. Analysis of Space Complexity**
Space complexity includes both the space needed to store the input data and any additional space required by the algorithm.

**3. Examples and Analysis**

**Example 1: Constant Space Complexity (O(1))**

```python
def constant_space_example(arr):
    sum = 0
    for element in arr:
        sum += element
    return sum
```
- **Analysis**: The function uses a fixed amount of extra space (for the variable `sum`), regardless of the size of `arr`.

**Example 2: Linear Space Complexity (O(n))**

```python
def linear_space_example(n):
    result = []
    for i in range(n):
        result.append(i)
    return result
```
- **Analysis**: The function creates a list `result` that stores `n` elements. Therefore, the space required grows linearly with the input `n`.

#### **Combining Time and Space Complexity**

**Example: Merge Sort Algorithm**

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left_half = merge_sort(arr[:mid])
    right_half = merge_sort(arr[mid:])

    return merge(left_half, right_half)

def merge(left, right):
    sorted_array = []
    while left and right:
        if left[0] <= right[0]:
            sorted_array.append(left.pop(0))
        else:
            sorted_array.append(right.pop(0))

    sorted_array.extend(left if left else right)
    return sorted_array
```
- **Time Complexity**: Merge sort divides the array into halves and merges them. The division takes \( O(\log n) \) and merging takes \( O(n) \), resulting in a total time complexity of \( O(n \log n) \).
- **Space Complexity**: Merge sort requires additional space to hold the divided arrays and the merged result, resulting in a space complexity of \( O(n) \).

### Summary

Understanding time and space complexity is essential for evaluating the efficiency of algorithms. Here's a quick recap:
- **Time Complexity**: How the runtime grows with input size.
- **Space Complexity**: How memory usage grows with input size.
- **Big O Notation**: Commonly used to express both time and space complexity.

Using these concepts, you can analyze and compare different algorithms to choose the most efficient one for your problem.

### Additional Example: Binary Search Algorithm

**Binary Search**: An algorithm to find the position of a target value within a sorted array.

```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1
```
- **Time Complexity**: Binary search repeatedly divides the search interval in half. This gives it a logarithmic time complexity, \( O(\log n) \).
- **Space Complexity**: Binary search uses a constant amount of space for the variables `low`, `high`, and `mid`, resulting in a space complexity of \( O(1) \).

These examples illustrate how time and space complexity can be analyzed for different algorithms, providing a foundation for understanding their efficiency and performance characteristics.

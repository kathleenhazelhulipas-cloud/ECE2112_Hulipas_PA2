# ECE2112_Hulipas_PA2
#### EXPERIMENT 2: NUMERICAL PYTHON (NUMPY)<br>**Submitted By: Kathleen Hazel L. Hulipas | 2ECE-A**
The content of this repository contains the _**Programming Assignment 2**_ for ECE2112 Advanced Computer Programming course A.Y. 2026 - 2027 which covers python problems from _**Module 2 - Numpy**_.

Objectives
---
At the end of this laboratory activity, the student should be able to:
  1. create and reshape NumPy arrays using appropriate NumPy functions;
  2. perform vectorized numerical operations on an ndarray;
  3. compute array statistics and use Boolean conditions to select elements; and
  4. save computed NumPy arrays as .npy files.

The code below is used to access the Numpy library:
```python
import numpy as np
```

A. REPRODUCIBLE NORMALIZATION PROBLEM
---
Create a reproducible random 5 × 5 integer ndarray named X. Use the following two statements before performing any calculation:
```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```
Normalize the complete array using
```math
Z = (X - \bar x) / \sigma
```
where ¯x is the mean of all 25 elements and σ is their population standard deviation as returned by NumPy’s default std() call. Store the normalized array in X_normalized

The following function and methods were used in this problem:
- `np.random.seed()` - used to initialize the random number generator
  
- `np.mean()` - built in function used to get the arithmetic mean of the chosen variable

  Example:
  ```python
  a = np.array([1,2,3])
  b = int(np.mean(a))
  b

  #result: 2
  #int was used to make the result as integer / whole number
  ```

- `np.std()` - built in function used to get the standard deviation of the chosen variable

  Example:
  ```python
  c = int(np.std(a))
  c

  #result: 0
  #int was used to make the result as integer / whole number
  ```

- `np.save('file name', array)` - used to save an array to a binary file in .npy format

These methods were used to create a single function that generates a random 5 × 5 integer array and gets the mean, standard deviation, and the X_normalized (Z-score):
```python
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

M = np.mean(X)
SD = np.std(X)

X_normalized = (X - M) / SD

np.save('X_normalized.npy', X_normalized)

print("\nX: \n", X)
print("\nX_normalized: \n", X_normalized)
print("\nMean of X_normalized: ", np.mean(X_normalized))
print("\nStandard Deviation of X_normalized: ", np.std(X_normalized))
```

B. CUBES DIVISIBLE BY 4 PROBLEM
---
Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named C. Thus, C begins with 1³ and ends with 100³.

Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in div by 4. Preserve NumPy’s normal row-major selection order.

The following function and methods were used in this problem:
- `np.arange(a, b, c)` - used to get the integers from a up to b (excluding b) and in c increments

  Example:
  ```python
  a = np.arange(2,10,2)
  a

  #result: array([2, 4, 6, 8])
  ```

- `.reshape(a,b)` - rearranges array to a rows and b columns

  Example:
  ```python
  b = np.array([(1,2,3),(4,5,6)])
  b = b.reshape(6,1).shape
  b

  #result: (6, 1)
  ```

- `A[equation]` - boolean condition where gets the A array and evaluates the equation enclosed in square brackets which will produce boolean values in the exact shape of A.

  Example:
  ```python
  c = np.array([(1,2,3),(4,5,6)])
  d = c[c % 3 == 0]
    #[(False, False, True), (False, False, True)]

  print(d)

  #result: [3 6]
  ```

- `np.save('file name', array)` - used to save an array to a binary file in .npy format

These methods were used to create a single function that gets the cube of the first 100 positive integers in a 10 × 10 ndarray and prints the elements divisible by 4:
```python
import numpy as np

C = ((np.arange(1, 101)**3)).reshape(10,10)

div_by_4 = C[C % 4 == 0]

np.save('div_by_4.npy', div_by_4)

print("Shape of C: ", C.shape)
print("\ndiv_by_4 array: \n", div_by_4)
print("\nNumber of Selected Elements: ", div_by_4.size)
```

C. ABOVE-MEAN SQUARES PROBLEM
---
Create a 6 × 6 ndarray named S containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of S and store it in S mean. Then use Boolean filtering to select only the elements strictly greater than S mean. Store these values in above mean.

The following function and methods were used in this problem:
- `np.arange(a, b, c)` - used to get the integers from a up to b (excluding b) and in c increments

  Example:
  ```python
  a = np.arange(3,10,3)
  a

  #result: array([3, 6, 9])
  ```

- `.reshape(a,b)` - rearranges array to a rows and b columns

  Example:
  ```python
  b = np.array([(1,2,3),(4,5,6)])
  b = b.reshape(6,1).shape
  b

  #result: (6, 1)
  ```
  
- `np.mean()` - built in function used to get the arithmetic mean of the chosen variable

  Example:
  ```python
  c = int(np.mean(a))
  c

  #result: 6
  #int was used to make the result as integer / whole number
  ```

- `A[equation]` - boolean condition where gets the A array and evaluates the equation enclosed in square brackets which will produce boolean values in the exact shape of A.

  Example:
  ```python
  c = np.array([(1,2,3),(4,5,6)])
  d = c[c > 3]
    #[(False, False, False), (True, True, True)]

  print(d)

  #result: [4 5 6]
  ```
  
- `np.save('file name', array)` - used to save an array to a binary file in .npy format

These methods were used to create a single function that gets the square of the first 36 positive integers in a 6 × 6 ndarray and filters the elements that are greater than the mean.
```python
import numpy as np

S = ((np.arange(1,37))**2).reshape(6, 6)
S_mean = np.mean(S)
above_mean = S[S > S_mean]

np.save('above_mean.npy', above_mean)

print("S: \n", S)
print("\nS_mean: ", S_mean)
print("\nabove_mean: \n", above_mean)
print("\nSelected Number of Elements: ", above_mean.size)
```
---
To view the program for PA2: download [ECE2112_PA2](https://github.com/kathleenhazelhulipas-cloud/ECE2112_Hulipas_PA2/blob/main/PA%202.ipynb), open on Jupyter Notebook, and run all cells.

## **README file Version History:**
- September 06, 2026 - Uploaded Readme File, PA2.ipynb, and 3 .npy files (X_normalized, div_by_4, above_mean)

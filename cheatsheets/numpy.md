# NumPy Cheatsheet

## Array Creation

```python
import numpy as np

np.array([1, 2, 3])              # From list
np.zeros((3, 4))                  # 3x4 zeros
np.ones((2, 3))                   # 2x3 ones
np.full((2, 2), 7)                # 2x2 filled with 7
np.eye(3)                         # 3x3 identity
np.arange(0, 10, 2)               # [0, 2, 4, 6, 8]
np.linspace(0, 1, 5)              # 5 evenly spaced [0, 0.25, 0.5, 0.75, 1]
np.random.randn(3, 4)             # 3x4 standard normal
np.random.rand(3, 4)              # 3x4 uniform [0,1)
```

## Indexing and Slicing

```python
a = np.array([[1,2,3],[4,5,6],[7,8,9]])

a[0, 1]          # 2 (row 0, col 1)
a[:, 1]           # [2, 5, 8] (all rows, col 1)
a[1, :]           # [4, 5, 6] (row 1, all cols)
a[:2, 1:]         # [[2,3],[5,6]]
a[a > 5]          # [6, 7, 8, 9] (boolean indexing)
a[[0, 2], :]      # rows 0 and 2 (fancy indexing)
```

## Reshaping

```python
a.reshape(3, 3)       # Reshape to 3x3
a.flatten()           # 1D copy
a.ravel()             # 1D view
a.T                   # Transpose
a[:, np.newaxis]      # Add dimension
np.expand_dims(a, 0)  # Add axis
np.squeeze(a)         # Remove size-1 dimensions
```

## Math Operations

```python
a + b                 # Element-wise add
a * b                 # Element-wise multiply (NOT matrix multiply)
a @ b                 # Matrix multiply
np.dot(a, b)          # Dot product / matrix multiply
np.sum(a, axis=0)     # Sum along axis 0 (columns)
np.mean(a, axis=1)    # Mean along axis 1 (rows)
np.max(a)             # Maximum value
np.argmax(a, axis=1)  # Index of max along axis
np.clip(a, 0, 1)      # Clip values to [0, 1]
np.exp(a)             # Element-wise exponential
np.log(a)             # Element-wise log
```

## Broadcasting Rules

```
Shape A     Shape B     Result
(3, 4)      (4,)        (3, 4)     ✓
(3, 4)      (3, 1)      (3, 4)     ✓
(3, 4)      (1, 4)      (3, 4)     ✓
(3, 4)      (3,)        ERROR      ✗
```

## Linear Algebra

```python
np.linalg.inv(A)           # Inverse
np.linalg.det(A)           # Determinant
np.linalg.eig(A)           # Eigenvalues + eigenvectors
np.linalg.svd(A)           # SVD decomposition
np.linalg.norm(a)          # L2 norm
np.linalg.solve(A, b)      # Solve Ax = b
np.linalg.pinv(A)          # Pseudo-inverse
```

## Random

```python
np.random.seed(42)                 # Set seed
np.random.randn(n)                 # Standard normal
np.random.uniform(0, 1, size=n)    # Uniform
np.random.choice(arr, size=k)      # Random sample
np.random.shuffle(arr)             # In-place shuffle
np.random.permutation(n)           # Random permutation
```

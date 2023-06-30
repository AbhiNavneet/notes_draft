

# The Numpy Library

> NumPy is one of the most important packages/libraries for numerical computing in python. The name **NumPy** basically is short for **Numerical Python**.

### Why Numpy uses Arrays instead of Python Lists ?

> Lists are ordered, mutable and heterogeneous. This makes them extremely flexible and they provide high usability but this flexibility of lists comes at a price. They are not efficient in numerical computations thus **Lists are slow**.

> Whereas, **Numpy** uses **nd-array** enables programmer to perform fast computations within the array using a technique called **vectorized operations** thus making **nd-array - super fast**.

## Importing Numpy Library

> To use the numpy library, we first have to **import** it into our current workspace using the import statement as shown below.

```python
import numpy as np
```

> **Note**: The name used to refer to the library can be changed using the “as” keyword followed by the preferred name as shown above (numpy as np).

## 1. Creating Numpy Arrays:

### 1.1 Creating An Array Using a - Python List

> Arrays can be created using python lists along with the arange as shown below:

```python
l1 = [1, 2, 3]  # l1 is python list

a = np.array(l1) # Using Numpy we convert List to Numpy array
a
```

### 1.2 Creating Arrays Using - arange function

> The **arange** function is similar to python’s **range** function:

```python
a = np.arange(5)
a
```

```py
a1 = np.arange(5, 20, 3)
a1
```

### 1.3 Creating Arrays Containing Only - Ones

> The **ones** functions can be used to create arrays containing only ones. This is done as shown below:

```py
a = np.ones(5) # num of values
a
```

> Numpy arrays with different matrix shape can be created using the ones function, by defining the shape required within square brackets, as the function’s argument.

```py
al = np.ones([2, 4])
a1
```

### 1.4 Creating Arrays Containing Only - Zeroes

> The **zeros** functions are very much similar to the ones function just described above, except that it creates arrays containing only zeros:

```py
a4 = np.zeros([3, 4])
a4
```

### 1.5 Creating Arrays Using - Random Number :

> Arrays can be created using numpy’s random number generation. This is made possible through the **random module** within the numpy library. 

> 1. **rand** Function : Arrays containing random **float** values between zero and one can be created using the rand function as shown below:

   ```py
   a = np.random.rand (3)
   a
   ```

   ```py
   a = np.random.rand (2, 2)
   a
   ```

> 2. **radint** Function: 

> Arrays containing random **integers** can be created using the randint function as shown below:

```py
a = np.random.randint (1, 10, 5) # (min, max, no. of values)
a
```



## 2. Indexing And Slicing

> Indexing numpy arrays is quite similar to the indexing protocol used for python lists.

```py
a = np.array([1, 2, 3, 11, 22])

a[0], a[3], a[-1]
```

```py
a[2:1]

a[2:-1]

a[:-2]
```

> To understand indexing of arrays that have more than one dimension, consider the two dimensional array shown below.

```py
a = np.random.randint(1, 100, [3, 4])
a
```

> The above array can be seen as an array containing three arrays containing integers. Using the same indexing rules as before we can access each of these individually as shown below:

```
a[0]
a[-1]
```

> Following the same indexing logic, elements within the arrays that compose the multidi- mensional array can then be accessed as shown below:

```py
a[O][0] 
a[e][-1] 
a[-1][0] 
a[-1][-1]
```

> Slicing of multidimensional arrays is done using a similar reasoning. Consider the two dimensional array shown below.

```py
a = np.random.randint(1, 100, [7, 8])
a
```

```py
a[1:4, 2:7]
```



## 3. Array Methods

### 3.1 RESHAPE & RESIZE

> The **reshape** and **resize** methods perform the task of reshaping a given array into another shape. 

> - The **reshape** method creates a copy of the original array and performs the reshaping operation on it. Hence the original array remains as it is.

  - ```py
    a = np.random.randint(1, 100, 6)
    a
    
    a1 = a.reshape(2, 3)
    a1
    ```

> - The **resize** method changes the shape of the original array into the new preferred shape. 

  - ```py
    a = np.random.randint(1, 100, 6)
    a
    
    a.resize (2, 3)
    a.shape
    ```

### 3.2 SORT

> The sort function sorts the array in ascending order:

```py
a = np.random.randint(1, 100, 5)
a

a.sort()
a
```

### 3.3 MAX & MIN

> The max method returns the maximum value along any given axis.

```py
a = np.random.randint(1, 100, [3, 5])
a

a.max(), a.max(axis = 0), a.max(axis = 1)
```

> The min methods return the minimum value along any given axis.

```py
a = np.random.randint(1, 100, [3, 5])
a

a.min(), a.min(axis = 0), a.min(axis = 1)
```

### 3.4 MEAN, VAR & STD:

> The mean,, var and std methods return the mean, median, variance and standard devi- ation of the array elements along any given axis.

```py
a = np.random.randint(1, 100, [2, 3])
a
```

```py
a.mean(), a.mean(axis = 0), a.mean (axis = 1)

a.var(), a.var(axis = 0), a.var(axis = 1)

a.std(), a.std(axis = 0), a.std(axis = 1)
```



## 3.5 UFUNCS (Inbuilt Numpy Functions):

> Numpy comes with an exhaustive set of **unary** ufuncs, shown in the table below are some of the more relevant ones:

```py
np.abs # Compute absolute value of each element in array

np.sqrt # Compute square root of each element in array

np.square # Compute square of each element in array

пр.exp # Compute exponent e**x of each element in array

np.log # Compute log to the base e of each element in array

np.log2 # Compute log to the base 2 of each element in array

np.loa10 # Compute log to the base 10 of each element in array

np.ceil # Rounds off to upper threshold of a number

np.floor # Rounds off to lower threshold of a number

np.sin, np.sinh # Sin and hyperbolic sin of each element in the array

np.cos, np.cosh # Cos and hyperbolic cos of each element in the array

np.tan, np.tanh # Tan and hyperbolic tan of each element in the array
```

> **Binary** ufuncs are basically ibuilt vectorized numpy functions that can be applied between two arrays of the same size and object type.

```py
np.add # Perform addition between corresponding elements of two arrays

np.subract # Perform suntraction between corresponding elements of two arrays

np.multiply # Perform multiplication between corresponding elements of two arrays

np.divide # Perform division between corresponding elements of two arrays

np.floor divide # Perform floor division between corresponding elements of two " // " arrays

np.power # Raise elements in first array to powers indicated in " ** " corresponding cells of the second array

np.mod # Perform modulus operation between corresponding elements" % " of two arravs
```

> The code shown below demonstrates some of the binary ufuncs described in the table above:

```py
al = np.random.randint(-100, 100, [2, 3])
a2 = np.random.randint(-10, 50, [2, 3])
a1
a2
```

```py
al + a2
a1 / a2
a1 % a2
```

## 4. Linear Algebra using Numpy

> Linear Algebraic operations like dot products, matrix multiplication/transformations, de- compositions and other matrix operations can be performed using numpy’s **linalg** module.

```py
np.transpose # returns the transpose of a 2D array
np.diag # returns the diagonal elements of a 2D array
np.trace # returns the sum of the diagonal elements
np.linalg.norm # returns the norms of an array along specfied axis
np.linalg.det # returns the determinant of a square array/matrix
np.linalg.eig # returns the eigen values of a square array/matrix
np.linalg.inv # returns the inverse of a square array/matrix
np.linalg.svd # returns the sigular value decompositions of an array/matrix
```

> Shown below is a demonstration of some of the functions described above:

```py
a = np.random.rand(3, 3)
np.diag(a)
np.trace(a)
```

> The **transpose** function can also be applied using the dot T operation as shown below. This operation converts all rows of a 2D array into columns as shown below.

```py
np.transpose(a)
a.T
```

> The **norm** function returns the norm of an array along any axis specified. Norms are a way to quantify the magnitude of a one dimensional array (ie: vector). There are more than one measures for the norm of a vector. Two norm types are relevant for our purposes, they are the **L1 and L2 norms.**

> - The **L1 norm** is the sum of the absolute values of each element of the vector, whereas the **L2 norm** is the square root of the sum of the squares of each element in the vector. 

  - ```py
    np.linalg.norm(a, 2) # L1 Norm
    
    np.linalg.norm(a, 2, axis = 0)
    
    np.linalg.norm(a, 2, axis = 1)
    ```

  - ```py
    np.linalg.norm(a, 1) # L1 Norm
    
    np.linalg.norm(a, 1, axis = 0)
    
    np.linalg.norm(a, 1, axis = 1)
    ```

### 4.1 The Dot Product

> The dot product is the most fundamental linear algebraic operation between two equal sized vectors (ie: one dimensional array). The dot product can be deconstructed into two sequential operations:

> 1. Multiplication operation between the two one dimensional arrays.
> 2. Summation of the values of the vector resulting from step 1.

> The two steps described above are implemented in the code shown below:

```py
a1 = np.random.rand(3)
a2 = np.random.rand(3)
a1, a2
```

```
a_dot = (al * a2).sum()
a_dot
```

> Dot products can be directly computed using the dot function described in the table shown earlier.

```py
np.dot(a1, a2)
```

### 4.2 Matrix Multiplication

> Matrix multiplication is a linear algebraic operation between two 2D arrays (ie: Matrices), which results in another matrix. Each value at any index(i, j) of this resultant matrix is the outcome of the dot product of the ith row of the first matrix and the jth column of the second matrix. 

> **Note**: Matrix multiplication is only possible if the number of columns of the first matrix is the same as the number of rows of the second matrix.

> The code shown below demonstrates matrix multiplication between two compatible matrices.

```py
m1 = np.random.randint(1, 100, [2, 3])
m2 = np.random.randint(50, 75, [3, 5])

m1
m2
```

> The code shown below demonstrates matrix multiplication between two compatible matrices.

```python
m_prod = m1 @ m2
m_prod
```

### 5. Concatenation Of Arrays

> Array can be concatenated using the numpy functions described below:

```py
m1 = np.random.randint(1, 100, [2, 3])
v1 = np.random.randint (10, 50, [1, 3])
v2 = np.random.randint (10, 50, [3, 1])

m1
v1
v2
```

> - **ROW WISE CONCATENATION**: To perform row concatenation we can use the concatenate function with axis specified as zero or use the vstack (vertical stack) function as shown below.

  - ```python
    m2 = np.concatenate((m1, V1), axis = 0)
    m2
    
    np.vstack((m1, V1))
    ```

> - **COLUMN WISE CONCATENATION**: To perform column concatenation we can use the concatenate function with axis specified as one or use the hstack (horizontal stack) function as shown below.

  - ```
    np.concatenate((m2, v2), axis = 1)
    
    np.hstack((m2, V2))
    ```

  

### 6. Saving and Loading NUMPY Data:

> Numpy has two functions save and load for efficiently saving and loading array data to disk. Arrays are saved in a file with .npy extension. The code shown below demonstrates the save and load functions.

```py
a = np.random. randint(1, 100, [3, 5])
a
```

```py
name = 'array a.npy'
np. save(name, a)
```

```py
a = np. load ('array_a.py')
a
```


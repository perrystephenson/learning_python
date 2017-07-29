# Numpy (Numeric Python)

This is a package which provides some types and functions for maths. The key use of numpy is the numpy.array() function, which provides something similar to the `c()` function (atomic vector) in R. Unlike lists (in both R and Python), the numpy.array function allows vectorised operations, which is apparently a bit novel for Python users but is the expected behaviour for R users.

### Numpy arrays

To create a numpy array:

```
import numpy
temp = numpy.array([1,2,3,4])
```

Note the strange bracket nesting - it looks like the array function takes a list as an argument, which means you need to use the square brackets to make a list, then pass this list as the argument to the array function. Not exactly elegant, but I'm sure I can deal with it.

One dimensional numpy arrays are useful for R users, because they behave like atomic vectors in R (in fact numpy arrays are also atomic - they can only hold items with the same data type). 

### Two dimensional numpy arrays

You can define n-dimensional numpy arrays using lists of lists. The highest level of the hierarchy is the first dimension of the n-dimensional array, the second level is the second dimension of the array, and so on. When working with a two dimensional array, this means that you can create a 2 row, 5 column numpy array using the following command:

```
import numpy as np
np_2d = np.array([[1, 2, 3, 4, 5 ],
                  [6, 7, 8, 9, 10]])
```

To interrogate the properties of the array you can use methods. For example, you can get the dimensions of the array using `np_2d.shape` - this would be written as `dim(np_2d)` in R.

You can subset 2D (or nD) arrays using chained square brackets (e.g. `np_2d[1][3]`), but the preferred method is to use a comma like in R (e.g. `np_2d[1,3]`). The main benefit of the comma approach is that it allows for slicing, e.g. `np_2d[:,2:3]`, which should be fairly familiar to R users except for the `inclusive:exclusive` syntax and 0-based indexing.

### Numpy functions

The numpy package also includes some maths functions, including `numpy.mean`, `numpy.median`, `numpy.round`, `numpy.corrcoef` (a correlation coefficient matrix) and `numpy.std` (for standard deviation). There are some data generation functions too, including `numpy.random.normal`, `numpy.column_stack`, etc.


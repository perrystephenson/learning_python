# Numpy (Numeric Python)

This is a package which provides useful new types for maths. The key use of numpy is the numpy.array() function, which provides something similar to the `c()` function (atomic vector) in R. Unlike lists (in both R and Python), the numpy.array function allows vectorised operations, which is apparently a bit novel for Python users but is the expected behaviour for R users.

To create a numpy array:

```
import numpy
temp = numpy.array([1,2,3,4])
```

Note the strange bracket nesting - it looks like the array function takes a list as an argument, which means you need to use the square brackets to make a list, then pass this list as the argument to the array function. Not exactly elegant, but I'm sure I can deal with it.


- NumPy is the fundamental package for scientific computing in Python. 
```python
import numpy as np
```
- It is a Python library that provides a multidimensional array object, various derived objects (such as masked arrays and matrices), and an *assortment* of routines for fast operations on arrays, including mathematical, logical, shape manipulation, sorting, selecting, I/O, discrete Fourier transforms, basic linear algebra, basic statistical operations, random simulation and much more.
- **Differences between NumPy arrays and the standard Python sequences:**
	- NumPy arrays have a fixed size at creation, unlike Python lists (which can grow dynamically). Changing the size of an `ndarray` will create a new array and delete the original.
	- The elements in a NumPy array are all required to be of the same data type, and thus will be the same size in memory. The exception: one can have arrays of (Python, including NumPy) objects, thereby allowing for arrays of different sized elements.
	- NumPy arrays facilitate advanced mathematical and other types of operations on large numbers of data. Typically, such operations are executed more efficiently and with less code than is possible using Python's built-in sequences.
[[np.random.normal]]
[[np.linspace]]

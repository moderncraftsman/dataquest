## INTRODUCTION TO NUMPY

#### READING FROM CSV FILE
- Convert a list of list into a ndarray
```python
import csv
import numpy as np
f = open("nyc_taxis.csv", "r")
taxi_list = list(csv.reader(f))  # data read as list of list    
taxi = np.array(converted_taxi_list)  
```


#### DIMENSIONS AND SELECTIONS FROM NDARRAY

- Retrieve dimensions
``` python
taxi.shape  # (rows, columns). If 1D, tuple (rows,) returned
```

- Select row from ndarray:
```python
second_row = taxi[1]
```

- Select multiple rows from ndarray:
```python
all_but_first_row = taxi[1:]
```
- Select specific item from ndarray:
```python
fifth_row_second_column = taxi[4, 1]
```

#### SLICING VALUES FROM NDARRAY
- Select single column:
```python
second_column = taxi[:, 1]
```

- Select multiple columns
```python
second_third_columns = taxi[:, 1:3]
cols =[1,3,5]
second_fourth_sixth_columns = taxi[:, cols]
```

- Select 2D slice:
```python
twod_slice = taxi[1:4, :3]
```

#### VECTOR MATH
- vector_a operation vector_b, where operation can be + - * / % ** //
- operations executed in parallel but dimensions, either original or through broadcasting, must match

CALCULATING STATISTICS FOR 1D NDARRAYS
- ndarray.min()
- ndarray.max()
- ndarray.mean()
- ndarray.median()
- ndarray.sum()

#### CALCULATING STATISTICS FOR 2D NDARRAYS

- Max value for entire 2D array
```python
taxi.max()
```

- Max value for each row in 2D Ndarray (returns a 1D Ndarray):
```python
taxi.max(axis=1)  # axis = 1 is across columns i.e. horizontal
```

- Max value for each column in 2D Ndarray (returns a 1D Ndarray):
```python
taxi.max(axis=0)  # axis = 0 is across rows i.e. vertical
```

#### ADDING ROWS AND COLUMNS TO NDARRAYS

- Join a sequence of arrays:
```python
np.concatenate([a1,a2], axis=0)
```

- Increase shape of an array by **one** in direction of axis:
```python
>>> x = np.array([1,2])
>>> x.shape
(2,)
>>> y = np.expand_dims(x, axis=0)
>>> y
array([[1, 2]])
>>> y.shape
(1, 2)
>>> y = np.expand_dims(x, axis=1)  # Equivalent to x[:,np.newaxis]
>>> y
array([[1],
       [2]])
>>> y.shape
(2, 1)
```

#### SORTING

- Sort a 1D Ndarray:
```python
np.argsort(taxi[0])
```

- Sort a 2D Ndarray by specific column:
```python
sorted_order = np.argsort(taxi[:, 15])  # Sort by column 16
taxi_sorted = taxi[sorted_order]
```

#### CONCEPTS
- One way NumPy makes our code run quickly is vectorization, which takes advantage of Single Instruction Multiple Data (SIMD) to process data more quickly.
- A list in NumPy is called a 1D Ndarray and a list of lists is called a 2D Ndarray. NumPy ndarrays use indices (all numbers unlike pandas which can use named labels) along both rows and columns and is the primary way we select and slice values

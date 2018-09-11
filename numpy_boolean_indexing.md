# Numpy Boolean Indexing

#### Numpy Generate From Text
- Reads in a file and chose a type that accommodate most values in that file since numpy arrays can only support a single type.
- If type chosen in numeric, fields with strings e.g. headers will become nan.
```python
import numpy as np
taxi = np.genfromtxt('nyc_taxi.csv', delimiter=',', skip_header=1)
taxi.dtype  # to print the datatype stored
```

#### Boolean arrays
- Boolean filtering for 1D Ndarray:
```python
a = np.array([2, 4, 6, 8])
filter = a < 5  # a<5 returns np.array([True, True, False, False])
a[filter]  # returns only true indices np.array([2, 4])
```

- Boolean filtering for 2D Ndarray:
```python
tip_amount = taxi[:, 12]
tip_bool = tip_amount > 50
top_tips = taxi[tip_bool, 5:14]  # pandas equivalent with column names taxi[taxi.tip_amt>50, 5:14]
```
Note: Numpy only use number indices so we cannot use df.colname

#### Assigning values
- Assigning values in a 2D Ndarray using indices:
```python
taxi[28214,5] = 1
taxi[:,0] = 16
taxi[1800:1802,7] = taxi[:,7].mean()
```
- Assigning values using Boolean arrays:
```python
taxi[taxi[:, 5] == 2, 15] = 1
```

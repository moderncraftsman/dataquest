*Importing Library*
```python
import matplotlib.pyplot as plt
%matplotlib inline # to plot within cells in jupyter notebook
```
*Basic Chart*
```python
import matplotlib.pyplot as plt

plt.plot(x, y) # figure and axes object automatically created
plt.get_xticks(rotation=90) # rotate x-axis marks to vertical
plt.xlabel("Dates")
plt.ylabel("Values")
plt.title("Plot of Values Over Time")
plt.show() # Render internal states. Subsequent changes will be shown in new plot
```

*Multiple Charts in Single Plot*
```python
import matplotlib.pyplot as pyplot

fig = plt.figure(figsize(15, 7)) # Create fig container size 15x7 inches
plt.plot(dates, gdp, color='green', label="GDP") # plot in axes 1
plt.plot(dates, unemployment, color='red', label='Unemployment') # plot in axes 1
plt.get_xticks(rotation=90) # rotate x axis ticks vertical
plt.xlabel("Month")
plt.ylabel("GDP/Unemployment")
plt.title("Plot of GDP and Unemployment Against Time")
plt.show_legend(loc='upper left')
plt.show()
```

# Matplotlib

Matplotlib is a python graphics library, and you normally import it using the following line of code:

```
import matplotlib.pyplot as plt
```

You can then plot things fairly quickly using the `plt.plot()` and `plt.show()` functions, like this:

```
year = [ 1950,  1970,  1990,  2010]
pop  = [2.519, 3.692, 5.263, 6.972]
plt.plot(year, pop)
plt.show()
```

You can modify the type of plot using different methods, e.g. `plt.scatter()`, `plt.hist()`, etc. The `plt.show()` method is used to show the plot on the screen, and `plt.clf()` is used to clean up after displaying the plot.

Unlike ggplot2 plots, it does not appear that you can build multiple plots simultaneously - you have to work on one at a time.

The plot can be modified with a whole bunch of methods, like in the following example:

```
import matplotlib.pyplot as plt
year = [ 1950,  1970,  1990,  2010]
pop  = [2.519, 3.692, 5.263, 6.972]
plt.plot(year, pop)
plt.xlabel('Year')
plt.ylabel('Population')
plt.title('World Population Projections')
plt.yticks([ 0,   2,    4,    6,    8. ], # Tick values
           ['0', '2B', '4B', '6B', '8B']) # Tick labels
plt.show()
```

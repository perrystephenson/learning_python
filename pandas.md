# pandas

The pandas package was written by Wes McKinney (who seems to be _Hadley Wickham lite_ for Python) and builds on top of the numpy package to provide DataFrames, another thing which is provided in base R but requires a package import in Python.

To create a DataFrame manually:

```
import pandas as pd
dict = {
"country":    ['Brazil',   'Russia', 'India',     'China',   'South Africa'],
"capital":    ['Brasilia', 'Moscow', 'New Delhi', 'Beijing', 'Pretoria'    ],
"area":       [ 8.516,      17.10,    3.286,       9.597,     1.221        ],
"population": [ 200.4,      143.5,    1252,        1357,      52.98        ]}
brics = pd.DataFrame(dict)
brics.index = ['BR',       'RU',     'IN',        'CH',      'SA'          ]
```

Alternatively, if you have data in a CSV file you can import it using:

```
brics = pd.read_csv('<path>')                # If there are no column names
brics = pd.read_csv('<path>', index_col = 0) # If there are column names
```

### Subsetting

To select a column in pandas, use `brics['country']`. This returns a "pandas Series" object, which is like a 1D element of a data frame. If you want to get a data frame back instead of a series, use `brics[['country']]`. This is the opposite of R, where the `[[]]` is used to drill down further than `[]`. The reason for this is that `[]` defines a list in Python, so you're really calling `brics[<subset>]` where `<subset>` is a list of length 1. In R, the `[[]]` subset operator is actually a function, hence the differing behaviours. This means that subsetting for multiple columns in Python doesn't take too much writing: `brics[['country', 'capital']]`.

Interestingly, and perhaps confusingly, if you provide a slice (range) to `brics[]` then you will be subsetting on rows, not columns! Using `brics[1:4]` selects the 2nd through 4th rows of the data frame.

If you want to do anything more complex than this, it starts getting a bit weird, and you have to use the `loc()` method (which stands for "location"). To pull out a named row, you need to use the `brics.loc['RU']` syntax (which returns a Series object), or `brics.loc[['RU']]` (which returns a DataFrame). You can also select multiple rows this way: `brics.loc[['RU', 'IN', 'CH']]`. You can then extend this to subset on columns as well, which starts to look a bit more like R (and like the 2D numpy array): `brics.loc[['RU', 'IN', 'CH'], ['country', 'capital']]`.

If you want to use an index, then you can do the same thing with lists of integers passed to the `iloc()` method (which stands for index-location. It seems like you probably need to chain these functions together if you want to have a mix of subsetting approaches. This is another area where R smashes Python - subsetting is so versatile in R!

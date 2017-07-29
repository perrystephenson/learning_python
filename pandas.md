# pandas

The pandas package was written by Wes McKinney (who seems to be Hadley Wickham lite for Python) and builds on top of the numpy package to provide DataFrames, another thing which is provided in base R but requires a package import in Python.

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


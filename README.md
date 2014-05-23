# pandaslite
Like `pandas` but in pure python.


```python
In [1]: import pandaslite as pd

In [2]: df = pd.read_csv("./pandaslite/data/diamonds.csv")

In [3]: df.head()
Out[3]:
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
|    cut    | color | price |  z   | carat | depth |  x   |  y   | table | clarity |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
|   Ideal   |   E   |  326  | 2.43 |  0.23 |  61.5 | 3.95 | 3.98 |   55  |   SI2   |
|  Premium  |   E   |  326  | 2.31 |  0.21 |  59.8 | 3.89 | 3.84 |   61  |   SI1   |
|    Good   |   E   |  327  | 2.31 |  0.23 |  56.9 | 4.05 | 4.07 |   65  |   VS1   |
|  Premium  |   I   |  334  | 2.63 |  0.29 |  62.4 | 4.2  | 4.23 |   58  |   VS2   |
|    Good   |   J   |  335  | 2.75 |  0.31 |  63.3 | 4.34 | 4.35 |   58  |   SI2   |
| Very Good |   J   |  336  | 2.48 |  0.24 |  62.8 | 3.94 | 3.96 |   57  |   VVS2  |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+

In [4]: df.describe()
Out[4]:
+---------------+---------------+----------------+---------------+-------+
|     table     |     depth     |     carat      |     price     | names |
+---------------+---------------+----------------+---------------+-------+
|  57.457183908 | 61.7494048943 | 0.797939747868 | 3932.79972191 |  mean |
| 2.23446984998 |  1.432608039  | 0.47400685051  | 3989.40275763 | stdev |
|    53940.0    |    53940.0    |    53940.0     |    53940.0    | count |
|      43.0     |      43.0     |      0.2       |     326.0     |  min  |
|      95.0     |      79.0     |      5.01      |    18823.0    |  max  |
+---------------+---------------+----------------+---------------+-------+

In [5]: df['color']
Out[5]:
+-------+
| value |
+-------+
|   E   |
|   E   |
|   E   |
|   I   |
|   J   |
|   J   |
+-------+

In [6]: df.color
Out[6]:
+-------+
| value |
+-------+
|   E   |
|   E   |
|   E   |
|   I   |
|   J   |
|   J   |
+-------+

In [7]: df[['color', 'price']]
Out[7]:
+-------+-------+
| color | price |
+-------+-------+
|   E   | 326.0 |
|   E   | 326.0 |
|   E   | 327.0 |
|   I   | 334.0 |
|   J   | 335.0 |
|   J   | 336.0 |
+-------+-------+

In [8]: df[1:50,:]
Out[8]:
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
|    cut    | color | price |  z   | carat | depth |  x   |  y   | table | clarity |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
|  Premium  |   E   | 326.0 | 2.31 |  0.21 |  59.8 | 3.89 | 3.84 |  61.0 |   SI1   |
|    Good   |   E   | 327.0 | 2.31 |  0.23 |  56.9 | 4.05 | 4.07 |  65.0 |   VS1   |
|  Premium  |   I   | 334.0 | 2.63 |  0.29 |  62.4 | 4.2  | 4.23 |  58.0 |   VS2   |
|    Good   |   J   | 335.0 | 2.75 |  0.31 |  63.3 | 4.34 | 4.35 |  58.0 |   SI2   |
| Very Good |   J   | 336.0 | 2.48 |  0.24 |  62.8 | 3.94 | 3.96 |  57.0 |   VVS2  |
| Very Good |   I   | 336.0 | 2.47 |  0.24 |  62.3 | 3.95 | 3.98 |  57.0 |   VVS1  |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+

In [9]: df[50:100]
Out[9]:
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
|    cut    | color | price |  z   | carat | depth |  x   |  y   | table | clarity |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+
| Very Good |   F   | 404.0 | 2.45 |  0.24 |  60.9 | 4.02 | 4.03 |  61.0 |   SI1   |
|   Ideal   |   G   | 404.0 | 2.44 |  0.23 |  61.9 | 3.93 | 3.95 |  54.0 |   VS1   |
|   Ideal   |   I   | 404.0 | 2.72 |  0.32 |  60.9 | 4.45 | 4.48 |  55.0 |   SI1   |
|  Premium  |   E   | 404.0 | 2.41 |  0.22 |  61.6 | 3.93 | 3.89 |  58.0 |   VS2   |
|  Premium  |   D   | 404.0 | 2.31 |  0.22 |  59.3 | 3.91 | 3.88 |  62.0 |   VS2   |
|   Ideal   |   I   | 405.0 | 2.63 |  0.3  |  61.0 | 4.3  | 4.33 |  59.0 |   SI2   |
+-----------+-------+-------+------+-------+-------+------+------+-------+---------+

In [10]: df[df.color=="E"]
Out[10]:
+---------+-------+-------+------+-------+-------+------+------+-------+---------+
|   cut   | color | price |  z   | carat | depth |  x   |  y   | table | clarity |
+---------+-------+-------+------+-------+-------+------+------+-------+---------+
| Premium |   E   | 326.0 | 2.31 |  0.21 |  59.8 | 3.89 | 3.84 |  61.0 |   SI1   |
| Premium |   E   | 326.0 | 2.31 |  0.21 |  59.8 | 3.89 | 3.84 |  61.0 |   SI1   |
| Premium |   E   | 326.0 | 2.31 |  0.21 |  59.8 | 3.89 | 3.84 |  61.0 |   SI1   |
|  Ideal  |   E   | 326.0 | 2.43 |  0.23 |  61.5 | 3.95 | 3.98 |  55.0 |   SI2   |
|  Ideal  |   E   | 326.0 | 2.43 |  0.23 |  61.5 | 3.95 | 3.98 |  55.0 |   SI2   |
|  Ideal  |   E   | 326.0 | 2.43 |  0.23 |  61.5 | 3.95 | 3.98 |  55.0 |   SI2   |
+---------+-------+-------+------+-------+-------+------+------+-------+---------+

In [11]: df.carat.apply(lambda x: x**2)
Out[11]:
+--------+
| value  |
+--------+
| 0.0529 |
| 0.0441 |
| 0.0529 |
| 0.0841 |
| 0.0961 |
| 0.0576 |
+--------+
```

## Why?

## But really, why?

## How it works?

### Install

### Basics

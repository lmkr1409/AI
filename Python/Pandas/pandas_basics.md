<!-- TOC -->

- [Introduction](#introduction)
    - [Pandas Objects](#pandas-objects)
        - [Objects](#objects)
            - [What are the Objects in Pandas?](#what-are-the-objects-in-pandas)
        - [DataFrame](#dataframe)
            - [What is DataFrame in pandas?](#what-is-dataframe-in-pandas)
            - [What are the different ways to create DataFrame?](#what-are-the-different-ways-to-create-dataframe)
            - [How to create pandas DataFrame using constructor?](#how-to-create-pandas-dataframe-using-constructor)
            - [How to create pandas DataFrame by reading from files ?](#how-to-create-pandas-dataframe-by-reading-from-files-)
            - [How to create pandas DataFrame using json object ?](#how-to-create-pandas-dataframe-using-json-object-)
            - [How to create pandas DataFrame using string ?](#how-to-create-pandas-dataframe-using-string-)
        - [Series](#series)
            - [What is a Series in pandas?](#what-is-a-series-in-pandas)
            - [How to create a Series in pandas ?](#how-to-create-a-series-in-pandas-)

<!-- /TOC -->

# Introduction

## Pandas Objects

### Objects
#### What are the Objects in Pandas?
    
Pandas has 2 Objects: `DataFrame`, `Series`

### DataFrame

#### What is DataFrame in pandas?

Pandas DataFrame is a 2-dimensional labeled data structure like any table with rows and columns. The size and values of the DataFrame are `mutable`,i.e., can be modified. It is the most commonly used pandas object.

#### What are the different ways to create DataFrame?

DataFrames can be created using different ways<br>
1. DataFrame() constructor
2. By reading files
    - pd.read_csv()
    - pd.read_excel()
    - pd.read_html()
    - pd.read_json()
    - pd.read_pickle()
3. By Normalizing Json
    - pd.json_normalize()
4. From string
    - pd.read_csv(io.StringIO())


#### How to create pandas DataFrame using constructor?

`DataFrame()` constructor is used to create a DataFrame in Pandas. The syntax of creating DataFrame is:

```python
pd.DataFrame(data, index, columns)
```

**data**: It is a dataset from which DataFrame is to be created. It can be list, dictionary, scalar value, series, ndarrays, etc.

**index**: It is optional, by default the index of the DataFrame starts from 0 and ends at the last data value(n-1). It defines the row label explicitly.

**columns**: This parameter is used to provide column names in the DataFrame. If the column name is not defined by default, it will take a value from 0 to n-1.

* **Method 1**: Create empty DataFrame.
  ```python
  df = pd.DataFrame()
  ```
  ```text
  Empty DataFrame
  Columns: []
  Index: []
  ```
* **Method 2**: Creating  DataFrame from `Lists`
  ```python
  import pandas as pd
  data = [10,20,30,40,50,60]
  df = pd.DataFrame(data, columns=['Numbers'])
  df
  ```
  <div>
  <table border="1" class="dataframe">
    <thead>
      <tr style="text-align: right;">
        <th></th>
        <th>Numbers</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>0</th>
        <td>10</td>
      </tr>
      <tr>
        <th>1</th>
        <td>20</td>
      </tr>
      <tr>
        <th>2</th>
        <td>30</td>
      </tr>
      <tr>
        <th>3</th>
        <td>40</td>
      </tr>
      <tr>
        <th>4</th>
        <td>50</td>
      </tr>
      <tr>
        <th>5</th>
        <td>60</td>
      </tr>
    </tbody>
  </table>
  </div>

**Method 3**: Creating Pandas DataFrame from `lists of lists`
```python
import pandas as pd
data = [['tom', 10], ['nick', 15], ['juli', 14]]
df = pd.DataFrame(data, columns=['Name', 'Age'])
df
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>tom</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>nick</td>
      <td>15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>juli</td>
      <td>14</td>
    </tr>
  </tbody>
</table>
</div>

**Method 4**: Creating DataFrame from `dict of lists`
```python
import pandas as pd
df = pd.DataFrame({'Name': ['Tom', 'nick', 'krishna', 'jack'], 'Age': [20, 21, 19, 18]})
df
```
<div>
<table border="1">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Tom</td>
      <td>20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>nick</td>
      <td>21</td>
    </tr>
    <tr>
      <th>2</th>
      <td>krishna</td>
      <td>19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>jack</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>

**Note**: While creating DataFrame using dictionary, the keys of dictionary will be column name by default. We can also provide column name explicitly using column parameter.

**Method 5**: Creating DataFrame from `list of dicts`
```python
import pandas as pd
data = [{'a': 1, 'b': 2, 'c': 3},
        {'a': 10, 'b': 20, 'c': 30}]
df = pd.DataFrame(data)
df
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10</td>
      <td>20</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
</div>

**Method 6:** Creating DataFrame from series
```python
import pandas as pd
sr = pd.Series([10, 20, 30, 40])
df = pd.DataFrame(sr)
df
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>

**Method 7:** Creating DataFrame from Dictionary of series.
```python
import pandas as pd
d = {'one': pd.Series([10, 20, 30, 40],
                      index=['a', 'b', 'c', 'd']),
     'two': pd.Series([10, 20, 30, 40],
                      index=['a', 'b', 'c', 'd'])}
  
df = pd.DataFrame(d)
df
```

<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>20</td>
      <td>20</td>
    </tr>
    <tr>
      <th>c</th>
      <td>30</td>
      <td>30</td>
    </tr>
    <tr>
      <th>d</th>
      <td>40</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>


<br>
<br>

#### How to create pandas DataFrame by reading from files ?

| file format | read_method   |
|--- | -- |
| csv     | pd.read_csv()     |
| excel   | pd.read_excel()   |
| json    | pd.read_json()    |
| pickle  | pd.read_pickle()  |
| html    | pd.read_html()    |

1. from `csv` files using `read_csv` method.
```python
pd.read_csv("sample_file.csv")
```

read_csv method has lot of optional parameter to read_read from csv files.<br>
Few of the optional parameter are:<br>
**index_col**: Treats the provided column as index for DataFrame.<br>
**usecols**: Uses only these columns for creating the DataFrame.<br>
**low_memory**: (default is `True`). Pandas internally process file in chunks to conserve memory while parsing. This will lead the type of columns to mixed types. To ensure no mixed types either set `low_memory` to `False` or we can specify the `dypes` parameter.

2. from `excel` files using `read_excel` method.
```python
pd.read_excel()
```

3. from `json` files using `read_json` method
```python
pd.read_json()
```

4. from `pickle` files using `read_pickle` method
```python
pd.read_pickle()
```
5. from `html` files using `read_html` method
```python
pd.read_html()
```

#### How to create pandas DataFrame using json object ?
```python
data = {'a': 1, 'b': 2, 'c': 3}
pd.DataFrame(data)
```
Raises<br>
ValueError: If using all scalar values, you must pass an index

Because we can create DataFrame if the json values are list using the constructor.
```python
data = {'a': 1, 'b': 2, 'c': 3}
pd.json_normalize(data)
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>

If the json is too complex then we may need to use `json_normalize from pandas.io.json` [like in this example](https://stackoverflow.com/questions/39899005/how-to-flatten-a-pandas-dataframe-with-some-columns-as-json/39906235)


Some hack to create dataframe from simple json object is by using Series
```python
data = {'a': 1, 'b': 2, 'c': 3}
pd.Series(data).to_frame().T
```

#### How to create pandas DataFrame using string ?

If we have data in a string object then we can create DataFrame by converting that string object as buffer using `StringIO` from `io`
```python
from io import StringIO
import pandas as pd1
data = """
Column A, Column B, Column C
Value1, 123, 23-09-2023
Value2, 147, 22-09-2023
Value3, 364, 21-09-2023
"""
pd.read_csv(StringIO(data))
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Column A</th>
      <th>Column B</th>
      <th>Column C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Value1</td>
      <td>123</td>
      <td>23-09-2023</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Value2</td>
      <td>147</td>
      <td>22-09-2023</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Value3</td>
      <td>364</td>
      <td>21-09-2023</td>
    </tr>
  </tbody>
</table>
</div>


### Series

#### What is a Series in pandas?

Pandas Series is a one-dimensional labeled array capable of holding data of any type (integer, string, float, python objects, etc.).

#### How to create a Series in pandas ?

We can create a pandas Series using `pd.Series()` constructor or by accessing a column from a DataFrame.

* using `list`

```python
import pandas as pd
pd.Series([1, 2, 3, 4, 5])
```
0&nbsp;&nbsp;&nbsp;&nbsp;1<br>
1&nbsp;&nbsp;&nbsp;&nbsp;2<br>
2&nbsp;&nbsp;&nbsp;&nbsp;3<br>
3&nbsp;&nbsp;&nbsp;&nbsp;4<br>
4&nbsp;&nbsp;&nbsp;&nbsp;5<br>
dtype: int64

* We can pass index and name for a series
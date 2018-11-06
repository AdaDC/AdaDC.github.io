---
title: 'Data Cleansing Using Python'
date: 2018-11-06 00:00:00
featured_image: '/images/sabrina_cleaning_data.jpg'
---
This example shows how to clean a dataset.  It removes duplicates and splits data that is all stored in one column into seperate columns.  Finally it writes the cleansed data to a .csv file.

<img src="https://media.giphy.com/media/3gPN8q3snGN759GAeY/giphy.gif" alt="Sabrina blowing out candles" title="Title text" />

For this example, dummy data based on [The Chilling Adventures of Sabrina](https://en.wikipedia.org/wiki/Chilling_Adventures_of_Sabrina_(TV_series)
will be used.  


```python
# Start by importing necessary libraries
import numpy as np
import pandas as pd

# Import data into dataframe
df = pd.DataFrame( [["first_name, last_name, tel, email"],
                   ["sabrina, spellman, 555, sspel@gmail.com"],
                   ["harvey, kinkle, 777, hkinkle@gmail.com"],
                   ["hilda, spellman, 888, hspell@gmail.com"],
                    ["zelda, spellman, 999, zspell@gmail.com"],
                    ["ambrose, spellman, 100, aspell@gmail.com"],
                    ["sabrina, spellman, 555, sspel@gmail.com"],
                    ["sabrina, spellman, 555, sspel@gmail.com"],
                    ["hilda, spellman, 888, hspell@gmail.com"]])

# The rows with information for Sabrina Spellman and Hilda Spellman have been repeated
```

All the data is stored in one column, with each value seperated by a comma.  Use the `head` command to preview the first five rows of data, and the `len` command to see the number of rows.


```python
print(df.head())
print("Number of rows: ", str(len(df)))
```

                                             0
    0        first_name, last_name, tel, email
    1  sabrina, spellman, 555, sspel@gmail.com
    2   harvey, kinkle, 777, hkinkle@gmail.com
    3   hilda, spellman, 888, hspell@gmail.com
    4   zelda, spellman, 999, zspell@gmail.com
    Number of rows:  9


## Remove duplicates
First we will use `drop_duplicates` to get rid of all the duplicated rows.


```python
dfDrop = df.drop_duplicates()
```

Let's look at the dataframe and number of rows to verify that there are no duplicates.


```python
print(dfDrop)
print("Number of rows: ", str(len(dfDrop)))
```

                                              0
    0         first_name, last_name, tel, email
    1   sabrina, spellman, 555, sspel@gmail.com
    2    harvey, kinkle, 777, hkinkle@gmail.com
    3    hilda, spellman, 888, hspell@gmail.com
    4    zelda, spellman, 999, zspell@gmail.com
    5  ambrose, spellman, 100, aspell@gmail.com
    Number of rows:  6


The three duplicated rows for Sabrina and Hilda Spellman have been removed from the dataset.

## Split the data into multiple cells


```python
dfSplit = dfDrop[0].str.split(', ', expand = True)
print(dfSplit)
```

                0          1    2                  3
    0  first_name  last_name  tel              email
    1     sabrina   spellman  555    sspel@gmail.com
    2      harvey     kinkle  777  hkinkle@gmail.com
    3       hilda   spellman  888   hspell@gmail.com
    4       zelda   spellman  999   zspell@gmail.com
    5     ambrose   spellman  100   aspell@gmail.com


## Capitalize the first letter of first and last names


```python
# Capitalize first_name
dfSplit[0][1:] = dfSplit[0][1:].str.capitalize()

# Capitalize last_name
dfSplit[1][1:] = dfSplit[1][1:].str.capitalize()
```

## Verify that the changes have been made, and save the cleansed data as a .csv file.


```python
dfSplit.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>first_name</td>
      <td>last_name</td>
      <td>tel</td>
      <td>email</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sabrina</td>
      <td>Spellman</td>
      <td>555</td>
      <td>sspel@gmail.com</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Harvey</td>
      <td>Kinkle</td>
      <td>777</td>
      <td>hkinkle@gmail.com</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hilda</td>
      <td>Spellman</td>
      <td>888</td>
      <td>hspell@gmail.com</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Zelda</td>
      <td>Spellman</td>
      <td>999</td>
      <td>zspell@gmail.com</td>
    </tr>
  </tbody>
</table>
</div>




```python
## Output the cleansed file to directory.csv
dfSplit.to_csv("directory.csv", header = False)
```

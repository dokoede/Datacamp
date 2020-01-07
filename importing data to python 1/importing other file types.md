## Importing other file types

- There are a number of datatypes that cannot be saved easily to flat files, such as lists and dictionaries.

- However, if you merely want to be able to import them into Python, you can serialize them. All this means is converting the object into a sequence of bytes, or a bytestream.

- Python pickle module is used for serializing and de-serializing a Python object structure. ... Pickling is a way to convert a python object (list, dict, etc.) into a character stream. The idea is that this character stream contains all the information necessary to reconstruct the object in another python script.

Example

```
# Import pickle package
import pickle

# Open pickle file and load data: d
with open('data.pkl', 'rb') as file:
    d = pickle.load(file)

# Print d
print(d)

# Print datatype of d
print(type(d))
```

## Working with excel

### listing sheet in excel

```
# Import pandas
import pandas as pd

# Assign spreadsheet filename: file
file = 'battledeath.xlsx'

# Load spreadsheet: xls
xls = pd.ExcelFile(file)

# Print sheet names
print(xls.sheet_names)
```

output
`2012, 2014`

### Importing sheets from Excel files

```
# Load a sheet into a DataFrame by name: df1. here we parsed using sheet name
df1 = xls.parse('2004')

# Print the head of the DataFrame df1
print(df1.head())

# Load a sheet into a DataFrame by index: df2. here we parsed using index
df2 = xls.parse(0)

# Print the head of the DataFrame df2
print(df2.head())

```

Examples

- Parse the first sheet by index. In doing so, skip the first row of data and name the columns 'Country' and 'AAM due to War (2002)' using the argument names. The values passed to skiprows and names all need to be of type list.

- Parse the second sheet by index. In doing so, parse only the first column with the usecols parameter, skip the first row and rename the column 'Country'. The argument passed to usecols also needs to be of type list.

```
# Parse the first sheet and rename the columns: df1
df1 = xls.parse(1, skiprows= [0], names=['Country', 'AAM due to war (2002)'])

# Print the head of the DataFrame df1
print(df1.head())

# Parse the first column of the second sheet and rename the column: df2
df2 = xls.parse(1, usecols=[1], skiprows=[0], names=['Country'])

# Print the head of the DataFrame df2
print(df2.head())
```

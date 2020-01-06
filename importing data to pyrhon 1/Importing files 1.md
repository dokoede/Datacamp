## importing text files

```
# Open a file: file
file = open('moby_dick.txt', mode = 'r')

# Print it
print(file.read())

# Check whether file is closed
print(file.closed)

# Close file
file.close()

# Check whether file is closed
print(file.closed)
```

- context manager
  `with open('file_name.txt') as file`

- to print first few line
  `print(file.readline())`

## Importing flat file (csv, txt)

- rows-record
- A record in a flat file is composed of fields or attributes, each of which contains at most one item of information.

### Using Numpy

```
# Import package
import numpy as np

# Assign filename to variable: file
file = 'digits.csv'

# Load file as array: digits
digits = np.loadtxt(file, delimiter=',')

# Print datatype of digits
print(type(digits))

```

### Customizing your NumPy import

There are a number of arguments that np.loadtxt() takes that you'll find useful:

- delimiter changes the delimiter that loadtxt() is expecting.
  You can use ',' for comma-delimited.
  You can use '\t' for tab-delimited.
- skiprows allows you to specify how many rows (not indices) you wish to skip
- usecols takes a list of the indices of the columns you wish to keep.

```
# Import numpy
import numpy as np

# Assign the filename: file
file = 'digits_header.txt'

# Load the data: data
data = np.loadtxt(file, delimiter='\t', skiprows=1, usecols=[0,2])

# Print data
print(data)
```

#### Working with mixed dataatypes

- the function np.loadtxt() wont work use this instead

```
data = np.genfromtxt('titanic.csv', delimiter=',', names=True, dtype=None)
```

- Here, the first argument is the filename, the second specifies the delimiter , and the third argument names tells us there is a header.

-Accessing rows and columns of structured arrays is super-intuitive: to get the ith row, merely execute data[i] and to get the column with name 'Fare', execute data['Fare']

- just like ng.genfromtxt() we can also use np.recfromcsv(), except that its default dtype is none, delimeter is ',' and names=True

```
data = np.recfromcsv('filename.txt')
```

## Using Pandas to import files as dataframe

```
# Import pandas as pd
import pandas as pd

# Assign the filename: file
file = 'titanic.csv'

# Read the file into a DataFrame: df
df = pd.read_csv(file)

# View the head of the DataFrame (first 5 rows)
df.head()
```

### building a numpy array from pandas dataframe

- we do this using .values()

example:

```
# Assign the filename: file
file = 'digits.csv'

# Read the first 5 rows of the file into a DataFrame:
data =pd.read_csv('digits.csv', nrows=5, header = None)


# Build a numpy array from the DataFrame: data_array

data_array = data.values

# Print the datatype of data_array to the shell
print(type(data_array))
```

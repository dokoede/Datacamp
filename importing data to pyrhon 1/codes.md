context manager
`with open('file_name.txt') as file`

to print first few line
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
data = np.loadtxt(file, delimiter='\t', skiprows=1)

# Print data
print(data)
```

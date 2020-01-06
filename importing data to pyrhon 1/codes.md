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

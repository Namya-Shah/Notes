---
Link: 
tags:
  - ML
---
# Notes
# Pretty Print with `pprint`
## Overview
- When working with complex or nested dictionaries, visualizing them in a readable format can be challenging. The `pprint` module in Python helps by providing a "pretty-print" functionality that formats dictionaries in a **structured and aesthetic way.**
## How it works
- The `pprint` function sorts dictionary keys, manages indentation, and breaks lines intelligently to improve readability. This is especially useful for debugging or presenting data structures.
## Example
```python
import pprint

data = {'key2': {'subkey1': 10,
				'subkey2': [20,30,40]},
		'key1': {'subkey1': 1, 'subkey3': {'subsubkey1': 12},
		'subkey2': [2,3,4]},
}
pprint.pprint(data)

# Output
# {'key1': {'subkey1': 1, 'subkey2': [2,3,4],

# 'subkey3': {'subsubkey1': 12}},

# 'key2': {'subkey1': 10, 'subkey2': [20,30,40]}}
```
# Retrieving values with `itemgetter`
## Overview
- Often, you need to retrieve specific values from a dictionary efficiently, especially when sorting or selecting specific fields. The `itemgetter` function from the `operator` module can optimize these operations.
## How it works
- `itemgetter` creates a callable that fetches the item from its operand using the keys you specify. This can be particularly useful in sorting lists of dictionaries by a specific key or extracting multiple values at once.
## Examples

--- start-multi-column: ID_3cgo
```column-settings
Number of Columns: 2
Largest Column: first
```

```python
from operator import itemgetter

data = [{'name': 'Alice', 'age': 30},

{'name': 'Bob', 'age': 25},

{'name': 'Charlie', 'age': 35}]

  

# Retrieve multiple values

get_name_age = itemgetter('name','age')

for person in data:

print(get_name_age(person))

# Sort by Age

data_sorted = sorted(data, key=itemgetter('age'))

print(data_sorted)
```


--- column-break ---

- In this example, `itemgetter` is used to retrieve both the name and age from each dictionary.
- The second example utilizes the function to seamlessly sort a list of dictionaries by age.

--- end-multi-column

# Dictionary Comprehensions
## Overview
- Similar to list comprehensions, dictionary comprehensions offer a concise way to construct new dictionaries from iterables or existing dictionaries.
## How it works
- This technique allows you to create a new dictionary by iterating over an iterable or transforming an existing dictionary, using an expression inside `curly braces {}`.
## Examples

--- start-multi-column: ID_9624
```column-settings
Number of Columns: 2
Largest Column: standard
```

```python
# Creating a new dictionary from a list

keys = ['a', 'b', 'c']

values = [1, 2, 3]

  

new_dict = {key: value for key, value in zip(keys, values)}

print(new_dict)
```

--- column-break ---

The first example creates a dictionary by zipping together two lists.

--- end-multi-column
--- start-multi-column: ID_zub2
```column-settings
Number of Columns: 2
Largest Column: standard
```


```python
# Transforming an existing dictionary

original_dict = {'a': 1, 'b': 2, 'c': 3}

squared_dict = {key: value ** 2 for key, value in original_dict.items()}

print(squared_dict)
```



--- column-break ---



The second example transforms an existing dictionary by squaring each value.

--- end-multi-column






# References
---
1. 

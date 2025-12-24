### Example

```python
from math_module.Addition import add
```

- We use **init**.py to create a package as before Python version 3.3, we weren't able to access packages without **init**.py file.
- We can import packages now without **init**.py if you are on version 3.3 and above.
- Also, creating **init**.py is useful for writing codes.
- Add . when importing packages in **init**.py

```python
from .Addition import add
from .Subtraction import sub
```

- Write in this way due to relative pathing
- We can conditionally import packages
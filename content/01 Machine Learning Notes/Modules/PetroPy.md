- A petrophysics with python package allowing scientific python computing of conventional and unconventional formation evaluation. Reads las files using lasio. Includes a petrophysical workflow and a log viewer based on XML templates.
![[Pasted image 20231020005358.png]]
# Installation
```bash
pip install petropy
```

To read in an las file, pass the file reference:
```python
import petropy as ptr
file_path = r'path/to/well.las'
log = ptr.Log(file_path)
```
- 
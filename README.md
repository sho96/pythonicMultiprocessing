# pythonicMultiprocessing
No need for writing __name__ == "__main__" for multiprocessing
## How to use
### Basics
* Import mp.py file into your script by 
```python
import mp
```
* Defile a function you want to run with multiple CPU cores
Example: 
```python
def function(x, y):
    a = 0
    for i in range(x):
        a += i
    return a + y
```
* Run the function using mp.process
```python
results = mp.process(function, [(100, 200), (200, 300), (300, 400)])
print(results)
```

### Using other libraries with functions run on mp.process()
* Writing ```python
mp.importLibraries(__file__)
```
anywhere before mp.process()

This will import all libraries to the functions that will be run with mp.process()
Notice: However, importing unnecessary libraries can lead to increasing RAM usage
* specifying 'imports' argunment for for mp.process()
```python
mp.process(
    function,
    [("a","r","g","1"), ("a","r","g","2")], 
    imports = """
    import numpy as np
    import sys
    """
)```
This can prevent increasing RAM usage caused by mp.importLibraries(__file__)
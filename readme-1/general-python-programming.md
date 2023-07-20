# General Python Programming

## Function

```python
def func(a, *args, b=None, **kwargs):
    """
    :param a: position argument
    :param args: variable arguments (also a tuple, so it can be used like a tuple)
    :param b: default argument
    :param kwargs: variable for named args (also a dict)
    """
    
    # Example to use the tuple
    self.item_one = args[0]
    for arg in args:
        print(arg)
    
    # Similar case for the **kwargs
    for k, v in kwargs.items():
        print(k, v)
    return None
```

## Class

### \_\_hash\_\_ and \_\_equal\_\_

Set() / Dict() use the object \_\_hash\_\_ and \_\_equal\_\_ method to compare if two objects are the same. \
So if we override the \_\_hash\_\_ method, we need to override the \_\_equal\_\_ method as well

[https://stackoverflow.com/questions/38430277/python-class-hash-method-and-set](https://stackoverflow.com/questions/38430277/python-class-hash-method-and-set)

## Decorator in Python

[https://www.programiz.com/python-programming/decorator](https://www.programiz.com/python-programming/decorator)

###

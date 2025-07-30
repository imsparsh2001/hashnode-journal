---
title: "Working with Modules in Python and Reloading Changes"
datePublished: Wed Jul 30 2025 18:30:43 GMT+0000 (Coordinated Universal Time)
cuid: cmdqax5fl000302l3ch3jerqz
slug: working-with-modules-in-python-and-reloading-changes
tags: python, python3, python-beginner, python-projects, python-modules-and-packages

---

  
In Python, a **module** is simply a `.py` file containing reusable code such as functions, classes, or variables. You can import built-in modules or create your own custom ones within a project.

### Importing Built-in and Custom Modules

```python
import os
print(os.getcwd())  # Prints the current working directory
```

You can also create your own module. For example, a file named `mymodule.py`:

```python
# mymodule.py
def greet():
    print("Hello from mymodule!")
```

Then, you can import and use it in your main script or Python shell:

```python
import mymodule
mymodule.greet()  # Output: Hello from mymodule!
```

### Updating an Imported Module

If you modify `mymodule.py`:

```python
# mymodule.py
def greet():
    print("Hi! This is an updated greeting.")
```

Then rerun `mymodule.greet()` in the same shell or interactive session, Python will still use the previously cached version of the module, showing the old output.

### Reloading the Module

To reflect the updated code without restarting the session, use `importlib.reload()`:

```python
import importlib
importlib.reload(mymodule)
mymodule.greet()  # Output: Hi! This is an updated greeting.
```

### Conclusion

Python caches modules after the first import to optimize performance. During development or testing, when frequent changes are made to a module, use `importlib.reload()` to update the session with the latest version of the module without restarting the interpreter.
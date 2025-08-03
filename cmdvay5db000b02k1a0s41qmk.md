---
title: "Python Mutability Explained: What You Need to Know"
seoTitle: "Python Mutability Explained: What You Need to Know"
datePublished: Sun Aug 03 2025 06:30:21 GMT+0000 (Coordinated Universal Time)
cuid: cmdvay5db000b02k1a0s41qmk
slug: python-mutability-explained-what-you-need-to-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1754033742117/1163cc62-914f-450c-b658-61c50f084e37.png
tags: python, python3, devops, python-beginner, python-projects, devops-journey

---

Mutability is one of those fundamental concepts that every Python developer must grasp. In this article, let's explore what mutability means in Python, how **everything in Python is really an object in memory**, and how references, not values, govern whether things are mutable or immutable. We'll make it easy, just like you see in the flowchart!

## Everything is an Object in Python

The first rule in Python: **everything is an object**—from integers and strings to lists and functions. Every object in Python has three core properties:

* **Identity:** Its unique address in memory, accessed using the `id()` function.
    
* **Type:** The kind of object (e.g., `int`, `str`, `list`), determined by `type()`.
    
* **Value:** The actual data stored in that object.
    

Variables in Python don’t have types assigned to them—instead, **the object stored in memory has a type**. Variables are just *labels* that reference these objects in memory.

> ***Example:***
> 
> ```python
> a = 10
> print(type(a))      # <class 'int'>
> print(id(a))        # Returns a unique memory address
> ```

## Mutability: Driven by Object Reference, Not Value

Whether something is mutable or immutable depends on whether you can change its value *at the same memory address*—in other words, whether a change affects the object referred to by a particular identity.

* **Mutable objects:** Their value can change while keeping the same identity (memory location).
    
* **Immutable objects:** Once created, you cannot change their value at that address; any “change” creates a new object.
    

## Lists Are Mutable—Examples

Let's dig into lists, which are classic mutable types:

```python
lst1 = [1, 2, 3]
lst2 = lst1           # Both variables point to the same object
lst2.append(4)        # Modify through lst2
print(lst1)           # Output: [1, 2, 3, 4]
print(lst2)           # Output: [1, 2, 3, 4]
```

Here, `lst1` and `lst2` both refer to the same object (same identity). Changing `lst2` reflects in `lst1`, showing mutability.

## Copying Lists: New Reference

But when you **copy a list**, you create a new object (new identity):

```python
lst1 = [1, 2, 3]
lst2 = lst1[:]        # Creates a shallow copy
lst2.append(4)
print(lst1)           # Output: [1, 2, 3] (unchanged)
print(lst2)           # Output: [1, 2, 3, 4]
```

Now, `lst1` and `lst2` are different objects; changing one doesn't affect the other.

## Immutable Example: Strings

Strings are **immutable**:

```python
s1 = "hello"
s2 = s1
s2 = "world"
print(s1)  # Output: "hello"
print(s2)  # Output: "world"
```

Assigning a new value to `s2` creates a new object in memory; `s1` remains unchanged.

## Why Reference Matters: Garbage Collection

When no variable refers to a particular object in memory, that object becomes inaccessible. Python's **garbage collector** automatically cleans it up in the background, freeing memory for other processes.

```python
a = [1, 2, 3]
b = a
a = None  # b still refers to the list
b = None  # Now, no references left: gets cleaned up!
```

## What About Other Types?

* **Mutable:** Lists, dicts, sets, user-defined objects.
    
* **Immutable:** Integers, floats, strings, tuples, frozensets.
    

## Wrapping Up Using the Diagram

The attached diagram sums it up:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1753896370983/7604d2dd-0080-4269-a5a4-f4a067d80c07.png align="left")

* An **object** has identity, type, and value.
    
* If you can change the value at the same identity (memory reference), it's **mutable**.
    
* If you can't, it's **immutable**.
    

The real trick is in understanding that **variables are labels—references—to objects in memory, not containers holding values themselves**. Mutability is all about *what happens at that memory location*, not about the variable.

## Key Points:

* Everything in Python is stored in memory as an object.
    
* Variables hold references to these objects, not the actual values.
    
* Mutability is about **whether an object can be changed at the same memory location**.
    
* Lists are mutable; integers, strings, and tuples are immutable.
    
* Copying mutable objects like lists creates a new reference.
    
* Unused objects are automatically cleaned up by Python’s garbage collector.
    

Understanding how Python handles memory and references will help you write cleaner and more predictable code.

Happy coding!
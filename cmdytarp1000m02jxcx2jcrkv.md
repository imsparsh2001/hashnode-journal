---
title: "Python Conditionals Explained: A Quick Tutorial"
datePublished: Tue Aug 05 2025 17:27:21 GMT+0000 (Coordinated Universal Time)
cuid: cmdytarp1000m02jxcx2jcrkv
slug: python-conditionals-explained-a-quick-tutorial
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1754034512363/085cc0e8-070a-48d4-abe0-c34a98d6668d.png
tags: python, python3, devops, python-beginner, python-projects, devops-articles, devops-journey

---

Conditionals are one of the most important building blocks in programming. They allow your code to "decide" what to do based on certain conditions—just like how you might choose to wear a raincoat only if it’s raining.

In this article, I’ll explain conditionals in Python in a simple way, using examples you can try right away, including some from real scenarios like ordering snacks, choosing cup sizes, device monitoring, and even seat bookings!

## What Are Conditionals?

At their core, **conditionals** help your program perform different actions based on whether a condition is true or false.

The most common conditional statements in Python are:

* `if`
    
* `elif` (short for "else if")
    
* `else`
    
* `match` (Python 3.10+ feature)
    

## Basic `if-else` Statement

The simplest way to do conditionals is with an `if` statement, which checks a condition, and if it’s true, runs the block of code inside it.

Here’s a real example using snack orders:

```python
snack = input("Enter your preferred snack: ").lower()

if snack == "cookies" or snack == "samosa":
    print(f"Great Choice! We'll serve you {snack}")
else:
    print("Sorry, we only serve cookies or samosa with tea")
```

**How this works:**

* The program asks you to enter a snack.
    
* It converts the input to lowercase to handle cases like “Cookies” or “SAMOSA”.
    
* If the snack is `"cookies"` or `"samosa"`, it prints a welcoming message.
    
* Otherwise, it politely says it doesn’t serve that snack.
    

## Using `if`, `elif`, and `else` for Multiple Conditions

Sometimes you want to choose between more than two options. This is where `elif` comes in handy.

Let's say you're choosing a cup size and want to set prices accordingly:

```python
cup = input("Choose your cup size (small/medium/large): ").lower()

if cup == "small":
    print("Price is 10 rupees")
elif cup == "medium":
    print("Price is 15 rupees")
elif cup == "large":
    print("Price is 20 rupees")
else:
    print("Unknown cup size")
```

**What’s happening here:**

* The program checks each condition one by one.
    
* If the size matches `"small"`, it displays 10 rupees.
    
* If not, it checks for `"medium"`, then `"large"`.
    
* If none match, it goes to the `else` block to catch unexpected input.
    

## Nested Conditionals: Condition Inside Another Condition

Sometimes, you want to check one condition only if another condition is true. This is called **nesting** conditionals.

Here’s an example with a device status and temperature monitoring:

```python
device_status = "active"
temperature = 38

if device_status == "active":
    if temperature > 35:
        print("High temperature alert!")
    else:
        print("Temperature is normal")
else:
    print("Device is offline")
```

**How this works:**

* First, the program checks if the device is `"active"`.
    
* If true, it then checks the temperature.
    
    * If temperature is above 35, it warns about high temperature.
        
    * Otherwise, it says temperature is normal.
        
* If the device isn’t active, it prints that the device is offline.
    

## Ternary Conditional Operator: Short `if-else`

Python offers a handy one-line way to write an `if-else` statement for simple conditions.

Here’s an example to calculate delivery fees based on order amount:

```python
order_amount = int(input("Enter the order amount: "))

delivery_fees = 0 if order_amount > 300 else 30

print(f"Delivery fees is : {delivery_fees}")
```

**Explanation:**

* If the order amount is greater than 300, delivery fees are set to 0.
    
* Otherwise, delivery fees are 30.
    
* This short form is very readable and useful in many cases.
    

## Python’s `match` Statement: Clean Multi-way Choices (Python 3.10+)

Python 3.10 introduced a powerful new feature called `match`, which works somewhat like a `switch` in other languages but much more powerful.

Here’s an example for choosing seat types in a booking system:

```python
seat_type = input("Enter seat type (sleeper/AC/general/luxury): ").lower()

match seat_type:
    case "sleeper":
        print("Sleeper - No AC, beds available")
    case "ac":
        print("AC - Air conditioned, comfy ride")
    case "general":
        print("General - Cheapest option, no reservation")
    case "luxury":
        print("Luxury - Premium seats with meals")
    case _:
        print("Invalid seat type")
```

**How it works:**

* The program compares the input to each case.
    
* If it finds a match, it prints the matching description.
    
* The underscore `_` acts like a default case to handle anything unknown.
    

## Summary: Key Points About Conditionals

* `if` runs code only if a condition is true.
    
* `elif` checks additional conditions if previous `if` or `elif` were false.
    
* `else` runs if none of the above conditions were true.
    
* Conditions can be **nested** inside other conditions.
    
* Use **ternary operator** (`<true_value> if <condition> else <false_value>`) for concise conditions.
    
* Use `match` for cleaner multi-way branching (Python 3.10+).
    

## Why Use Conditionals?

Conditionals help your programs:

* Make decisions
    
* Handle different inputs gracefully
    
* React in real-time to changing conditions (like sensor readings or user choices)
    

They are essential to writing smart and useful software.

## Try It Yourself!

Practice these examples in your Python environment or online interpreters. Modify the input prompts and experiment with different conditions. It’s a great way to learn by doing!

If you want to dive deeper, many tutorials online explain conditionals with visuals and practice exercises. But starting with real-world examples like snacks, cup sizes, devices, and seat bookings makes it easier to relate.

Happy coding! 🎉🐍

If you found this helpful, do share your own examples or questions. I’m here to help!
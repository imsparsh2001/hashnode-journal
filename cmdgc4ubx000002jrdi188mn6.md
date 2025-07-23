---
title: "Shell Scripting for Beginners: Automate Your Linux Tasks 🚀"
seoTitle: "Shell scripting"
datePublished: Wed Jul 23 2025 19:07:00 GMT+0000 (Coordinated Universal Time)
cuid: cmdgc4ubx000002jrdi188mn6
slug: shell-scripting-for-beginners-automate-your-linux-tasks
tags: devops, shell, shell-scripting, scripting, shell-script

---

## What is Shell Scripting? 🤔

Shell scripting means writing a series of commands, saved in a file, which the computer will carry out one by one. Think of it as creating a **set of instructions** so your computer can do your boring or repetitive jobs for you, automatically.

**Why use it?**

* Automate tasks like file handling and software installs.
    
* Manage system settings.
    
* Speed up your daily computer chores without clicking around.
    

* ## How to Create and Run a Shell Script
    
    **Every shell script:**
    
    * Is just a text file.
        
    * Usually ends with `.sh`
        
    * Begins with the magic line: `#!/bin/bash`
        
    
    **Steps:**
    
    1. **Write your script** (in Notepad, VS Code, etc.).
        
    2. **Make it executable:**
        
        ```bash
        chmod 700 myscript.sh
        ```
        
    3. **Run it:**
        
        ```bash
        ./myscript.sh
        ```
        
    
    ## Basic Shell Script Example 🚦
    
    ```bash
    #!/bin/bash
    
    # This is a comment
    echo "Hello, welcome to my Shell Scripting Tutorial!"
    
    # Show current date and time
    date
    
    # Create a directory, move in, and create a file
    mkdir my_directory
    cd my_directory
    touch my_file.txt
    
    # Write text into the file and display it
    echo "This is some example text." > my_file.txt
    cat my_file.txt
    
    # Remove the file and directory, go back
    rm my_file.txt
    cd ..
    rmdir my_directory
    
    echo "Script execution complete.!"
    ```
    
    ## Getting User Input 📥
    
    To make your script interactive, ask the user for info:
    
* ```bash
    #!/bin/bash
    
    # reads input from the user and puts it in the username variable
    echo "Enter Username: "
    read username
    echo $username
    
    # displays the prompt message
    # -p stand for prompt
    # reads input from the user and puts it in the newusername variable
    read -p "Enter the new username: " newusername
    echo $newusername
    
    # reads input from the user & hides the text from echoing in the terminal
    # -s stands for silent
    read -sp "Enter Password: " password
    echo ""
    echo $password
    ```
    

* if you don’t wish to specify the variable name for the read we can use `$REPLY` to echo the value
    
    ```bash
    #!/bin/bash
    
    echo "Enter the username: "
    read
    echo "Read without variable name assignment: "$REPLY
    ```
    
* # **Argument Passing**
    
    We can pass arguments that can be used inside the scripts when it is executed. Those arguments can be accessed by the script using special variables like `$1` `$2` `$3` etc.
    
    * `$0` - returns the file name of the shell script.
        
    * `$@` - returns all arguments passed from cli.
        
    * `$#` - returns the no of arguments passed from cli.
        
    
    Let’s say we have a script file named [`arguement.sh`](http://passing.sh) and let's pass 2 arguments to it.
    
    ```bash
    argument.sh "Sparsh" "DevOps Engineer"
    ```
    
    ```bash
    #!/bin/bash
    
    # gives the filename of the script itself
    echo "FileName Argument: "$0 # argument.sh
    
    # gives the first argument passed
    echo "First Argument: "$1 # Sparsh
    
    # gives the second argument passed
    echo "Second Argument: "$2 # DevOps Engineer
    
    # displays all arguments passed
    echo "All Arguments: "$@ # Sparsh DevOps Engineer
    
    # displays number of arguments passed
    echo "No of Arguments: "$# # 2
    ```
    
    ## Variables & Data Types
    
    Variables are where you **store data to reuse later**.
    
    ## Assigning and Using Variables
    
    ```bash
    #!/bin/bash
    
    length=10
    width=5
    area=$((length * width))
    echo "The area of the rectangle is: $area"  # Shows 50
    ```
    
    ## Strings and Numbers
    
    ```bash
    #!/bin/bash
    
    # String variables
    name="Sparsh"
    greeting="Hello"
    
    # Concatenating strings
    message="$greeting, $name! How are you?"
    
    # Displaying the message
    echo $message
    ```
    
    ```bash
    #!/bin/bash
    
    # Integer variables
    num1=10
    num2=5
    
    # Performing arithmetic operations
    sum=$((num1 + num2))
    difference=$((num1 - num2))
    product=$((num1 * num2))
    quotient=$((num1 / num2))
    
    # Displaying the results
    echo "Sum: $sum"
    echo "Difference: $difference"
    echo "Product: $product"
    echo "Quotient: $quotient"
    ```
    
    The output will be:
    
    ```bash
    Sum: 15
    Difference: 5
    Product: 50
    Quotient: 2
    ```
    
    ## Using Environment Variables 🌎
    
    Environment variables are special variables predefined by your operating system or set by users. They hold important information about your system's environment.
    
    ```bash
    #!/bin/bash
    
    # Accessing environment variables
    echo "Home directory: $HOME"
    echo "Username: $USER"
    echo "Current working directory: $PWD"
    echo "Operating system: $OSTYPE"
    ```
    
    In the above example, we use the `echo` command to display the values of several common environment variables:
    
    * `$HOME`: This variable represents the home directory of the current user. It typically stores the path to the user's folder.
        
    * `$USER`: This variable holds the username of the current user.
        
    * `$PWD`: This variable stores the absolute path of the current working directory. It provides the location where the script is being executed.
        
    * `$OSTYPE`: This variable contains the identifier for the operating system type. It specifies the type of operating system being used, such as "linux-gnu" for Linux systems.
        
    
    When you run this script, it will output something similar to:
    
    ```bash
    Home directory: /home/username
    Username: username
    Current working directory: /path/to/current/directory
    Operating system: linux-gnu
    ```
    
    The actual values will depend on your system configuration.
    
* # **Conditional Statements**
    
    ```bash
    #!/bin/bash
    
    a=10
    b=20
    
    # less than using square brackets
    if [[ $a -lt $b ]]
    then
       echo "a is less than b"
    else
       echo "a is not less than b"
    fi
    ```
    
    In shell scripting, `[[ ]]` or `test` command can be used for evaluating conditional expressions. Below are certain unary operators that can be used for testing the conditions
    
    # **Conditions**
    
    * `[[ -z STRING ]]` - Empty string
        
    * `[[ -n STRING ]]` - Not empty string
        
    * `[[ STRING == STRING ]]` - Equal
        
    * `[[ STRING != STRING ]]` - Not equal
        
    * `[[ NUM -eq NUM ]]` - Equal
        
    * `[[ NUM -ne NUM ]]` - Not equal
        
    * `[[ NUM -lt NUM ]]` - Less than
        
    * `[[ NUM -le NUM ]]` - Less than or equal
        
    * `[[ NUM -gt NUM ]]` - Greater than
        
    * `[[ NUM -ge NUM ]]` - Greater than or equal
        
    * `[[ ! EXPR ]]` - Not
        
    * `[[ X && Y ]]` - And
        
    * `[[ X || Y ]]` - Or
        
    
    # **File Conditions**
    
    * `[[ -e FILE ]]` - Exists
        
    * `[[ -r FILE ]]` - Readable
        
    * `[[ -h FILE ]]` - Symbolic link
        
    * `[[ -d FILE ]]` - Directory
        
    * `[[ -w FILE ]]` - Writable file
        
    * `[[ -s FILE ]]` - File size is &gt; 0 bytes
        
    * `[[ -f FILE ]]` - File
        
    * `[[ -x FILE ]]` - Executable file
        
    
    ```bash
    #!/bin/bash
    
    # -e stands for exists
    if [[ -e ./ifelse.sh ]]
    then
      echo "File exists"
    else
      echo "File does not exist"
    fi
    ```
    
    ```bash
    #!/bin/bash
    
    read -p "Enter the number between 1 to 3: " number
    
    if [[ $number -eq 1 ]]
    then
            echo "The number entered is 1"
    elif [[ $number -eq 2 ]]
    then
            echo "The number entered is 2"
    elif [[ $number -eq 3 ]]
    then
            echo "The number entered is 3"
    else
            echo "Invalid Number"
    fi
    ```
    
    # **for**
    
    The `for` loop is used to iterate over a sequence of values and below is the syntax
    
    ```bash
    #!/bin/bash
    
    for i in {1..10}
    do
      echo "Val: $i"
    done
    ```
    
    # **while**
    
    The `while` loop is used to execute a set of commands repeatedly as long as a certain condition is true. The loop continues until the condition is false.
    
    ```bash
    #!/bin/bash
    
    count=0
    
    while [ $count -lt 5 ]
    do
      echo $count
      count=$(($count+1))
    done
    ```
    
    # **Arrays**
    
    An array is a variable that can hold multiple values under a single name
    
    * `${arrayVarName[@]}` - displays all the values of the array.
        
    * `${#arrayVarName[@]}` - displays the lenght of the array.
        
    * `${arrayVarName[0]}` - displays the first element of the array
        
    * `${arrayVarName[-1]}` - displays the last element of the array
        
    * `unset arrayVarName[2]` - deletes the 2 element
        
    
    ```bash
    #!/bin/bash
    
    # Declare an array of fruits
    fruits=("apple" "banana" "orange" "guava")
    
    # Print the entire array
    echo "All fruits using @ symbol: ${fruits[@]}"
    echo "All fruits using * symbol: ${fruits[*]}"
    
    # Print the third element of the array
    echo "Third fruit: ${fruits[2]}"
    
    # Print the length of the array
    echo "Number of fruits: ${#fruits[@]}"
    ```
    
    # **Break Statement**
    
    `break` is a keyword. It is a control statement that is used to exit out of a loop ( `for`, `while`, or `until`) when a certain condition is met. It means that the control of the program is transferred outside the loop and resumes with the next set of lines in the script
    
    ```bash
    #!/bin/bash
    
    count=1
    
    while true
    do
      echo "Count is $count"
      count=$(($count+1))
      if [ $count -gt 5 ]; then
        echo "Break statement reached"
        break
      fi
    done
    ```
    
    # **Continue statement**
    
    `continue` is a keyword that is used inside loops (such as `for`, `while`, and `until`) to skip the current iteration of the loop and move on to the next iteration. It means that when the continue keyword is encountered while executing a loop the next set of lines in that loop will not be executed and moves to the next iteration.
    
    ```bash
    #!/bin/bash
    
    for i in {1..10}
    do
      if [ $i -eq 5 ]
      then
        continue
      fi
      echo $i
    done
    ```
    
    # **Functions**
    
    Functions are a block of code which can be used again and again for doing a specific task thus providing code reusability.
    
    # **Normal Function**
    
    ```bash
    #!/bin/bash
    
    sum(){
            echo "The numbers are: $n1 $n2"
            sum_val=$(($n1+$n2))
            echo "Sum: $sum_val"
    }
    
    n1=$1
    n2=$2
    sum
    ```
    
    # **Function with return values**
    
    To access the return value of the function we need to use `$?` to access that value
    
    ```bash
    #!/bin/bash
    
    sum(){
            echo "The numbers are: $n1 $n2"
            sum_val=$(($n1+$n2))
            echo "Sum: $sum_val"
            return $sum_val
    }
    
    n1=$1
    n2=$2
    sum
    
    echo "Retuned value from function is $?"
    ```
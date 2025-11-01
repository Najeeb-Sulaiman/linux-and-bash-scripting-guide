## Functions and Reusability in Bash

As your Bash scripts grow larger, you will find yourself repeating yourself by writting the same block of code over and over again. This is an issue because repeating the same code blocks becomes inefficient and hard to maintain. This also doesn't conform to the DRY (Don't Repeat Yourself) principle in programming.

Functions solve this problem by letting you group commands into reusable, named units, just like Python functions.

### What Are Functions?

A function is a named block of code that performs a specific task.
You can call it multiple times in your script to avoid duplication and make your code cleaner.

**Syntax**
```bash
function function_name {
    # commands
}
```

Alternatively, it can be written like this:

```bash
function_name() {
    # commands
}
```
Both versions work the same way.

Let's define and call a simple function that greets:

```bash
#!/bin/bash

greet() {
    echo "Hello, Data Engineer!"
}

# Call the function
greet
```

I bet you already know what the output is.

**Note**: Functions must be defined before they are called in the script.

### Functions with Parameters

You can pass arguments to a function, just like in Python.

Let's pass a name parameter to our greeting function above:

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

greet "Najeeb"
```
Output:
```text
Hello, Najeeb!
```

**Notes**:
- `$1`, `$2`, `$3` represent the first, second, and third arguments passed to the function.
- `$@` represents all arguments.

For example, let's create a function that takes multiple parameters:

```bash
process_file() {
    echo "Processing file: $1"
    echo "Saving to: $2"
}

process_file "sales.csv" "/data/processed/sales.csv"
```
It's as simple as that.

### Return Values and Exit Codes

Functions can return a status code (0 = success, anything else = failure). This can be useful if we want to intentionally mark our code run as success or failure.

For example:
```bash
check_file() {
    if [ -f "$1" ]; then
        echo "File exists"
        return 0
    else
        echo "File not found"
        return 1
    fi
}

check_file "/data/raw/data.csv"
echo "Status code: $?"
```
Output:
```bash
File exists
Status code: 0
```
Remember, we use `$?` to capture the exit status of the last executed command.


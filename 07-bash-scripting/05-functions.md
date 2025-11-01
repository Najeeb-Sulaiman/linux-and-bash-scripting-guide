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

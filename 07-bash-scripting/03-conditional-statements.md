## Conditional Statements

Conditional statements make your Bash scripts **intelligent**. Just like in any other programming language, they can check for conditions and take different actions depending on whether something is true or false.

In data engineering, we use conditional statements in these example scenario:

- Check if a file or directory exists before processing it.
- Stop the script if an error occurs.
- Validate inputs or configuration before running a pipeline.

Let's deep-dive into how we write conditionals:

### The `if` Statement

Below is the structure of an `if` statement in Bash:

```bash
if [ condition ]
then
    # commands to execute if condition is true
fi
```

Foe example:

```bash
#!/bin/bash
if [ -f "/data/raw/sales.csv" ]
then
    echo "File exists. Proceeding with processing..."
fi
```

Here is what that means:

- `-f`: checks if the file exists and is a regular file.
- The condition must be wrapped in `[ ]` and separated by spaces.
- `then` starts the block of code to execute if true.
- `fi` ends the `if` statement.

### The `if-else` Statement

Sometimes you want to handle both outcome of the condition, the true and the false. This is where we use `if-else` Statement.

For example:

```bash
#!/bin/bash
if [ -d "/data/raw" ]
then
    echo "Raw data directory found!"
else
    echo "Raw data directory missing! Please create it first."
fi
```

Here, we are checking wether a directory exists and then taking action based on the outcome (true or fals).

### The `if-elif-else` (Multiple Conditions)

The `if-elif-else` statement is used to handle multiple conditions. For example:

```bash
#!/bin/bash
size=50

if [ $size -gt 100 ]; then
    echo "Large dataset"
elif [ $size -gt 10 ]; then
    echo "Medium dataset"
else
    echo "Small dataset"
fi
```

Explanation:

- `elif` = “else if”
- `-gt` means greater than

If `size` is greater than 100, then `echo "Large dataset"` will be excuted. Else if `size` is greater than 10, then `echo "Medium dataset"` will be executed. Else, if none of these is true, then execute echo `"Small dataset"`.

### Common Conditional Operators
Conditional operators are often used in conditional statements to check the condition of an expression. So it's important to be familiar with the common ones.

| Type                   | Operator | Meaning                  | Example               |
| ---------------------- | -------- | ------------------------ | --------------------- |
| **File test**          | `-f`     | File exists              | `[ -f file.csv ]`     |
|                        | `-d`     | Directory exists         | `[ -d /data/raw ]`    |
|                        | `-e`     | File or directory exists | `[ -e /tmp/log.txt ]` |
|                        | `-s`     | File is not empty        | `[ -s data.csv ]`     |
| **String comparison**  | `==`     | Strings are equal        | `[ "$var" == "yes" ]` |
|                        | `!=`     | Strings are not equal    | `[ "$var" != "no" ]`  |
|                        | `-z`     | String is empty          | `[ -z "$name" ]`      |
| **Numeric comparison** | `-eq`    | Equal                    | `[ $a -eq 10 ]`       |
|                        | `-ne`    | Not equal                | `[ $a -ne 5 ]`        |
|                        | `-gt`    | Greater than             | `[ $a -gt 5 ]`        |
|                        | `-lt`    | Less than                | `[ $a -lt 10 ]`       |
|                        | `-ge`    | Greater or equal         | `[ $a -ge 10 ]`       |
|                        | `-le`    | Less or equal            | `[ $a -le 10 ]`       |


### Combining Conditions (AND & OR)

As covered in the earlier modules, we can logically combine multiple commands. We can also combine multiple conditional tests using:
- && → AND
- || → OR

For example:

AND:
```bash
if [ -d "/data/raw" ] && [ -s "/data/raw/sales.csv" ]; then
    echo "Data folder and file are ready."
else
    echo "Missing folder or empty file."
fi

OR:
```bash
if [ "$ENV" == "dev" ] || [ "$ENV" == "staging" ]; then
    echo "Running in non-production environment."
fi
```

### The case Statement (For Multiple Matches)

For cleaner multi-condition handling, use `case`, just like in SQL or a `switch` statement in Python.

Here is an example of how it works:

```bash
#!/bin/bash
echo "Enter environment (dev, staging, prod):"
read env

case $env in
  dev)
    echo "You selected development environment."
    ;;
  staging)
    echo "You selected staging environment."
    ;;
  prod)
    echo "You selected production environment."
    ;;
  *)
    echo "Unknown environment: $env"
    ;;
esac
```

This is bery useful in data engineering workloads.
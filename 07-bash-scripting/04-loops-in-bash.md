## Loops in Bash

In data engineering, you often need to repeat actions, for example, running a command on every CSV file in a directory, or checking a folder for new data every few seconds.

Instead of copying and pasting commands, loops help you automate repetitive tasks efficiently.

Just like other programming languages, there are different types of loop.

### The `for` Loop

The `for` loop runs a command for each item in a list. We use it to iterate over a list. It similar to for loops in Python.

Basic Syntax:

```bash
for item in list
do
    # commands to execute for each item
done
```

For example, let's loop through numbers:
```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "Processing dataset #$i"
done
```

Now, let's loop through files:

This is one of the most common use cases in data engineering:

```bash
#!/bin/bash
for file in /data/raw/*.csv
do
    echo "Processing file: $file"
    head -n 2 "$file"
done
```

With this, we can automatically process every CSV file in a data ingestion(raw) folder.


Let's loop with a sequence. More like range in python:

```bash
for i in {1..5}
do
    echo "Run $i completed"
done
```

You can also use the seq command:
```bash
for i in $(seq 1 5)
do
    echo "Loop $i"
done
```

### The `while` Loop

The `while` loop runs as long as a condition is true. Similar to Python's while loop.

Eample:

```bash
#!/bin/bash
count=1

while [ $count -le 5 ]
do
    echo "Run #$count"
    ((count++))
done
```
This will run the `echo` command 5 times, from 1 to 5.

Let's look at this data engineering example:

```bash
#!/bin/bash
while [ ! -f "/data/raw/daily_sales.csv" ]
do
    echo "Waiting for daily_sales.csv to arrive..."
    sleep 5
done

echo "File detected! Starting ETL..."
```

This automates waiting for new data arrivals before running transformations. The code will continue to execute (in this case wait for a new file) until a new file is detected.

There is an `until` Loop but we will not cover the details here. Just think of it as the opposite of `while` loop. it runs **until** the condition becomes true.

### Loop Control Statements

A very important aspect of loops is the control statement. We use them to control the behavior of loops.

- `break` - We use it to exit the loop early
    ```bash
        for i in {1..10}
        do
            if [ $i -eq 5 ]; then
                echo "Stopping loop at $i"
                break
            fi
            echo "Count: $i"
        done
    ```
- continue – We use it to skip to the next iteration. For example if you want to skip the processing of certain files.
    ```bash
        for i in {1..5}
        do
            if [ $i -eq 3 ]; then
                echo "Skipping 3"
                continue
            fi
            echo "Count: $i"
        done
    ```


## Loops in Bash

In data engineering, you often need to repeat actions, for example, running a command on every CSV file in a directory, or checking a folder for new data every few seconds.

Instead of copying and pasting commands, loops help you automate repetitive tasks efficiently.

Just like other programming languages, there are different types of loop.

### The for Loop

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



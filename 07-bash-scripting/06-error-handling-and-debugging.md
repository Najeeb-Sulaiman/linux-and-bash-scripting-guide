## Error Handling and Debugging in Bash

Let me tell you a fact in Data Engineering, **things can and will go wrong**. But how you prepare for this and handle this when it happens is what makes you an exceptional engineer. When building your data pipelines or any automation many things can go wrong, there could be missing files, issues, failed API calls, or unexpected input.

In this module, you will learn how to:
- Detect and handle errors gracefully
- Debug scripts efficiently
- Write reliable Bash scripts for production use

Before we dive-deeper, let's explore some reasons why error handling matters.

Without proper error handling, a Bash script can:
- Continue running after a failure (causing data corruption)
- Overwrite important files
- Fail silently (and you won’t even know it happened)

All these can be very costly in production, so pay attention.

Take a look at this example:
```bash
#!/bin/bash
cp /data/raw/sales.csv /data/processed/
echo "File copied!"
```

Can you already guess what will happen?

Let me tell ypu if you don't know:

If `/data/raw/sales.csv` doesn’t exist, the `cp` command will fail but the script still prints “File copied!”.

Now you should know what the danger is.

Let's look at exit code and how we can use them for error handling.

### Exit Codes in Bash

Every command in Bash returns an exit status code:
- `0` - Success
- Non-zero - Failure

You can access the exit code of the **last executed command** with `$?`.

For example:
```bash
ls /data/raw
echo $?
```
If `/data/raw` exists - 0
If not - non-zero value (e.g., `2`).

We can use exit codes in conditions to check if a command succeeds before taking action.
```bash
if ls /data/raw > /dev/null 2>&1; then
  echo "Directory exists"
else
  echo "Directory missing"
fi
```

### Stopping Scripts on Error (`set -e`)

`set -e` tells Bash to immediately exit if any command fails.

```bash
#!/bin/bash
set -e

echo "Starting pipeline..."
cp /data/raw/input.csv /data/tmp/
awk -F, '$6 != "Failed"' /data/tmp/input.csv > /data/tmp/clean.csv
mv /data/tmp/clean.csv /data/processed/
echo "Pipeline completed successfully!"
```
In the above script, if any command fails, the script stops right there, preventing partial or corrupted processing.

**Be Careful**

I want to warn you again. If you expect a command to fail (e.g, checking for file existence), use error handling around it:
```bash
set -e

if [ ! -f "input.csv" ]; then
  echo "Error: input.csv not found"
  exit 1
fi
```

### Custom Error Messages with `exit`

You can manually stop a script and print an error message with exit.

```bash
if [ ! -d "/data/raw" ]; then
  echo "Data directory missing!"
  exit 1
fi
```

Let me show you some exit codes meaning by conventio:

| Code | Meaning                        |
| ---- | ------------------------------ |
| 0    | Success                        |
| 1    | General error                  |
| 2    | Misuse of shell builtins       |
| 126  | Command invoked cannot execute |
| 127  | Command not found              |
| 130  | Script terminated by Ctrl+C    |

You can check the documentation for more.

A powerful way to handle errors gracefully is with the `trap` command. I will not cover this here but you can look it up to learn more about it.

### Enabling Debug Mode (`set -x`)

When a script doesn’t behave as expected, `debug mode` helps you trace what’s happening. There are also some scenarios where you want to write your script with debug mode enabled.

Let's look at an example:
```bash
#!/bin/bash
set -x  # Enable debug mode

echo "Starting job..."
cp /data/raw/input.csv /data/tmp/
awk -F, '$6 != "Failed"' /data/tmp/input.csv > /data/tmp/clean.csv
set +x  # Disable debug mode
```
Output:
```bash
+ echo 'Starting job...'
Starting job...
+ cp /data/raw/input.csv /data/tmp/
+ awk -F, '$6 != "Failed"' /data/tmp/input.csv > /data/tmp/clean.csv
```
Debug mode can be useful in CI/CD logs when troubleshooting job failures. We use this in our CI/CD at work.

### Using `set -u` to Catch Undefined Variables
`set -u` (or `set -o nounset`) makes Bash throw an error if you use an undefined variable.
```bash
#!/bin/bash
set -u

echo "Username: $USER_NAME"
```
If `$USER_NAME` is not defined, Bash exits with:
```bash
./script.sh: line 3: USER_NAME: unbound variable
```
This can be useful to prevent small bugs.


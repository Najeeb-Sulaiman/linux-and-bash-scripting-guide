## Introduction to Bash Scripting

Bash scripting is one of the most powerful tools in a data engineer’s toolkit.
It lets you automate repetitive tasks, manage files, run data pipelines, and glue together tools like Python, Spark, or SQL from the command line. Learning Bash is like learning English, it's very important.

Now,
### What is a Bash Script?

A Bash script is simply a text file that contains a series of Linux commands that execute automatically when run.

Instead of typing each command manually, you can write them once in a script and execute them all at once.

Bash is has a lot of similar concept as other programming languages like Python, so we can somehow say Bash is a programming language.

### Why Use Bash Scripts as a Data Engineer?

Here are some everyday automation scenarios where Bash can be extremely useful:

| Task                  | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| **Data Ingestion**    | Automate the download and organization of raw datasets daily.         |
| **Data Cleaning**     | Run commands (like `awk`, `sed`, `grep`) on multiple files.           |
| **ETL Orchestration** | Chain multiple scripts together to extract, transform, and load data. |
| **Environment Setup** | Install dependencies and prepare your local or cloud environment.     |
| **Monitoring Jobs**   | Automate health checks and send alerts on failures.                   |


### Structure of a Bash Script

Every Bash script typically has these parts:

1. Shebang line (defines the interpreter)
2. Commands or logic (what you want to run)

Let's look at the following example:

```bash
#!/bin/bash
# This is a simple bash script
echo "Welcome to Bash scripting!"
echo "Today is $(date)"
```
What  does that mean?

- `#!/bin/bash`: tells the system to use the Bash interpreter.
- Lines starting with `#`: are comments.
- `echo`: prints text to the terminal.
- `$(date)`: runs the date command and substitutes its output.

### Creating and Running Your First Bash Script

Follow this simple steps to create and run your first bash script:

- Step 1: Create a new file
     ```bash
     nano welcome.sh
     ```

- step 2: Add the following content and save the file
    ```bash
    #!/bin/bash
    echo "Hello Data Engineers!"
    echo "This is your first Bash script running on $(hostname)"
    ```

- step 3: Make it executable

    Before running, give it permission:
    
    ```bash
    chmod +x welcome.sh
    ```

- step 4: Run your script

    ```bash
    ./welcome.sh
    ```

You should see output like:

```text
Hello Data Engineers!
This is your first Bash script running on <Your hostname>
```

### Common Mistakes to Avoid

Please take note of the below common mistakes while writting Bash scripts:

| Mistake                           | Why It Matters                                                         |
| --------------------------------- | ---------------------------------------------------------------------- |
| Forgetting `#!/bin/bash`          | Script may not run correctly or use a different shell.                 |
| Missing `chmod +x`                | Script won’t be executable.                                            |
| Using Windows line endings        | Always save files with **Unix (LF)** line endings, not Windows (CRLF). |
| Not using quotes around variables | Filenames with spaces can break your script.                           |


In the next module, we will explore how to make scripts dynamic using **variables** and **user input**.

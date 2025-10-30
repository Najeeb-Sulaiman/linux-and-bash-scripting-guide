## Variables and User Input

Variables are at the heart of any programming or scripting language, and Bash is no exception.
They allow you to store data (like filenames, dates, paths, and user inputs) that can be reused and modified throughout your script.

### What is a Variable?

A variable is a name for a value that you can store and reference later. It's simply a placeholder.

Let's look at how we define variables:

```bash
#!/bin/bash
name="Najeeb"
role="Data Engineer"

echo "Hello, $name! Your role is $role."
```

What's hapenning here?

The `name` and `role` are our variable, we are then referencing their value  using `$` in the sentence.

- Notice that there are no spaces aroun the `=` sign.
- name = "Najeeb" will cause an error.
- Use `$variable` to access the value.
- Always quote variable references (`"$name"`) to handle spaces safely.

### Command Substitution

Command substitution lets you store the output of a command inside a variable.

For example:

```bash
#!/bin/bash
current_date=$(date)
echo "The current date and time is: $current_date"
```

### Reading User Input

Your scripts can interact with users using the read command.

Example:

```bash
#!/bin/bash
echo "Enter your project name:"
read project
echo "Creating project folder: $project"
mkdir -p "/projects/$project"
```

This is wjat you get when you run it (assuming your input is `etl_pipeline`):
```yaml
Enter your project name:
etl_pipeline
Creating project folder: etl_pipeline
```

### Environment Variables

Bash comes with `built-in variables` provided by the system. For example:

| Variable    | Description       | Example Output   |
| ----------- | ----------------- | ---------------- |
| `$USER`     | Current username  | `najeeb`         |
| `$HOME`     | Home directory    | `/home/najeeb`   |
| `$PWD`      | Current directory | `/data/projects` |
| `$HOSTNAME` | System hostname   | `data-lab-vm`    |
| `$SHELL`    | Current shell     | `/bin/bash`      |

Environment variables are useful for building platform-independent scripts that work across systems.

For example:

```bash
echo "You are logged in as $USER on $HOSTNAME"
```
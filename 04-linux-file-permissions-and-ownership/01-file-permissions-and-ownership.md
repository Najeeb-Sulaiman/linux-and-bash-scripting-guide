## What Does File Permissions Mean?

Every file and directory in Linux has permissions that control:

- Who can access it

- What they can do with it (read, write, execute)


### Types of Users
There are three types of users in Linux. Each file and directory has three levels of permission:

- User (u): The creator/owner of the file.
- Group (g): Users belonging to the file's group.
- Others (o): All other users on the system.

### Types of Permissions:
There are three types of permissions in Linux:

| Symbol | Meaning | Applies To                                            |
| ------ | ------- | ----------------------------------------------------- |
| **r**  | read    | view the file contents / list a directory             |
| **w**  | write   | modify the file / create or delete inside a directory |
| **x**  | execute | run the file as a program / access a directory        |

You can view file permissions using:

```bash
ls -l
```

Example output:

```bash
-rwxr-xr--  1 najeeb devs  5120 Oct 23  etl.py
```

What does the ouptut above mean? Let's break it down below:

| Part           | Meaning                                        |
| -------------- | ---------------------------------------------- |
| **-**          | Type (`-` = file, `d` = directory, `l` = link) |
| **rwx**        | Owner permissions (`read`, `write`, `execute`) | 
| **r-x**        | Group permissions (`read`, `execute`)          |
| **r--**        | Others permissions (`read` only)               |
| **najeeb**     | Owner                                          |
| **devs**       | Group                                          |
| **5120**       | File size                                      |
| **etl.py** | File name                                      |

This means:

- The owner can read/write/execute

- The group can read/execute

- Others can only read

### How to Change Permissions:

We use the `chmod` command to change permissions in Linux. `chmod` means **change mode**

There are two ways we use it:

- symbolic mode
- Octal (numeruc) mode

Let's look at some example and understand how they work:

- Symbolic Mode Examples

    - Let's add a write permission for the `dev` group above:
    ```bash
    chmod g+w weather.py
    ```

    - Let's remove execute permission for others:
    ```bash
    chmod o-x weather.py
    ```

    - Let's give everyone execute permission:
    ```bash
    chmod a+x weather.py
    ```
    (a means all: user + group + others)

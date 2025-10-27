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

We use the `chmod` command to change permissions in Linux. `chmod` means **change mode**.

To specify what type of modification we want to made, we use symbols:

- Add (+), remove (-), or set (=) permissions.

There are two ways we can modufy permissions:

- symbolic mode
- Octal (numeruc) mode

Let's look at some example and understand how they work:

- **Symbolic Mode Examples**

    - Let's add a write permission for the `dev` group above:
    ```bash
    chmod g+w etl.py
    ```

    - Let's remove execute permission for others:
    ```bash
    chmod o-x etl.py
    ```

    - Let's give everyone execute permission:
    ```bash
    chmod a+x etl.py
    ```
    (a means all: user + group + others)


- **Octal Mode (Numeric)**:

    Each permission has a number value:

    | Permission | Value |
    | ---------- | ----- |
    | r          | 4     |
    | w          | 2     |
    | x          | 1     |

    You add them up to represent combinations:

    | Permissions | Value |
    | ----------- | ----- |
    | rwx         | 7     |
    | rw-         | 6     |
    | r-x         | 5     |
    | r--         | 4     |
    | ---         | 0     |

    Example:

    ```bash
    chmod 754 etl.py
    ```

    What does that mean?

    - 7 (rwx) → owner

    - 5 (r-x) → group

    - 4 (r--) → others

    This means:

    ```bash
    Owner: read, write, execute
    Group: read, execute
    Others: read
    ```

### How to Change Ownership:

Permissions are tied to ownership and you can chnge who owns a file using the command `chown`.

For example:

```bash
sudo chown najeeb etl.py
```

Change both owner and group:

```bash
sudo chown najeeb:devs etl.py
```

### Directory Permissions

Directory file types are indicated with `d`. Conceptually, permissions operate the same way, but directories interpret these operations differently.

| Permission | Meaning                           |
| ---------- | --------------------------------- |
| r          | list files in the directory       |
| w          | add/remove files in the directory |
| x          | enter the directory (cd into it)  |

For example, if a directory doesn’t have execute (x) permission, you can’t `cd` into it, even if you can see it.


Exercise:

- Make a script executable
- Give a group write access to a directory
- Restrict access to a file completely (Only the owner can read/write.)
- Make a file publicly readable (Owner can read/write, others can only read.)
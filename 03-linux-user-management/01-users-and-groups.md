## Users and Groups

Linux is a **multi-user system**, This means that multiple people or services can access it simultaneously. Each user must be granted with controlled privileges, otherwise the system will be messed up. We also need to be able to define who can access the system and what level of acces they should have.

Linux uses `users` and `groups` to assign this privileges. This makes Linux a secure system by design

### Key Concepts

- **User:** This refers to a person or process account (e.g. root, ubuntu, airflow).
    
- **Group:** A collection of users with shared access rights.
    
- **Root:** The superuser with unrestricted control.

### Common Commands for User and Group Management

| Command          | Description                                     |
| ---------------- | ----------------------------------------------- |
| `whoami`         | Displays the current user                       |
| `id`             | Shows user ID (UID), group ID (GID), and groups |
| `adduser <name>` | Creates a new user (requires root)              |
| `passwd <name>`  | Sets or changes a user password                 |
| `su <user>`      | Switches user                                   |
| `sudo <command>` | Executes a command with root privileges         |
| `groups`         | Lists groups you belong to                      |


For example:
```bash
sudo useradd analyst
sudo passwd analyst
sudo usermod -aG data-team analyst
```

Anatomy of a Command

Every shell command follows this structure:

```bash
command [options] [arguments]
```

Example:

```bash
ls -lh /home
```
- command: ls (list directory contents)

- option: -lh (long format + human-readable)

- argument: /home (which directory)

---

## Navigating the File System
These are the most used commands to navigate the file system in Linux.

| Command    | Description                                      | Example    |
| ---------- | ------------------------------------------------ | ---------- |
| `pwd`      | Print current working directory                  | `pwd`      |
| `ls`       | List files and directories                       | `ls`       |
| `ls -1`    | Display one item per line                        | `ls -1`    |
| `ls -l`    | Show detailed (long) listing of files            | `ls -l`    |
| `ls -a`    | Show hidden files (those starting with .)        | `ls -la`   |
| `cd`       | Change directory (use relative or absolute path) | `cd /etc`  |
| `cd ..`    | Move up one level                                | `cd ..`    |
| `cd ../..` | Move up two levels                               | `cd ../..` |
| `cd ~`     | Go to your home directory                        | `cd ~`     |
| `cd /`     | Go to the root directory                         | `cd /`     |


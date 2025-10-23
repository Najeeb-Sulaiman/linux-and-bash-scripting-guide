## Manipulate Files and Directory

These commands help you organize and clean up the Linux file system.

| Command | Description                                         | Example                |
| ------- | --------------------------------------------------- | ---------------------- |
| `cp`    | Copy a file                                         | `cp file1.txt backup/` |
| `cp -r` | Copy a directory and its contents recursively       | `cp -r dir1 dir2`      |
| `mv`    | Move or rename a file/directory                     | `mv old.txt new.txt`   |
| `mkdir` | Create a new directory                              | `mkdir logs`           |
| `rmdir` | Remove an empty directory                           | `rmdir test`           |
| `rm`    | Delete a file                                       | `rm temp.txt`          |
| `rm -r` | Remove a directory and all its contents (recursive) | `rm -r old_folder`     |
| `rm -i` | Interactive delete (asks before each removal)       | `rm -i file.txt`       |


**Note:**
rm -r permanently deletes everything inside the directory — there is no “undo.”
Always double-check before pressing Enter.
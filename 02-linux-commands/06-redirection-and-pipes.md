## Redirection and Pipes

Every command in Linux uses three data streams:
- stdin – input (e.g content of a file)
- stdout – normal output (What you see on the terminal)
- stderr – error output (Errors you get when you run a command or process)

Redirection lets you chain commands and redirect from one streams to the other. This is a powerful feature of Linux.

| Operator | Function                               | Example                                 |
| -------- | -------------------------------------  | --------------------------------------- |
| `>`      | Redirect output to a file (overwrite)  | `Cat file1.txt > file2.txt`             |
| `>>`     | Append output to a file                | `echo "more" >> file.txt`               |
| `<`      | Read input from a file                 | `sort < file.txt`                       |
| \|       | Pipe output of one command into another| `cat file.txt \| grep "error"`          |


**Example**: Count error lines in a log file.
```bash
cat app.log | grep "ERROR" | wc -l
```

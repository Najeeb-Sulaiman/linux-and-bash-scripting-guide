## Redirection and Pipes

Redirection lets you chain commands. This is a powerful feature of Linux.

| Operator | Function                               | Example                                 |
| -------- | -------------------------------------  | --------------------------------------- |
| `>`      | Redirect output to a file (overwrite)  | `Cat file1.txt > file2.txt`             |
| `>>`     | Append output to a file                | `echo "more" >> file.txt`               |
| `<`      | Read input from a file                 | `sort < file.txt`                       |
| |        | Pipe output of one command into another| `cat file.txt | grep "error"`           |


**Example**: Count error lines in a log file.

```bash
cat app.log | grep "ERROR" | wc -l
```

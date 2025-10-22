## Manipulate Files and Directory
As a data engineer, you will constantly interact with text files, scripts, and logs. Here are some essential commands to carry out this operations.

| Command                   | Description                                    | Example                                  |
| ------------------------- | ---------------------------------------------- | ---------------------------------------- |
| `touch`                   | Create a new empty file                        | `touch data.txt`                         |
| `touch file1 file2 file3` | Create multiple files at once                  | `touch file1 file2 file3`                |
| `nano`                    | Open a simple text editor                      | `nano notes.txt`                         |
| `vi`                      | Open a powerful text editor (Vim)              | `vi script.sh`                           |
| `cat`                     | Display contents of a file                     | `cat hello.txt`                          |
| `cat file1 file2 > file3` | Combine contents of two files into a new one   | `cat part1.txt part2.txt > combined.txt` |
| `tac`                     | Display file contents in reverse order         | `tac log.txt`                            |
| `more`                    | View long files one page at a time             | `more largefile.txt`                     |
| `less`                    | Scroll through a file interactively            | `less data.txt`                          |
| `head -n 5`               | Show the first 5 lines of a file               | `head -n 5 sample.txt`                   |
| `tail -n 10`              | Show the last 10 lines of a file               | `tail -n 10 sample.txt`                  |
| `tail -f`                 | Continuously monitor file changes (e.g., logs) | `tail -f /var/log/syslog`                |

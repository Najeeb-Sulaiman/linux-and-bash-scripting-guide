## Chaining and Combining Commands

In Linux, you can combine commands logically:

```bash
cmd1 && cmd2     # run cmd2 only if cmd1 succeeds
cmd1 || cmd2     # run cmd2 only if cmd1 fails
cmd1; cmd2       # run both commands sequentially
```

**Example:** Create a logs directory and echo "Created logs folder" to the terminal.
```bash
mkdir logs && echo "Created logs folder"
```
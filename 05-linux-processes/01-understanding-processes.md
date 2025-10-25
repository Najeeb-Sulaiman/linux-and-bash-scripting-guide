## Understanding Processes

### What is a Process?

A **process** is a running instance of a program. Every time you run a command, a new process is created.

For example:

```bash
firefox &
python script.py
```

Each of the above commands runs as a separate process with its own **PID (Process ID)**.

### Important things to note

- **PID**: This is the unique ID assigned to each running process.
   
- **Parent & Child Processes**: A process can start another process (its child). For example, a shell starting python or bash scripts.
    
- **Foreground process**: This is a processes that runs on your terminal.
    
- **Background process**: A process that runs behind the scenes (doesn’t block your terminal).

---
### Viewing and Managing Processes
Linux provides useful commands you can use to check system activities. Below are some common ones.

| Command           | Description                                                 |
| ----------------- | ----------------------------------------------------------- |
| `ps`              | Shows processes running in the current shell                |
| `ps aux`          | Shows all system processes                                  |
| `top`             | Real-time view of processes and CPU/memory usage            |
| `htop`            | Like `top`, but more interactive (requires installation) |
| `pidof <program>` | Finds PID of a process                                      |
| `jobs`            | Lists background processes started in your shell            |

Example: Let's asume you want to show all running Python processes. You can achieve that with the following command.

```bash
ps aux | grep python
```

---
### Starting & Stopping Processes
Below are some common commands to start and stop processe in Linux.

| Action                       | Command Example      | Notes                               |
| ---------------------------- | -------------------- | ----------------------------------- |
| Run in background            | `python script.py &` | The `&` means to detach from terminal |
| Bring to foreground          | `fg`                 | Resumes the last background process |
| Stop process temporarily     | `Ctrl + Z`           | Suspends                            |
| Resume process in background | `bg`                 | Continues a stopped process         |
| Kill process                 | `kill <PID>`         | Gracefully terminate                |
| Force kill                   | `kill -9 <PID>`      | Force termination                   |
| Kill all by name             | `pkill python`       | Terminates all python processes     |

**Please use Use `kill` responsibly, it can stop system-critical processes!**

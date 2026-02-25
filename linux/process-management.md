# Process Management

## Viewing Running Processes

To view all running processes:

```bash
ps aux
```

**Explanation:**

- `ps` → process status  
- `a` → show processes for all users  
- `u` → user-oriented format  
- `x` → include processes not attached to a terminal  

This displays all active processes including their:

- USER  
- PID (Process ID)  
- %CPU and %MEM usage  
- TTY (terminal session)  
- STAT (process state)  
- COMMAND  

The **PID** uniquely identifies each running process.

---

## Filtering Processes

To filter specific processes:

```bash
ps aux | grep bash
```

**Explanation:**

- `|` (pipe) sends output of `ps aux` into `grep`  
- `grep bash` filters for lines containing "bash"  

Note: The `grep` command itself appears in the results because it also contains the word "bash".

---

## Real-Time Monitoring

To monitor processes in real time:

```bash
top
```

Press `q` to quit.

`top` shows live CPU and memory usage for running processes.

---

## Running a Background Process

To start a process in the background:

```bash
sleep 200 &
```

**Explanation:**

- `sleep 200` pauses for 200 seconds  
- `&` runs the command in the background  

The terminal returns something like:

```
[1] 5819
```

- `[1]` = job number  
- `5819` = PID  

To see background jobs:

```bash
jobs
```

---

## Finding the PID

To confirm the process:

```bash
ps aux | grep sleep
```

This shows the running `sleep` process and its PID.

---

## Killing a Process

To stop the process:

```bash
kill 5819
```

Replace `5819` with the actual PID.

After killing:

```bash
ps aux | grep sleep
jobs
```

The sleep process should no longer appear, and no background jobs should be listed.

---

## What I Learned

- Every running program in Linux is a process  
- Each process has a unique PID  
- Background processes can be managed using `jobs`  
- `ps`, `grep`, and `kill` are essential for process control  
- Process management is critical for maintaining system stability  
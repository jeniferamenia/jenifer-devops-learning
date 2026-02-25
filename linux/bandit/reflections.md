# Linux Module Reflections

## Module Overview

This Linux module moved me from running isolated commands to understanding how Linux systems function as a whole. Instead of memorising syntax, I began recognising patterns in how processes, permissions, and text streams interact within a system.

---

## Core Linux Skills Developed

### File System Navigation

Working entirely through the terminal improved my ability to navigate directories without relying on a graphical interface. Commands like `cd`, `ls -lah`, and `pwd` became muscle memory.

I gained a clearer understanding of how Linux structures system-critical directories such as:

- `/etc` (configuration)
- `/var` (logs and variable data)
- `/home` (user directories)

---

### Permissions and Ownership

Understanding permissions was a major turning point.

Key concepts internalised:

- Owner vs group vs others
- Difference between file and directory execute permissions
- Numeric permissions (e.g. 644, 755)
- Role of `sudo` in privileged operations

This reinforced how Linux enforces security boundaries in multi-user systems.

---

### Process Management

Managing processes using:

- `ps aux`
- `grep`
- `jobs`
- `kill`

Helped me understand how servers continuously run services in the background and how administrators identify and terminate processes when needed.

Running background jobs and manually killing them reinforced how PID tracking works.

---

### Text Processing

Using:

- `grep` for filtering
- `awk` for field extraction
- `sed` for substitution
- Pipes (`|`) to chain commands

Demonstrated how powerful Linux is for log analysis and automation without external tools.

Understanding field positions in `/etc/passwd` using `-F:` clarified how structured text can be parsed programmatically.

---

## Bandit Challenge (Levels 1–20)

The Bandit wargame strengthened problem-solving and command composition skills.

Key areas reinforced:

- Finding hidden files
- Using `find` with multiple conditions
- Checking file types with `file`
- Working with compression formats
- Handling unusual file names
- SSH workflow familiarity

Rather than guessing commands, I had to combine tools logically to solve each level.

---

## Challenges Encountered

- Remembering when `grep` includes itself in results
- Understanding why directory execute permission controls entry access
- Recognising when to use `-p` in `mkdir`
- Interpreting output formats from `ps aux`

Each issue improved my ability to read terminal output carefully instead of reacting blindly.

---

## Why This Module Matters for DevOps

Linux underpins:

- Cloud infrastructure
- Docker containers
- CI/CD pipelines
- Kubernetes clusters
- Server administration

Being comfortable in the terminal reduces friction when working with infrastructure tools and remote systems.

---

## Personal Progress

At the beginning of the module, I relied heavily on copying commands.

By the end, I:

- Understood why commands worked
- Could chain tools together intentionally
- Interpreted error messages more confidently
- Thought in terms of system behaviour rather than isolated commands

This module established the foundation required for the next stages of DevOps learning. 
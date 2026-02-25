# Linux Module – DevOps learning

## Overview

This module focused on building foundational Linux command-line skills required for DevOps engineering.

All core tasks were completed, including structured practice of file system navigation, permissions, shell configuration, user management, redirection, piping, and completing OverTheWire Bandit Levels 1–20.

---

## Core Skills Covered

### File System Navigation
- Used `pwd`, `cd`, `cd ..`, `cd ~` to move confidently between directories
- Listed files using `ls`, `ls -la`, `ls -l`, and `ls -R`
- Created and removed directories using `mkdir`, `mkdir -p`, `rmdir`, `rm -r`
- Managed files using `touch`, `cp`, `cp -r`, `mv`, `rm`

### File Inspection & Search
- Viewed files using `cat`, `head`, `tail`, `head -n`
- Located files using `find`
- Filtered content using `grep`
- Located binaries using `which`
- Inspected system structure (`/`, `/home`, `/etc`, `/bin`, `/var`)

### Permissions & Ownership
- Understood permission values: `r=4`, `w=2`, `x=1`
- Applied common permission modes: `755`, `644`, `600`
- Used `chmod` (numeric and symbolic)
- Changed ownership using `chown`, `chgrp`
- Practiced recursive permission changes

### User & Group Management
- Used `sudo`, `su`, `whoami`, `id`
- Created users with `useradd`
- Set passwords with `passwd`
- Managed groups with `groupadd`, `usermod -aG`, `deluser`
- Tested permission boundaries between users

### Redirection & Pipes
- Redirected output using `>`, `>>`
- Redirected errors using `2>`
- Redirected both streams using `&>`
- Built pipelines using `|`
- Practiced multi-stage command chaining

### Environment & Shell Configuration
- Managed environment variables using `export`, `echo $VAR`, `printenv`
- Checked shell using `echo $SHELL`
- Switched shells using `bash`, `zsh`
- Edited `.bashrc` / `.zshrc`
- Created aliases
- Configured Oh My Zsh
- Used history features and terminal shortcuts

### VIM Usage
- Insert mode, command mode
- Save/quit operations
- Navigation (`h/j/k/l`)
- Search and replace
- Line manipulation (`dd`, `yy`, `p`)
- Undo/redo
- Line numbers and movement

---

## Practical Application – Bandit (Levels 1–20)

Completed OverTheWire Bandit Levels 1–20 to apply Linux fundamentals in structured challenges.

Skills applied:
- SSH connections
- Reading hidden files
- Handling files with unusual names
- Searching using `find` and `grep`
- Filtering unique lines
- Decoding Base64
- Applying ROT13 transformations
- Inspecting binary files using `strings`
- Working with permissions and setuid binaries
- Using `nc` for local port connections

Challenge reference:
https://overthewire.org/wargames/bandit/

Solutions documented in:

`linux/bandit/bandit-levels-1-20.md`

---

## Repository Structure

```
linux/
│
├── environment-setup.md
├── file-system-notes.md
├── permissions-and-ownership.md
├── process-management.md
├── text-processing.md
├── bandit/
│   ├── bandit-levels-1-20.md
│   ├── reflections.md
│   └── screenshots/
└── scripts/
    └── hello.sh
```

---

## DevOps Relevance

Linux is the operating system behind most production servers, cloud infrastructure, and CI/CD environments.

This module builds:

- Command-line fluency  
- Permission awareness  
- Process understanding  
- Shell configuration skills  
- Structured troubleshooting habits  

These fundamentals are required before progressing into Bash scripting, Docker, CI/CD pipelines, and cloud platforms.

---

## Outcome

Comfortable navigating and operating within a Linux environment entirely via terminal.

Prepared to build automation workflows and infrastructure tooling in the next modules.

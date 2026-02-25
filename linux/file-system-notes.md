# File System Navigation

## Overview

This section covers navigating the Linux file system, creating and managing files and directories, and understanding how commands behave in different contexts.

---

## Navigating Directories

### `cd`

Changes the current working directory.

- `cd ~` moves to the home directory.
- `cd /var/log` moves to a system directory.
- `cd ..` moves up one directory level.

Understanding directory navigation is critical when working on servers, as most DevOps tasks involve moving between system paths.

---

### `pwd`

Prints the current working directory.

This is useful to confirm your location before creating, modifying, or deleting files.

Example:

```bash
pwd
```

---

## Listing Files

### `ls -lah`

Lists directory contents in long format.

- `-l` → shows permissions, owner, size, and timestamps
- `-a` → shows hidden files
- `-h` → shows human-readable sizes (KB, MB)

Example:

```bash
ls -lah
```

This command is frequently used to inspect server directories.

---

## Creating Files and Directories

### `touch`

Creates an empty file.

Example:

```bash
touch test.txt
```

---

### `mkdir -p`

Creates directories, including parent directories if they do not exist.

Example:

```bash
mkdir -p projects/demo
```

The `-p` flag makes the command idempotent.  
If the directory already exists, it does not produce an error.

This is important in automation scripts and CI/CD pipelines where commands may run multiple times.

---

## Copying and Moving Files

### `cp`

Copies files from one location to another.

Example:

```bash
cp test.txt projects/demo/
```

---

### `mv`

Moves or renames files.

Example:

```bash
mv projects/demo/test.txt projects/demo/backup.txt
```

`mv` can either move files to a different directory or rename them in the same directory.

---

## Removing Files

### `rm`

Deletes files permanently.

Example:

```bash
rm projects/demo/backup.txt
```

There is no recycle bin in the Linux terminal.  
Deleted files cannot be easily recovered.

---

## Key Learning

Understanding file system navigation is foundational in DevOps.  
Most production servers are Linux-based, and managing files, logs, configuration directories, and deployment artifacts requires confidence with these commands. 
# Permissions and Ownership

## Creating a Script

To create a simple Bash script:

```bash
echo '#!/bin/bash' > hello.sh
echo 'echo "Hello DevOps"' >> hello.sh
```

**Explanation:**

- `#!/bin/bash` is called a **shebang**
- It tells Linux which interpreter should execute the script
- `>` creates/overwrites a file
- `>>` appends to a file

---

## Making the Script Executable

By default, new files are not executable.

To make the script executable:

```bash
chmod +x hello.sh
```

**Explanation:**

- `chmod` = change mode (permissions)
- `+x` = add execute permission
- This allows the file to be run as a program

To run it:

```bash
./hello.sh
```

`./` means "run the file from the current directory".

---

## Understanding File Permissions

To view permissions:

```bash
ls -l hello.sh
```

Example output:

```
-rwxr-xr-x 1 jamenia jamenia 32 Feb 25 20:00 hello.sh
```

### Breaking It Down

```
-rwxr-xr-x
```

- First character:
  - `-` = regular file
  - `d` = directory

Then permissions are split into 3 groups:

```
rwx r-x r-x
│   │   │
│   │   └── Others
│   └────── Group
└────────── Owner
```

Permission meanings:

For files:
- `r` = read file contents
- `w` = modify file
- `x` = execute file

For directories:
- `r` = list directory contents
- `w` = create/delete files inside
- `x` = enter directory

---

## Changing Ownership

To change the owner of a file:

```bash
sudo chown root:root hello.sh
```

**Explanation:**

- `chown` = change owner
- `root:root` = owner and group
- `sudo` required because only root can change ownership

---

## Challenge: Custom Permissions

Create a file:

```bash
touch secure.txt
```

Set permissions so:

- Owner: read + write
- Group: read only
- Others: read only

```bash
chmod 644 secure.txt
```

### Why 644?

Permission numbers:

- 4 = read
- 2 = write
- 1 = execute

So:

- 6 = 4 + 2 = read + write
- 4 = read
- 4 = read

Result:

```
-rw-r--r--
```

Owner can read/write.
Group and others can only read.

---

## What I Learned

- Linux permissions control who can access files and directories
- Permissions are divided into owner, group, and others
- `chmod` modifies permissions
- `chown` changes file ownership
- Numeric permissions (e.g., 644, 755) represent read, write, execute combinations
- Understanding permissions is essential for server security and DevOps workflows

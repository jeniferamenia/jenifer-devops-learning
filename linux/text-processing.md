# Text Processing

This section demonstrates practical use of `grep`, `awk`, `sed`, and command piping in a Linux environment.

---

## Searching with grep

Search for a specific user:

```bash
grep "root" /etc/passwd
```

Output:

```
root:x:0:0:root:/root:/bin/bash
```

This shows the full entry for the root user.

---

### Case-Insensitive Search

```bash
grep -i "bash" /etc/passwd
```

Output:

```
root:x:0:0:root:/root:/bin/bash
jamenia:x:1000:1000:,,,:/home/jamenia:/bin/bash
```

This lists users whose shell contains `/bin/bash`.

---

### Counting Matches

```bash
grep -i "bash" /etc/passwd | wc -l
```

Output:

```
2
```

There are 2 users with `/bin/bash` as their login shell.

---

## Using awk

Extract selected columns from running processes:

```bash
ps aux | awk '{print $1, $11}'
```

This prints:

- `$1` → user
- `$11` → command

Example output included:

```
root /sbin/init
jamenia -bash
```

---

### Parsing /etc/passwd

List users whose shell is `/bin/bash`:

```bash
awk -F: '$7 == "/bin/bash" {print $1}' /etc/passwd
```

Output:

```
root
jamenia
```

Explanation:

- `-F:` sets `:` as field separator
- `$7` refers to the shell field
- `$1` prints the username

---

## Using sed (Stream Editor)

Create a test file:

```bash
echo "apple banana apple" > file.txt
```

Replace all occurrences of "apple" with "orange":

```bash
sed 's/apple/orange/g' file.txt
```

Output:

```
orange banana orange
```

Explanation:

- `s` = substitute
- `apple` = pattern
- `orange` = replacement
- `g` = replace all matches on the line

Without `g`, only the first occurrence per line would be replaced.

---

## What I Learned

- `grep` searches for patterns inside files
- `wc -l` counts lines (useful for log analysis)
- `awk` extracts structured fields from text output
- `sed` modifies text streams using substitution syntax
- Pipes (`|`) allow chaining commands together
- Linux text processing tools are powerful for analysing logs, configuration files, and system output 
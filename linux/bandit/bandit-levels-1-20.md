# OverTheWire Bandit – Levels 1–20

This document summarises the commands and reasoning used to complete Bandit Levels 1–20.

---

## Bandit Level 0 → 1

### Objective
Read the password stored in the `README` file.

### Command Used
```bash
cat README
```

### Why It Works
`cat` prints file contents to the terminal. The password was stored directly inside the file.

### Skill Reinforced
Basic file inspection.

---

## Bandit Level 1 → 2

### Objective
Read a file literally named `-`.

### Command Used
```bash
cat ./-
```

### Why It Works
Files beginning with `-` can be interpreted as flags. Using `./` explicitly references it as a file in the current directory.

### Skill Reinforced
Handling edge-case filenames.

---

## Bandit Level 2 → 3

### Objective
Read a file with spaces in its name.

### Command Used
```bash
cat "spaces in this filename"
```

### Why It Works
Quoting prevents the shell from splitting the filename into separate arguments.

### Skill Reinforced
Proper handling of filenames with spaces.

---

## Bandit Level 3 → 4

### Objective
Find the password stored in a hidden file.

### Commands Used
```bash
cd inhere
ls -la
cat .hidden
```

### Why It Works
Hidden files begin with `.` and require `ls -la` to be visible.

### Skill Reinforced
Understanding hidden files and directory inspection.

---

## Bandit Level 4 → 5

### Objective
Find the only human-readable file among many.

### Commands Used
```bash
cd inhere
file ./*
cat ./-fileXX
```

### Why It Works
`file` identifies file types. Only one file was ASCII text.

### Skill Reinforced
Using file type inspection to filter results.

---

## Bandit Level 5 → 6

### Objective
Find a file that is:
- Human-readable
- 1033 bytes
- Not executable

### Command Used
```bash
find . -type f -size 1033c ! -executable
```

### Why It Works
`find` allows filtering by file type, size, and execution permissions.

### Skill Reinforced
Advanced file searching with constraints.

---

## Bandit Level 6 → 7

### Objective
Search the entire system for a file:
- 33 bytes
- Owned by bandit7
- Group bandit6

### Command Used
```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
```

### Why It Works
- `-user` and `-group` filter ownership
- `2>/dev/null` suppresses permission errors

### Skill Reinforced
System-wide search and error redirection.

---

## Bandit Level 7 → 8

### Objective
Find the password next to the word "millionth".

### Command Used
```bash
grep "millionth" data.txt
```

### Why It Works
`grep` searches for matching patterns inside files.

### Skill Reinforced
Text filtering.

---

## Bandit Level 8 → 9

### Objective
Find the only line that occurs once.

### Command Used
```bash
sort data.txt | uniq -u
```

### Why It Works
- `sort` groups identical lines
- `uniq -u` outputs only unique entries

### Skill Reinforced
Combining pipes for data processing.

---

## Bandit Level 9 → 10

### Objective
Extract readable strings from a binary file.

### Command Used
```bash
strings data.txt | grep "="
```

### Why It Works
`strings` extracts printable characters from binary files.

### Skill Reinforced
Binary inspection.

---

## Bandit Level 10 → 11

### Objective
Decode Base64 encoded content.

### Command Used
```bash
base64 -d data.txt
```

### Why It Works
`base64 -d` decodes encoded data.

### Skill Reinforced
Working with encoded data.

---

## Bandit Level 11 → 12

### Objective
Decode a ROT13 encoded file.

### Command Used
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### Why It Works
`tr` translates characters according to the ROT13 substitution cipher.

### Skill Reinforced
Character transformation using `tr`.

---

## Bandit Level 12 → 13

### Objective
Extract the password from a repeatedly compressed file.

### Commands Used
```bash
file data.txt
mv data.txt data.gz
gzip -d data.gz
# repeated based on file type (gzip, bzip2, tar, etc.)
```

### Why It Works
The file was compressed multiple times using different formats.  
`file` identifies the current format, allowing proper decompression step-by-step.

### Skill Reinforced
- File type inspection
- Layered decompression
- Not trusting file extensions blindly

---

## Bandit Level 13 → 14

### Objective
Log in using an SSH private key instead of a password.

### Command Used
```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

### Why It Works
The `-i` flag specifies a private key file for authentication.

### Skill Reinforced
SSH key-based authentication.

---

## Bandit Level 14 → 15

### Objective
Submit the current password to a service listening on localhost port 30000.

### Command Used
```bash
echo "current_password" | nc localhost 30000
```

### Why It Works
`nc` (netcat) connects to a TCP port and sends input from standard input.

### Skill Reinforced
Basic TCP communication using netcat.

---

## Bandit Level 15 → 16

### Objective
Submit the password to a service using SSL/TLS encryption.

### Command Used
```bash
echo "current_password" | openssl s_client -connect localhost:30001 -quiet
```

### Why It Works
The service required encrypted communication.  
`openssl s_client` establishes an SSL/TLS connection.

### Skill Reinforced
Understanding encrypted network connections.

---

## Bandit Level 16 → 17

### Objective
Scan ports 31000–32000 to find the correct SSL-enabled service.

### Commands Used
```bash
nmap -p 31000-32000 -sV localhost
echo "current_password" | openssl s_client -connect localhost:31790 -quiet
```

### Why It Works
- `nmap` identifies open ports and service types
- Only one port accepted SSL and returned credentials

### Skill Reinforced
Port scanning and service detection.

---

## Bandit Level 17 → 18

### Objective
Identify the changed line between `passwords.old` and `passwords.new`.

### Command Used
```bash
diff passwords.old passwords.new
```

### Why It Works
`diff` compares files line-by-line and highlights differences.

### Skill Reinforced
File comparison and output interpretation.

---

## Bandit Level 18 → 19

### Objective
Retrieve the password from `readme` despite automatic logout on SSH login.

### Command Used
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

### Why It Works
Executing a command directly over SSH bypasses interactive shell startup.

### Skill Reinforced
Understanding shell initialisation and command execution via SSH.

---

## Bandit Level 19 → 20

### Objective
Use the setuid binary to access the password stored in `/etc/bandit_pass`.

### Command Used
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

### Why It Works
The setuid binary runs with elevated privileges, allowing access to restricted files.

### Skill Reinforced
Understanding setuid binaries and privilege escalation boundaries.

---

## Bandit Level 20 → 21

### Objective
Run a local listener and use the provided setuid binary to send the correct password over a port.

### Commands Used

Terminal 1:
```bash
nc -l -p 4444
```

Terminal 2:
```bash
./suconnect 4444
```

### Why It Works
- `nc -l -p 4444` creates a listening service
- The setuid binary connects to the specified port
- If the correct password is provided, the next password is transmitted

### Skill Reinforced
- Local port communication
- Understanding client/server interaction
- Coordinating multiple terminal sessions


---

## Key Takeaways

### 1. Linux Is About Precision
Small details matter:
- Quoting filenames
- Redirecting errors
- Using `./` for special filenames
- Suppressing noisy output with `2>/dev/null`

Many failures were caused by incorrect assumptions about how the shell parses input.

---

### 2. Trust Tools, Not File Extensions
Using `file` repeatedly during compression challenges reinforced that extensions are not authoritative.

Inspect first. Assume nothing.

---

### 3. Pipes Are Extremely Powerful
Combining tools like:

```bash
sort | uniq
grep | wc -l
strings | grep
```

demonstrated how small utilities can be chained into powerful workflows.

---

### 4. Networking Is Still Just Input and Output
Levels involving `nc`, `openssl`, and port scanning reinforced that:

- Services listen on ports  
- Clients send data  
- Correct input produces correct output  

Understanding this model simplifies debugging.

---

### 5. Permissions Define Boundaries
Setuid challenges reinforced that:

- Execution context matters  
- User identity determines access  
- Privilege boundaries are intentional  

Security is built on correct permission management.

---

### 6. Error Messages Are Information
Instead of ignoring errors, reading them carefully often revealed the exact issue (wrong port, wrong flag, permission denied, etc.).

Learning to interpret error output is a critical troubleshooting skill.

---

## Overall Impact

Bandit transformed theoretical Linux commands into practical problem-solving tools.

It reinforced:
- Structured troubleshooting
- Reading documentation (`man`)
- Breaking problems into smaller steps
- Verifying assumptions before acting

This experience strengthened command-line confidence and improved system-level thinking.
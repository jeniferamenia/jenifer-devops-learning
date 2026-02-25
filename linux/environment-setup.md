# Linux Environment Setup

## Environment Used

- **Platform:** WSL2 (Windows Subsystem for Linux)
- **Distribution:** Ubuntu 24.04.4 LTS
- **Architecture:** x86_64
- **Previous Setup:** Ubuntu Virtual Machine (scrapped)
- **Current Setup:** WSL only (single Linux environment)

---

## Verification Commands

The following commands were used to verify the Linux installation:

```bash
uname -a
whoami
pwd
lsb_release -a
```

---

## Command Outputs

### uname -a

```bash
Linux LAPTOP-0FHQ8J5J 6.6.87.2-microsoft-standard-WSL2 #1 SMP PREEMPT_DYNAMIC Thu Jun 5 18:30:46 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux
```

### whoami

```bash
jamenia
```

### pwd

```bash
/home/jamenia
```

### lsb_release -a

```bash
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.4 LTS
Release:        24.04
Codename:       noble
```

---

## Project Directory Structure

All Linux module work is stored in:

```bash
/home/jamenia/devops-learning/linux
```
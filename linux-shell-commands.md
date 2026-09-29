# Linux & Shell Scripting Commands Cheat Sheet

A beginner-friendly collection of commonly used Linux commands and basic shell scripting commands.

---

## 1. `ls` — List files and directories

Shows files and directories in the current location.

```bash
ls
```

### Useful options

```bash
ls -ltr
```
Lists files in long format, sorted by modification time.

```bash
ls -a
```
Shows hidden files also.

---

## 2. `man` — Manual/help

Shows the manual page of a command.

```bash
man ls
```

Press `q` to exit the manual.

---

## 3. `cat` — Display file content

```bash
cat file.txt
```

Displays the contents of `file.txt`.

---

## 4. `cd` — Change directory

```bash
cd /home/user
```

Move to a specific directory.

```bash
cd ..
```

Move one directory back.

```bash
cd ../..
```

Move two directories back.

```bash
cd ~
```

Go to the home directory.

---

## 5. `touch` — Create an empty file

```bash
touch file.txt
```

Creates `file.txt` if it does not exist.

---

## 6. `vi` / `vim` — Edit a file

```bash
vi file.txt
```

or

```bash
vim file.txt
```

### Basic `vi` commands

```text
i       → Insert/write mode
Esc     → Exit insert mode
:w      → Save
:q      → Quit
:wq     → Save and quit
:q!     → Quit without saving
```

---

## 7. `mkdir` — Create directory

```bash
mkdir myfolder
```

Creates a directory named `myfolder`.

```bash
mkdir -p project/src
```

Creates parent directories if required.

---

## 8. `rm` — Remove files

```bash
rm file.txt
```

Deletes a file.

### Remove directory recursively

```bash
rm -r myfolder
```

Deletes a directory and its contents.

> Be careful with `rm -r` because deleted files may not be recoverable.

---

## 9. `rmdir` — Remove empty directory

```bash
rmdir myfolder
```

Works only when the directory is empty.

---

# Shell Script Basics

## 10. Create a Shell Script

Create a file:

```bash
vi abc.sh
```

Add:

```bash
#!/bin/bash

echo "Hello World"
echo "My first shell script"
```

Save and exit:

```text
Esc
:wq
```

---

## 11. Execute a Shell Script

### Method 1 — Using `sh`

```bash
sh abc.sh
```

### Method 2 — Using bash

```bash
bash abc.sh
```

### Method 3 — Using `./`

First give execute permission:

```bash
chmod +x abc.sh
```

Then execute:

```bash
./abc.sh
```

---

## 12. `exit` — Exit from shell/script

```bash
exit
```

Exits the current shell/session.

Inside a script:

```bash
#!/bin/bash

echo "Script started"
exit 0
echo "This will not execute"
```

`exit 0` normally indicates successful execution.

---

# System Monitoring Commands

## 13. `free -g` — Memory usage

```bash
free -g
```

Shows RAM and swap usage in GB.

---

## 14. `df -h` — Disk usage

```bash
df -h
```

Shows filesystem disk usage in human-readable format.

---

## 15. `top` — System processes

```bash
top
```

Shows running processes and CPU/memory usage in real time.

Press `q` to exit.

---

## 16. `ps -ef` — Running processes

```bash
ps -ef
```

Displays detailed information about currently running processes.

Example:

```bash
ps -ef | grep nginx
```

Finds processes related to `nginx`.

> Note: The correct command is `ps -ef`, not `pf -ef`.

---

# File Permissions

## 17. `chmod` — Change permissions

Linux permissions are given to:

```text
User (Owner) → Group → Others
```

Three basic permissions:

```text
r = Read    = 4
w = Write   = 2
x = Execute = 1
```

Therefore:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4 + 1     = 5
r-- = 4
-w- = 2
--x = 1
--- = 0
```

### Example

```bash
chmod 777 file.sh
```

Meaning:

```text
User   → 7 → rwx
Group  → 7 → rwx
Others → 7 → rwx
```

So:

```text
777 = rwxrwxrwx
```

### Common example

```bash
chmod 755 abc.sh
```

Meaning:

```text
User   → 7 → rwx
Group  → 5 → r-x
Others → 5 → r-x
```

So:

```text
755 = rwxr-xr-x
```

---

# `awk` Command

## 18. `awk` — Process and extract text

`awk` is commonly used to process columns from text output.

Example:

```bash
awk '{print $1}' file.txt
```

Prints the first column.

Example with `/etc/passwd`:

```bash
awk -F: '{print $1}' /etc/passwd
```

Prints usernames.

---

# `set` Commands in Shell

## 19. `set -x` — Debugging

Shows commands while the script is executing.

```bash
#!/bin/bash

set -x

name="Abhilash"
echo "Hello $name"
```

Useful for debugging shell scripts.

Turn it off:

```bash
set +x
```

---

## 20. `set -e` — Stop on error

Stops the script when a command fails.

```bash
#!/bin/bash

set -e

echo "Starting"

ls /wrong-folder

echo "This will not execute"
```

Because `ls /wrong-folder` fails, the script stops.

Turn it off:

```bash
set +e
```

---

## 21. `set -o` — Shell options

Displays shell options:

```bash
set -o
```

You can enable an option:

```bash
set -o xtrace
```

This is equivalent to:

```bash
set -x
```

Another example:

```bash
set -o errexit
```

This is equivalent to:

```bash
set -e
```

---

# Pipes

## 22. `|` — Pipe

A pipe sends the output of one command as input to another command.

Example:

```bash
ls -l | grep ".txt"
```

Meaning:

```text
ls -l → output → grep → filter .txt files
```

Another example:

```bash
ps -ef | grep nginx
```

---

# Date and History

## 23. `date` — Show date and time

```bash
date
```

Example:

```bash
date "+%Y-%m-%d %H:%M:%S"
```

---

## 24. `history` — Show previous commands

```bash
history
```

Shows previously executed commands.

Example:

```bash
history | tail
```

Shows the last few commands.

Run a previous command:

```bash
!100
```

Runs command number 100 from history.

---

# Useful Basic Commands

## 25. `pwd` — Current directory

```bash
pwd
```

Shows the current working directory.

---

## 26. `clear` — Clear terminal

```bash
clear
```

Clears the terminal screen.

---

## 27. `whoami` — Current user

```bash
whoami
```

Shows the username of the currently logged-in user.

---

## 28. `hostname` — System hostname

```bash
hostname
```

Shows the machine/server hostname.

---

## 29. `echo` — Print text

```bash
echo "Hello Linux"
```

Prints text to the terminal.

---

# Mini Shell Script Example

Create the file:

```bash
vi system_info.sh
```

Add:

```bash
#!/bin/bash

set -e

echo "===== System Information ====="

echo "User:"
whoami

echo "Current Directory:"
pwd

echo "Date:"
date

echo "Memory:"
free -g

echo "Disk:"
df -h

echo "Running Processes:"
ps -ef | head

echo "===== Script Completed ====="
```

Save:

```text
Esc
:wq
```

Give permission:

```bash
chmod +x system_info.sh
```

Run:

```bash
./system_info.sh
```

---

# Quick Revision

| Command | Purpose |
|---|---|
| `ls` | List files |
| `ls -ltr` | Long listing, sorted by time |
| `ls -a` | Show hidden files |
| `man` | Command manual |
| `cat` | Display file |
| `cd` | Change directory |
| `cd ..` | Go one directory back |
| `touch` | Create file |
| `vi` / `vim` | Edit file |
| `mkdir` | Create directory |
| `rm` | Remove file |
| `rm -r` | Remove directory recursively |
| `rmdir` | Remove empty directory |
| `sh file.sh` | Execute shell script |
| `chmod` | Change permissions |
| `free -g` | Memory usage |
| `df -h` | Disk usage |
| `top` | Live process monitoring |
| `ps -ef` | List processes |
| `awk` | Process/extract text |
| `set -x` | Debug/tracing |
| `set -e` | Stop on error |
| `set -o` | Shell options |
| `\|` | Pipe output |
| `date` | Date/time |
| `history` | Command history |
| `pwd` | Current directory |
| `whoami` | Current user |
| `echo` | Print text |

---

## GitHub Upload

Save this file as:

```text
linux-shell-commands.md
```

Then:

```bash
git add linux-shell-commands.md
git commit -m "Add Linux and Shell Scripting commands"
git push
```

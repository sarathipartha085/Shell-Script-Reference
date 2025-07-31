---

## 📘 Module 1: Introduction to Shell and Linux

---

### 🔹 **1. What is a Shell? Types of Shells**

A **shell** is a program that takes your commands (as text input) and passes them to the operating system to execute. It acts as a command-line interpreter.

#### Common Shells:

| Shell        | Description                                                          |
| ------------ | -------------------------------------------------------------------- |
| **bash**     | Bourne Again SHell – Most common shell in Linux                      |
| **sh**       | Original Bourne Shell – simpler, more portable                       |
| **zsh**      | Z Shell – like bash but with more features (auto-completion, themes) |
| **fish**     | Friendly Interactive SHell – user-friendly, not POSIX-compliant      |
| **csh/tcsh** | C-like shell, mostly used in some legacy systems                     |

---

### 🔹 **2. Terminal vs Shell vs Console**

| Term         | Meaning                                                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Terminal** | A program (like GNOME Terminal or iTerm2) that gives you access to the shell. It's a "window" to the shell.                                 |
| **Shell**    | The command interpreter that runs inside the terminal (e.g., bash).                                                                         |
| **Console**  | Originally referred to a physical terminal (like a keyboard+monitor connected to a server), now often used interchangeably with "terminal". |

> 🧠 Think of it like this: Console = Hardware interface, Terminal = Software window, Shell = Program that runs your commands.

---

### 🔹 **3. Basic Linux Commands**

These are the most frequently used commands:

| Command | Description                         |
| ------- | ----------------------------------- |
| `ls`    | List files and directories          |
| `cd`    | Change directory                    |
| `pwd`   | Print working directory             |
| `man`   | Manual/help for commands (`man ls`) |
| `cp`    | Copy files/directories              |
| `mv`    | Move or rename files/directories    |
| `rm`    | Remove files/directories            |
| `mkdir` | Make new directory                  |

> 📌 Example:

```bash
mkdir my_folder
cd my_folder
touch file.txt
ls
```

---

### 🔹 **4. File System Hierarchy**

Linux organizes files in a hierarchical structure like an upside-down tree. Key directories:

| Directory | Purpose                                            |
| --------- | -------------------------------------------------- |
| `/`       | Root directory – everything starts here            |
| `/home`   | User home directories (`/home/alice`, `/home/bob`) |
| `/etc`    | Configuration files                                |
| `/var`    | Variable files like logs, mail, spool              |
| `/bin`    | Essential user binaries (commands)                 |
| `/usr`    | User programs and data (non-essential)             |
| `/tmp`    | Temporary files                                    |
| `/dev`    | Device files (e.g., `/dev/sda` for disks)          |

> 🧠 `cd /` takes you to the root of this structure.

---

### 🔹 **5. File Permissions and Ownership**

In Linux, each file/directory has:

* **Owner** (user)
* **Group**
* **Permissions** (Read, Write, Execute)

You can view them using:

```bash
ls -l
```

Example output:

```
-rw-r--r-- 1 alice users 1234 Jul 31  file.txt
```

* `rw-` → user (alice) can read/write
* `r--` → group can read
* `r--` → others can read

Commands:

* `chmod` → change permissions
* `chown` → change owner
* `umask` → default permission mask for new files

> 📌 Example:

```bash
chmod +x script.sh
chown bob file.txt
```

---

### 🔹 **6. Redirection and Pipes**

These are used to handle input and output in powerful ways.

| Symbol | Meaning                         | Example                     |                  |            |
| ------ | ------------------------------- | --------------------------- | ---------------- | ---------- |
| `>`    | Redirect stdout (overwrite)     | `echo "Hi" > file.txt`      |                  |            |
| `>>`   | Redirect stdout (append)        | `echo "Bye" >> file.txt`    |                  |            |
| `<`    | Redirect input                  | `wc -l < file.txt`          |                  |            |
| \`     | \`                              | Pipe output to next command | \`ls             | grep txt\` |
| `tee`  | Write output to file and screen | \`echo "log"                | tee output.txt\` |            |

---

### 🔹 **7. Wildcards and Globbing**

Used to match multiple files based on patterns:

| Symbol | Matches                 |                                                    |
| ------ | ----------------------- | -------------------------------------------------- |
| `*`    | Zero or more characters | `ls *.txt` matches all `.txt` files                |
| `?`    | Exactly one character   | `ls file?.txt` matches `file1.txt`, `fileA.txt`    |
| `[]`   | Character set           | `ls file[12].txt` matches `file1.txt`, `file2.txt` |

---

### ✅ Summary:

By the end of Module 1, you should be able to:

* Understand what a shell is and navigate in it
* Use essential Linux commands
* Understand Linux directory structure
* Handle file permissions and ownership
* Use redirection and pipes
* Match file patterns with wildcards

---

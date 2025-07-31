---

## 🗂️ Shell Scripting Syllabus (Beginner to Advanced)

---

### 📘 **Module 1: Introduction to Shell and Linux**

**Objective**: Understand what the shell is, and basic Linux usage.

* What is a shell? Types of shells (bash, zsh, etc.)
* Terminal vs shell vs console
* Basic Linux commands (`ls`, `cd`, `pwd`, `man`, `cp`, `mv`, `rm`, `mkdir`, etc.)
* File system hierarchy (`/home`, `/etc`, `/var`, etc.)
* File permissions and ownership (`chmod`, `chown`, `umask`)
* Redirection and pipes (`>`, `>>`, `<`, `|`, `tee`)
* Wildcards and globbing (`*`, `?`, `[]`)

---

### 📘 **Module 2: Getting Started with Bash Scripting**

**Objective**: Learn to write and run your first shell scripts.

* Writing your first shell script
* Script permissions and execution (`chmod +x`, `./script.sh`)
* `#!/bin/bash` – Shebang explained
* `echo`, `read`, `printf`
* Comments and best practices
* Using variables and constants
* Quotes: single `'`, double `"`, backticks `` ` ``

---

### 📘 **Module 3: Control Structures**

**Objective**: Learn how to add logic to your scripts.

* Conditional statements:

  * `if`, `else`, `elif`
  * `test`, `[ ]`, `[[ ]]` usage
* Case statement:

  * `case...esac`
* Loops:

  * `for`, `while`, `until`
* Loop control: `break`, `continue`

---

### 📘 **Module 4: Functions and Scope**

**Objective**: Structure scripts using functions.

* Defining and calling functions
* Local and global variables
* Function return values
* `$?` and exit status

---

### 📘 **Module 5: Command-line Arguments**

**Objective**: Make scripts dynamic.

* `$0`, `$1`, `$2`, ..., `$#`, `$*`, `$@`
* Shift and processing arguments
* `getopts` for parsing flags/options

---

### 📘 **Module 6: Input/Output and Files**

**Objective**: Work with files and user input/output.

* Reading user input
* Reading and writing files
* File testing (`-f`, `-d`, `-e`, `-r`, `-w`, `-x`)
* Redirecting stderr and stdout
* Here documents (`<<EOF`)

---

### 📘 **Module 7: Advanced Topics**

**Objective**: Go beyond the basics.

* Arrays in bash
* String manipulation
* Arithmetic operations
* Trap and signals (`trap`, `SIGINT`, `SIGTERM`)
* Debugging (`set -x`, `set -e`, `trap ERR`)
* Scheduling scripts using `cron`

---

### 📘 **Module 8: Real-World Scripting Projects**

**Objective**: Apply your knowledge.

* Backup script
* Log rotation script
* System monitoring script
* Automated deployment script
* User management automation

---

### 📘 **Module 9: Tools & Best Practices**

**Objective**: Write clean, reusable scripts.

* Linting and formatting tools (`shellcheck`)
* Modular scripts
* Error handling and logging
* Creating configuration files
* Documentation and maintainability

---

### 🧠 **Optional: Dive Deeper**

* Bash job control (`&`, `fg`, `bg`, `jobs`)
* Subshells and command substitution
* Sourcing files (`source`, `.`)
* Secure scripting practices

---


---

## Optional: Dive Deeper

---

### 🔹 **1. Bash Job Control (`&`, `fg`, `bg`, `jobs`)**

Job control lets you manage background and foreground processes from your shell.

* `&` — Run a command **in the background**

  ```bash
  long_running_task &
  ```
* `jobs` — List all background jobs

  ```bash
  jobs
  ```
* `fg` — Bring a background job **to the foreground**

  ```bash
  fg %1
  ```
* `bg` — Resume a stopped job **in the background**

  ```bash
  bg %1
  ```
* Ctrl+Z — **Suspend** the current foreground job (stop it)

Use job control to run multiple processes in parallel or control tasks without closing the terminal.

---

### 🔹 **2. Subshells and Command Substitution**

* **Subshells**: Run commands in a **child shell** — changes don’t affect the current shell.

```bash
(cd /tmp && ls)    # Runs ls in /tmp without changing current directory
```

* **Command substitution**: Capture the output of a command into a variable.

```bash
current_date=$(date)
echo "Today is $current_date"
```

Or older style:

```bash
current_date=`date`
```

Use command substitution to embed command outputs inside scripts dynamically.

---

### 🔹 **3. Sourcing Files (`source`, `.`)**

Instead of running a script as a child process, you can **source** it to execute in the current shell environment.

```bash
source ./myvars.sh
# or
. ./myvars.sh
```

* Useful for loading environment variables, functions, or configuration into your current shell.
* Changes like variable exports persist after the sourcing.

---

### 🔹 **4. Secure Scripting Practices**

Make your scripts safer by:

* **Avoiding `eval`** unless absolutely necessary.
* **Quoting variables** to prevent word splitting and globbing:

  ```bash
  rm -rf "$directory"
  ```
* **Validating user input** before using it.
* Running scripts with **least privileges** — don’t run as root unless needed.
* Using **temporary files securely** (e.g., `mktemp`).
* Avoiding storing sensitive info (passwords) in plaintext.

---

### Summary

These deeper topics give you control over process management, safer scripting habits, and more flexible code structure.

---

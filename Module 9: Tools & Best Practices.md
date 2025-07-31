
---

## 📘 Module 9: Tools & Best Practices

**🎯 Objective: Write clean, reusable scripts**

---

### 🔹 **1. Linting and Formatting Tools (`shellcheck`)**

**`shellcheck`** is a static analysis tool for shell scripts. It helps you catch:

* Syntax errors
* Unsafe code patterns
* Bad practices
* Portability issues

#### ✅ Example Usage:

```bash
shellcheck myscript.sh
```

> Output will show line-by-line warnings and suggestions (like a linter for Python or JavaScript).

#### 🧰 Installation:

```bash
sudo apt install shellcheck    # Debian/Ubuntu
brew install shellcheck        # macOS
```

---

### 🔹 **2. Modular Scripts**

Split complex scripts into **modular parts** — like functions or separate files — so they can be reused or tested independently.

#### ✅ Strategy:

* Keep **utility functions** in a separate file (e.g., `utils.sh`)
* Use `source` to import:

```bash
source ./utils.sh
```

#### ✅ Example:

```bash
# utils.sh
log() {
  echo "[$(date +%F_%T)] $1"
}
```

```bash
# main.sh
source ./utils.sh
log "Script started"
```

> Improves **maintainability** and encourages **code reuse**.

---

### 🔹 **3. Error Handling and Logging**

Robust scripts handle errors gracefully and log key events.

#### ✅ Use `set -e`, `set -u`, and `trap`:

```bash
set -e    # Exit on any error
set -u    # Error on undefined variables

trap 'echo "Script failed at line $LINENO"; exit 1' ERR
```

#### ✅ Logging Example:

```bash
logfile="/var/log/myscript.log"

log() {
    echo "[$(date)] $1" | tee -a "$logfile"
}

log "Script started"
```

---

### 🔹 **4. Creating Configuration Files**

Avoid hardcoding settings — use **external config files** (e.g., `.conf` or `.env` style).

#### ✅ Example config.cfg:

```bash
SOURCE_DIR="/home/user/documents"
BACKUP_DIR="/mnt/backup"
```

#### ✅ Load config in your script:

```bash
source ./config.cfg
echo "Backing up from $SOURCE_DIR to $BACKUP_DIR"
```

> Makes scripts more **portable and flexible**.

---

### 🔹 **5. Documentation and Maintainability**

Write your scripts like someone else (or future you) will maintain them.

#### ✅ Header Block Example:

```bash
#!/bin/bash
# backup.sh - Backs up important files
# Author: Your Name
# Date: 2025-07-31
# Usage: ./backup.sh [optional_args]

set -e
```

#### ✅ Inline Comments:

```bash
# Create archive of project directory
tar -czf backup.tar.gz /home/user/project
```

#### ✅ Use `--help` options:

```bash
if [[ "$1" == "--help" ]]; then
    echo "Usage: ./myscript.sh [options]"
    exit 0
fi
```

---

### ✅ Summary

This module helps you write scripts that are:

* **Safe**: via linting and error handling
* **Reusable**: with modular and configurable design
* **Readable**: with comments and clear structure
* **Maintainable**: through documentation and separation of logic/config

---

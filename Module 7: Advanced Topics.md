
---

## 📘 Module 7: Advanced Topics

**🎯 Objective: Go beyond the basics**

---

### 🔹 **1. Arrays in Bash**

Bash supports **one-dimensional arrays**. You can store and access multiple values.

#### ✅ Defining an array:

```bash
fruits=("apple" "banana" "cherry")
```

#### ✅ Accessing elements:

```bash
echo ${fruits[0]}    # apple
echo ${fruits[2]}    # cherry
```

#### ✅ Looping through an array:

```bash
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done
```

#### ✅ Array length:

```bash
echo ${#fruits[@]}   # 3
```

---

### 🔹 **2. String Manipulation**

#### ✅ Basic operations:

```bash
str="hello world"

echo ${#str}             # Length: 11
echo ${str:0:5}          # Substring: hello
echo ${str/world/universe}  # Replace: hello universe
```

#### ✅ Remove patterns:

```bash
file="/home/user/file.txt"

echo ${file##*/}    # file.txt (basename)
echo ${file%/*}     # /home/user (dirname)
```

---

### 🔹 **3. Arithmetic Operations**

Use `(( ))` or `let` for arithmetic, or `expr` (older way).

#### ✅ Examples:

```bash
a=10
b=5

echo $((a + b))      # 15
((a++))              # Increment
let c=a*b            # 50
```

> All variables must be **integers**, and no `$` needed inside `(( ))`.

---

### 🔹 **4. Trap and Signals**

`trap` allows your script to **catch signals** (e.g., Ctrl+C) and run cleanup code before exiting.

#### ✅ Common signals:

| Signal    | Meaning                          |
| --------- | -------------------------------- |
| `SIGINT`  | Interrupt (Ctrl+C)               |
| `SIGTERM` | Termination request              |
| `EXIT`    | Run when script exits            |
| `ERR`     | Trigger on error (with `set -e`) |

#### ✅ Example: Cleanup on exit

```bash
cleanup() {
    echo "Cleaning up..."
    rm -f /tmp/tempfile
}
trap cleanup EXIT
```

#### ✅ Example: Handle Ctrl+C

```bash
trap 'echo "Interrupted!"; exit' SIGINT
```

---

### 🔹 **5. Debugging**

Use these tools to debug scripts more easily.

| Command    | What it does                           |
| ---------- | -------------------------------------- |
| `set -x`   | Print each command before executing it |
| `set -e`   | Exit immediately on any error          |
| `trap ERR` | Catch and handle any command failure   |

#### ✅ Example:

```bash
set -e
trap 'echo "An error occurred."' ERR

cp file1.txt backup/
echo "Done"
```

> This will exit on error and run the `ERR` trap if `cp` fails.

---

### 🔹 **6. Scheduling Scripts Using `cron`**

You can **automate your scripts** using `cron`, a time-based job scheduler.

#### ✅ Editing your crontab:

```bash
crontab -e
```

#### ✅ Example entry:

```cron
0 2 * * * /home/user/backup.sh
```

> Runs the script every day at **2:00 AM**

#### Cron timing format:

```
* * * * * <command>
│ │ │ │ │
│ │ │ │ └─── Day of week (0–7)
│ │ │ └───── Month (1–12)
│ │ └─────── Day of month (1–31)
│ └───────── Hour (0–23)
└─────────── Minute (0–59)
```

#### ✅ View scheduled jobs:

```bash
crontab -l
```

---

### ✅ Summary

After completing this module, you’ll be able to:

* Use arrays and manipulate strings
* Do math in scripts
* Handle interrupts and clean up safely with `trap`
* Debug scripts with `set -x`, `set -e`, and `trap ERR`
* Automate script execution using `cron`

---

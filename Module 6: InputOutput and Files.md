
---

## 📘 Module 6: Input/Output and Files

**🎯 Objective: Work with files and user input/output**

---

### 🔹 **1. Reading User Input**

Use the `read` command to get input from the user during script execution.

#### 🧪 Example:

```bash
read -p "Enter your name: " name
echo "Hello, $name!"
```

* `-p` lets you display a prompt.
* `-s` hides input (useful for passwords).
* `-t` sets a timeout.

#### Password Example:

```bash
read -sp "Enter password: " password
echo
```

---

### 🔹 **2. Reading and Writing Files**

#### ✅ Reading from a file (line-by-line):

```bash
while IFS= read -r line; do
    echo "Line: $line"
done < input.txt
```

* `IFS=` preserves leading/trailing whitespace.
* `-r` prevents backslash escapes.

#### ✅ Writing to a file:

```bash
echo "Hello" > file.txt      # Overwrites
echo "World" >> file.txt     # Appends
```

#### ✅ Reading file into a variable:

```bash
content=$(<file.txt)
echo "$content"
```

---

### 🔹 **3. File Testing Operators**

Bash provides several **test conditions** to check file properties:

| Test | Description            |
| ---- | ---------------------- |
| `-e` | File exists            |
| `-f` | Regular file (not dir) |
| `-d` | Directory              |
| `-r` | Readable               |
| `-w` | Writable               |
| `-x` | Executable             |

#### 🧪 Example:

```bash
file="notes.txt"
if [ -f "$file" ]; then
    echo "$file exists and is a regular file"
else
    echo "File not found"
fi
```

---

### 🔹 **4. Redirecting `stdout` and `stderr`**

You can control standard output (`stdout`) and standard error (`stderr`) streams:

| Symbol | Meaning                     |
| ------ | --------------------------- |
| `>`    | Redirect stdout (overwrite) |
| `>>`   | Redirect stdout (append)    |
| `2>`   | Redirect stderr             |
| `&>`   | Redirect stdout and stderr  |
| `2>&1` | Redirect stderr to stdout   |

#### Examples:

```bash
ls validfile.txt > output.txt
ls invalidfile.txt 2> error.txt
ls validfile.txt invalidfile.txt &> all_output.txt
```

---

### 🔹 **5. Here Documents (`<<EOF`)**

Used to **feed multiline input** into a command or a file.

#### 🧪 Example 1: Pass multiple lines to `cat`

```bash
cat <<EOF
This is a
multi-line
string.
EOF
```

#### 🧪 Example 2: Write to a file

```bash
cat <<EOF > greeting.txt
Hello, $USER
Welcome to the system!
EOF
```

> 🧠 You can use `<<-EOF` with tabs (indented content allowed).

---

### ✅ Summary

After this module, you should be able to:

* Prompt users for input and handle it
* Read from and write to files
* Check if files exist, are readable, writable, etc.
* Redirect output and errors to files
* Use Here Documents for multi-line input

---

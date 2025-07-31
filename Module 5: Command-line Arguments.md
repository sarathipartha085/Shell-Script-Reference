
---

## 📘 Module 5: Command-line Arguments

**🎯 Objective: Make scripts dynamic**

---

### 🔹 **1. Positional Parameters: `$0`, `$1`, `$2`, ...**

Bash automatically assigns special variables to the arguments passed to your script.

| Variable     | Meaning                                |
| ------------ | -------------------------------------- |
| `$0`         | The name of the script itself          |
| `$1` to `$9` | The first 9 arguments                  |
| `${10}`      | 10th argument (must use braces if ≥10) |

#### 🧪 Example:

```bash
# script.sh
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
```

Run it:

```bash
bash script.sh apple banana
```

> Output:

```
Script name: script.sh
First argument: apple
Second argument: banana
```

---

### 🔹 **2. Argument Count and All Arguments**

| Variable | Meaning                         |
| -------- | ------------------------------- |
| `$#`     | Number of arguments passed      |
| `$*`     | All arguments as a single word  |
| `$@`     | All arguments as separate words |

#### Example:

```bash
echo "You passed $# arguments"
echo "All args using *: $*"
echo "All args using @: $@"
```

---

### 🔹 **3. `shift` – Processing Arguments One at a Time**

The `shift` command **shifts** all arguments to the left by one. `$2` becomes `$1`, `$3` becomes `$2`, etc. This is useful when processing multiple arguments in a loop.

#### 🧪 Example:

```bash
while [ "$#" -gt 0 ]; do
    echo "Argument: $1"
    shift
done
```

Run:

```bash
bash script.sh one two three
```

> Output:

```
Argument: one
Argument: two
Argument: three
```

---

### 🔹 **4. `getopts` – Handling Flags and Options**

`getopts` is used for parsing **flags** like `-f`, `-v`, or `-u username`. It's more powerful and standard for professional scripts.

#### Syntax:

```bash
while getopts ":u:p:" opt; do
  case $opt in
    u) user=$OPTARG ;;
    p) pass=$OPTARG ;;
    \?) echo "Invalid option: -$OPTARG" ;;
  esac
done
```

#### Example Script:

```bash
#!/bin/bash

while getopts ":n:a:" opt; do
  case $opt in
    n) name="$OPTARG" ;;
    a) age="$OPTARG" ;;
    \?) echo "Invalid option: -$OPTARG" ;;
  esac
done

echo "Name: $name"
echo "Age: $age"
```

Run:

```bash
bash script.sh -n Alice -a 25
```

> Output:

```
Name: Alice
Age: 25
```

#### Notes:

* `:` after a letter means it **expects a value**
* `OPTARG` stores the value provided
* `OPTIND` stores the index of the next argument

---

### ✅ Summary

After this module, you should be able to:

* Use `$1`, `$2`, `$@`, `$#` to access arguments
* Use `shift` to iterate over arguments
* Use `getopts` to handle command-line flags like `-f`, `-n`, `-v`

---

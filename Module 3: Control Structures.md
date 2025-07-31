
---

## 📘 Module 3: Control Structures

**🎯 Objective: Learn how to add logic to your scripts**

---

### 🔹 **1. Conditional Statements**

#### ✅ `if`, `else`, `elif`

The syntax:

```bash
if [ condition ]; then
    # code if true
elif [ another_condition ]; then
    # code if another condition is true
else
    # code if none are true
fi
```

#### Example:

```bash
read -p "Enter a number: " num
if [ "$num" -gt 0 ]; then
    echo "Positive"
elif [ "$num" -lt 0 ]; then
    echo "Negative"
else
    echo "Zero"
fi
```

---

### 🔹 **2. test, \[ ], and \[\[ ]]**

These are used to evaluate conditions.

| Syntax       | Notes                                |
| ------------ | ------------------------------------ |
| `test expr`  | Legacy POSIX command                 |
| `[ expr ]`   | Common form, same as `test`          |
| `[[ expr ]]` | Bash-specific, more powerful & safer |

#### Comparison Operators:

| Type    | `[ ]` / `test`            | `[[ ]]`          |
| ------- | ------------------------- | ---------------- |
| Numbers | `-eq`, `-lt`, `-gt`, etc. | same             |
| Strings | `=`, `!=`, `-z`, `-n`     | same, plus regex |
| Files   | `-f`, `-d`, `-e`, `-r`    | same             |

#### Example:

```bash
if [ "$name" = "Alice" ]; then
    echo "Welcome, Alice"
fi
```

#### File test example:

```bash
if [ -f "myfile.txt" ]; then
    echo "File exists"
fi
```

---

### 🔹 **3. Case Statement: `case...esac`**

Useful for matching multiple patterns.

#### Syntax:

```bash
case "$var" in
    pattern1)
        # code
        ;;
    pattern2)
        # code
        ;;
    *)
        # default case
        ;;
esac
```

#### Example:

```bash
read -p "Enter a letter: " letter
case "$letter" in
    [a-z])
        echo "Lowercase letter"
        ;;
    [A-Z])
        echo "Uppercase letter"
        ;;
    *)
        echo "Not a letter"
        ;;
esac
```

---

### 🔹 **4. Loops**

#### 🔁 `for` loop

Iterates over items or a sequence.

```bash
for i in 1 2 3; do
    echo "Number: $i"
done
```

With a range:

```bash
for i in {1..5}; do
    echo "$i"
done
```

---

#### 🔁 `while` loop

Repeats while a condition is true.

```bash
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

---

#### 🔁 `until` loop

Repeats until a condition becomes true.

```bash
num=1
until [ $num -gt 5 ]; do
    echo "Number: $num"
    ((num++))
done
```

---

### 🔹 **5. Loop Control: `break` and `continue`**

* `break` → exit the loop immediately
* `continue` → skip current iteration

#### Example with `break`:

```bash
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        break
    fi
    echo "$i"
done
```

#### Example with `continue`:

```bash
for i in {1..5}; do
    if [ $i -eq 3 ]; then
        continue
    fi
    echo "$i"
done
```

---

### ✅ Summary

By the end of this module, you’ll be able to:

* Make decisions using `if`, `else`, and `case`
* Use test expressions safely with `[ ]` or `[[ ]]`
* Loop over items or ranges using `for`, `while`, `until`
* Control flow using `break` and `continue`

---

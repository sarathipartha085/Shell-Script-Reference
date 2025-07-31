
---

## 📘 Module 4: Functions and Scope

**🎯 Objective: Structure scripts using functions**

---

### 🔹 **1. Defining and Calling Functions**

Functions in Bash help organize code, promote reusability, and improve readability.

#### 🔧 Defining a Function (Two Styles):

```bash
# Style 1
my_function() {
    echo "Hello from a function"
}

# Style 2 (less common)
function my_function {
    echo "Hello from a function"
}
```

#### ✅ Calling a Function:

```bash
my_function
```

#### 🧪 Example:

```bash
greet() {
    echo "Hello, $1!"
}

greet "Alice"
```

> Output: `Hello, Alice!`

---

### 🔹 **2. Local and Global Variables**

In Bash:

* By default, variables are **global**, even inside functions.
* Use `local` to declare variables **local to a function**.

#### 🔍 Example:

```bash
name="Global"

say_name() {
    local name="Local"
    echo "Inside function: $name"
}

say_name
echo "Outside function: $name"
```

> Output:

```
Inside function: Local  
Outside function: Global
```

---

### 🔹 **3. Function Return Values**

* You can use the `return` keyword to return an **exit status** (0–255).
* For returning **data** (e.g., strings or numbers), use **echo** and command substitution.

#### ⚠️ `return` is **not** for returning strings, only numeric exit codes.

#### 🔁 Example 1: Returning Exit Status

```bash
check_even() {
    if (( $1 % 2 == 0 )); then
        return 0
    else
        return 1
    fi
}

check_even 4
if [ $? -eq 0 ]; then
    echo "Even number"
else
    echo "Odd number"
fi
```

---

#### 🔁 Example 2: Returning a Value via `echo`

```bash
get_name() {
    echo "Alice"
}

name=$(get_name)
echo "User is: $name"
```

---

### 🔹 **4. `$?` and Exit Status**

* `$?` holds the **exit status** of the **last command**.
* `0` means **success**, anything else means **failure**.

#### 🧪 Example:

```bash
ls /nonexistent
echo "Exit status: $?"   # likely 2

ls /
echo "Exit status: $?"   # 0
```

You can also set a script's exit status:

```bash
exit 1   # Script ends with exit code 1 (custom failure)
```

---

### ✅ Summary

After this module, you should be able to:

* Define and call functions in your scripts
* Use local and global variables correctly
* Return status codes and values from functions
* Understand and use `$?` for exit status checking

---

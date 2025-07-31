---

## 📘 Module 2: Getting Started with Bash Scripting

---

### 🔹 **1. Writing Your First Shell Script**

A **shell script** is simply a file containing a sequence of shell commands.

#### Example:

Create a file called `hello.sh`:

```bash
#!/bin/bash
echo "Hello, World!"
```

This script tells the shell to run `echo "Hello, World!"`.

---

### 🔹 **2. Script Permissions and Execution**

To run a script:

1. Make it **executable** using `chmod +x`:

   ```bash
   chmod +x hello.sh
   ```

2. Execute the script:

   ```bash
   ./hello.sh
   ```

> 🔍 Note: `./` means “in the current directory.” You can't run it just with `hello.sh` unless that directory is in your `PATH`.

---

### 🔹 **3. `#!/bin/bash` – Shebang Explained**

The first line of your script:

```bash
#!/bin/bash
```

This is called the **shebang** (or hashbang).

* It tells the OS **which interpreter** to use (in this case, `/bin/bash`).
* Without it, the script may run under the default shell (which might not be `bash`).

You can also use:

```bash
#!/usr/bin/env bash
```

This is more portable because it uses the environment to find `bash`.

---

### 🔹 **4. `echo`, `read`, `printf`**

These are used for output/input in scripts.

#### `echo` – Print to screen

```bash
echo "Hello, $USER!"
```

#### `read` – Take input from user

```bash
echo "Enter your name:"
read name
echo "Welcome, $name"
```

#### `printf` – More control over formatting (like in C)

```bash
printf "Name: %s\nAge: %d\n" "$name" 25
```

---

### 🔹 **5. Comments and Best Practices**

Use comments to explain what your script does:

```bash
#!/bin/bash
# This script prints a greeting
echo "Hello!"
```

**Best Practices:**

* Use comments to describe each section of your script
* Use meaningful variable names
* Stick to consistent indentation and formatting
* Start scripts with `#!/bin/bash`
* Handle errors (later modules will cover this)

---

### 🔹 **6. Using Variables and Constants**

Assign values to variables:

```bash
name="Alice"
age=25
```

Access variables using `$`:

```bash
echo "Name: $name"
```

There’s no `const` keyword in bash, but by convention:

* Use **readonly** for constants:

```bash
readonly PI=3.14
```

---

### 🔹 **7. Quotes in Shell Scripts**

Quotes affect how variables and special characters are interpreted.

| Type              | Meaning                          |
| ----------------- | -------------------------------- |
| `'single quotes'` | Literal – no variable expansion  |
| `"double quotes"` | Expand variables                 |
| `` `backticks` `` | Execute command (older style)    |
| `$(...)`          | Command substitution (preferred) |

#### Examples:

```bash
name="Bob"

echo 'Hello $name'   # Outputs: Hello $name
echo "Hello $name"   # Outputs: Hello Bob

echo "Today is $(date)"   # Recommended
echo "Today is `date`"    # Same as above, but older syntax
```

---

### ✅ Summary

After this module, you should be able to:

* Write and execute basic shell scripts
* Use `echo`, `read`, and `printf`
* Define and use variables
* Understand how quoting affects command behavior
* Write well-commented and formatted scripts

---

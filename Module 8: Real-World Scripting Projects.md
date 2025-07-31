
---

## 📘 Module 8: Real-World Scripting Projects

**🎯 Objective: Apply your knowledge**

---

### 🔹 **1. Backup Script**

**Purpose:** Back up important directories (like `/home`, `/etc`, or project folders) into compressed archives.

#### ✅ Key Concepts Used:

* Variables
* `tar`, `gzip`
* `date` for timestamping
* `cron` for scheduling

#### 🧪 Example:

```bash
#!/bin/bash
backup_src="/home/user"
backup_dest="/backups"
timestamp=$(date +%F-%H%M%S)
backup_file="$backup_dest/home_backup_$timestamp.tar.gz"

mkdir -p "$backup_dest"
tar -czf "$backup_file" "$backup_src"

echo "Backup completed: $backup_file"
```

> You can schedule it daily using `cron`.

---

### 🔹 **2. Log Rotation Script**

**Purpose:** Archive and rotate logs manually if `logrotate` is not used, keeping only recent logs.

#### ✅ Key Concepts Used:

* File checks (`-f`)
* Looping
* Archiving and deleting files

#### 🧪 Example:

```bash
#!/bin/bash
log_dir="/var/log/myapp"
archive_dir="/var/log/myapp/archive"
mkdir -p "$archive_dir"

for file in "$log_dir"/*.log; do
  if [ -f "$file" ]; then
    mv "$file" "$archive_dir/$(basename "$file").$(date +%F)"
    touch "$file"
  fi
done

# Delete logs older than 7 days
find "$archive_dir" -type f -mtime +7 -delete
```

---

### 🔹 **3. System Monitoring Script**

**Purpose:** Monitor CPU, memory, and disk usage and alert (e.g., via email or log file) if thresholds are crossed.

#### ✅ Key Concepts Used:

* `top`, `free`, `df`
* Conditional logic
* Logging

#### 🧪 Example:

```bash
#!/bin/bash
logfile="/var/log/sys_monitor.log"
threshold=80
usage=$(df / | tail -1 | awk '{print $5}' | tr -d '%')

if [ "$usage" -gt "$threshold" ]; then
    echo "$(date): Disk usage is above $threshold%: ${usage}%" >> "$logfile"
fi
```

> You can expand it to check memory and CPU too.

---

### 🔹 **4. Automated Deployment Script**

**Purpose:** Deploy a web app or project by pulling from Git, copying files, restarting services, etc.

#### ✅ Key Concepts Used:

* Git commands
* Service control (`systemctl`, `service`)
* File operations

#### 🧪 Example:

```bash
#!/bin/bash
repo_dir="/home/user/app"
deploy_dir="/var/www/html"

cd "$repo_dir" || exit 1
git pull origin main || exit 1

cp -r * "$deploy_dir"
systemctl restart apache2

echo "Deployment complete at $(date)"
```

> Add checks for service status, permissions, etc. for production readiness.

---

### 🔹 **5. User Management Automation**

**Purpose:** Create, delete, or list users in bulk using a script.

#### ✅ Key Concepts Used:

* Input reading or file parsing
* `useradd`, `usermod`, `userdel`
* Loops and error handling

#### 🧪 Example (add users from file):

```bash
#!/bin/bash
while IFS= read -r username; do
    if id "$username" &>/dev/null; then
        echo "User $username already exists"
    else
        useradd "$username"
        echo "User $username created"
    fi
done < users.txt
```

> `users.txt` could be a file with usernames listed line by line.

---

### ✅ Summary

After this module, you’ll be able to:

* Build real-world, useful shell scripts
* Apply all earlier concepts in combination
* Create maintainable, automated solutions
* Schedule and deploy scripts in production environments

---

# 🐧 Linux File Permissions Guide

> A simple and colorful guide to understand **Linux File Permissions**.

------------------------------------------------------------------------

## 🎯 What are Linux File Permissions?

Linux file permissions define **who can read, write, or execute a
file**.

They apply to three types of users:

  User Type           Description
  ------------------- -----------------------------------
  👤 **Owner (u)**    Person who created the file
  👥 **Group (g)**    Users belonging to the same group
  🌍 **Others (o)**   Everyone else on the system

Permissions can be viewed using:

``` bash
ls -l
```

Permissions can be modified using:

``` bash
chmod
chown
chgrp
```

------------------------------------------------------------------------

# 🔐 The 3 Permission Types

  Permission       Symbol   Meaning
  ---------------- -------- ----------------------------
  📖 **Read**      r        View file contents
  ✏️ **Write**     w        Modify or delete the file
  ⚙️ **Execute**   x        Run file as program/script

------------------------------------------------------------------------

# 📂 Permission Format

Example command:

``` bash
ls -l
```

Example output:

    -rwxr-xr--

### Breakdown

  Section   Meaning
  --------- --------------------
  `-`       File type
  `rwx`     Owner permissions
  `r-x`     Group permissions
  `r--`     Others permissions

📌 File Types:

  Symbol   Meaning
  -------- -----------
  `-`      File
  `d`      Directory

------------------------------------------------------------------------

# 🔢 Numeric Permission Method

Linux permissions can also be represented as numbers.

  Number   Permission
  -------- ------------
  4        Read
  2        Write
  1        Execute

### Example

``` bash
chmod 755 script.sh
```

Explanation:

  User     Value   Permission
  -------- ------- ------------
  Owner    7       rwx
  Group    5       r-x
  Others   5       r-x

------------------------------------------------------------------------

# ⭐ Common Permission Examples

  Number       Symbol      Usage
  ------------ ----------- -----------------------------------
  🔴 **777**   rwxrwxrwx   Dangerous -- everyone full access
  🟢 **755**   rwxr-xr-x   Scripts & executables
  🔵 **644**   rw-r--r--   Configuration files
  🟡 **600**   rw-------   Private files

------------------------------------------------------------------------

# 🛠 Important Commands

## Change Permissions

``` bash
chmod +x /scripts/backup.sh
```

## Change Owner

``` bash
sudo chown ubuntu:developers app.log
```

Change owner only:

``` bash
sudo chown newowner file.txt
```

Change owner and group:

``` bash
sudo chown newowner:newgroup file.txt
```

## Change Group

``` bash
sudo chgrp newgroup file.txt
```

------------------------------------------------------------------------

# 🚀 Quick Summary

✔ **Read (r)** → View file\
✔ **Write (w)** → Modify file\
✔ **Execute (x)** → Run file

✔ **Owner, Group, Others** control access

✔ Use **chmod, chown, chgrp** to manage permissions.

------------------------------------------------------------------------

⭐ Perfect for **Linux beginners, DevOps engineers, and CKA learners**



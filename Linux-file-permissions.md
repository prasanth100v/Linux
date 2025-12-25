# What is umask in Linux?
### umask (User File Creation Mask) is a setting that controls the default permissions of newly created files and directories.

## 📊 umask → Permission Mapping Table
| umask | File Permission   | Directory Permission | Use Case                    |
| ----- | ----------------- | -------------------- | --------------------------- |
| `000` | `666` (rw-rw-rw-) | `777` (rwxrwxrwx)    | Very open (not recommended) |
| `002` | `664` (rw-rw-r--) | `775` (rwxrwxr-x)    | Shared/team environment     |
| `007` | `660` (rw-rw----) | `770` (rwxrwx---)    | Private group access        |
| `022` | `644` (rw-r--r--) | `755` (rwxr-xr-x)    | **Default (RHEL 9.x)**      |
| `027` | `640` (rw-r-----) | `750` (rwxr-x---)    | Secure servers              |
| `033` | `644` (rw-r--r--) | `744` (rwxr--r--)    | Limited group write         |
| `077` | `600` (rw-------) | `700` (rwx------)    | Highly secure systems       |
| `222` | `444` (r--r--r--) | `555` (r-xr-xr-x)    | Read-only creation          |
| `666` | `000` (---------) | `111` (--x--x--x)    | Rare / testing only         |

## 🔧 Commands & Usage
| Command                 | Description                             |
| ----------------------- | --------------------------------------- |
| `umask`                 | Display current umask value             |
| `umask 022`             | Set umask temporarily (current session) |
| `umask -S`              | Show umask in symbolic format           |
| `umask u=rwx,g=rx,o=rx` | Set symbolic umask                      |
| `umask u=rwx,g=rx,o=rx` | Owner full, group & others read+execute   |
| `umask u=rwx,g=rw,o=`   | Owner full, group read/write, others none |
| `umask u=rw,g=r,o=`     | Files with restricted permissions         |

#### 🔸umask defines default permission removal for new files, while 🔸chmod changes permissions of existing files or directories.


# What is chmod?
chmod (change mode) is used to change permissions of files and directories.
### 👉 It works on existing files/directories.

## 🔹 Examples (Numeric)
| Command          | Result               |
| ---------------- | -------------------- |
| `chmod 644 file` | rw-r--r--            |
| `chmod 755 dir`  | rwxr-xr-x            |
| `chmod 600 file` | rw-------            |
| `chmod 777 file` | rwxrwxrwx (⚠️ risky) |

## 🔹 Examples (Symbolic)
| Command               | Meaning                 |
| --------------------- | ----------------------- |
| `chmod u+x file`      | Add execute to owner    |
| `chmod g-w file`      | Remove write from group |
| `chmod o=r file`      | Others read-only        |
| `chmod a+x script.sh` | Make executable for all |

# 🔹 How chmod Works on Directories
Permissions on directories control who can enter, list, create, or delete files.

## 📘 Directory Permission Meaning
On directories, execute (x) permission is required to access files inside the directory.

| Permission | Symbol | What it Allows                        |
| ---------- | ------ | ------------------------------------- |
| Read       | `r`    | List directory contents (`ls`)        |
| Write      | `w`    | Create, delete, rename files          |
| Execute    | `x`    | Enter directory (`cd`) & access files |


## 🔧 chmod Commands for Directories
```
chmod 755 mydir
chmod u=rwx,g=rx,o=rx mydir
```
🔁 Recursive Permission Change
```
chmod -R 755 mydir
```
| Option | Purpose                                       |
| ------ | --------------------------------------------- |
| `-R`   | Apply permissions to all subdirectories/files |








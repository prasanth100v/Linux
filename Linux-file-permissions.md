# What is umask in Linux?
#### umask (`User File Creation Mask`) is a setting that controls the default permissions of newly created `files` and `directories`.

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
| `umask 022`             | Set umask temporarily (`current session`) |
| `umask -S`              | Show umask in `symbolic format`           |
| `umask u=rwx,g=rx,o=rx` | Set `symbolic umask  `                    |
| `umask u=rwx,g=rx,o=rx` | Owner full, group & others read+execute   |
| `umask u=rwx,g=rw,o=`   | Owner full, group read/write, others none |
| `umask u=rw,g=r,o=`     | Files with restricted permissions         |

#### 🔸umask defines default permission removal for new files, while 🔸chmod changes permissions of existing files or directories.


# What is chmod?
 * chmod (change mode) is used to `change permissions` of files and directories.
 * 👉 It works on existing `files/directories`.

## 🔹 Examples (Numeric)
| Command          | Result               |
| ---------------- | -------------------- |
| `chmod 644 file` | rw-r--r--            |
| `chmod 755 dir`  | rwxr-xr-x            |
| `chmod 600 file` | rw-------            |
| `chmod 777 file` | rwxrwxrwx (⚠️` risky`) |

## 🔹 Examples (Symbolic)
| Command               | Meaning                 |
| --------------------- | ----------------------- |
| `chmod u+x file`      | Add execute to owner    |
| `chmod g-w file`      | Remove write from group |
| `chmod o=r file`      | Others read-only        |
| `chmod a+x script.sh` | Make executable for all |

# 🔹 How chmod Works on Directories
  Permissions on directories control who can `enter`, `list`, `create`, or `delete` files.

## 📘 Directory Permission Meaning
  On directories, execute (`x`) permission is required to access files inside the directory.

| Permission | Symbol | What it Allows                        |
| ---------- | ------ | ------------------------------------- |
| Read       | `r`    | List directory contents (`ls`)        |
| Write      | `w`    | Create, delete, rename files          |
| Execute    | `x`    | Enter directory (`cd`) & access files |


## 🔧 chmod Commands for Directories
```hcl
chmod 755 mydir
chmod u=rwx,g=rx,o=rx mydir
```
🔁 Recursive Permission Change
```hcl
chmod -R 755 mydir
```
| Option | Purpose                                       |
| ------ | --------------------------------------------- |
| `-R`   | Apply permissions to all subdirectories/files |

## Full permission for all
```hcl
chmod 777 devops.txt
chmod ugo+rwx devops.txt
```
⚠️ Security risk – avoid in production

## ➕ Add Permissions  ➖ Remove Permissions
```hcl
chmod u+x file.txt     # Add execute for user
chmod g+w file.txt     # Add write for group
chmod o-r file.txt     # Remove read from others
chmod u-w file.txt     # Remove write from user
```
🎯 Set Permissions Explicitly
```hcl
chmod u=rwx,g=rx,o=r file.txt
```

# 👑 chown Command (Change Owner)
### chown changes the owner and/or group of files and directories.
📌 ONLY root user can use chown

🔹 Basic Syntax
```hcl
chown root:devops devops.txt          # 🔸 Owner → root   Group → devops
chown -R root:root DevOps/
```
### 🔹 Recursive ownership change  👉 Changes ownership of `directory + all contents`

# 👥 chgrp Command (Change Group)
  Only root user can use chgrp
🔹 Syntax
```hcl
chgrp wheel devops.txt      ➡ Group changed to wheel
```

# 📄 file Command
Purpose: Check what type of file it is (text, binary, script, image, etc.)
🔹 Syntax
```hcl
file filename   👉 Example:  file demo.txt
```

# 🔀 diff Command
Purpose: Compare two files line by line and show differences.
## 🚀 DevOps Use Cases
| Command               | Purpose             |
| --------------------- | ------------------- |
| `diff a.txt b.txt`    | Compare files       |
| `diff -u a.txt b.txt` | Unified diff        |
| `diff -y a.txt b.txt` | Side-by-side view   |
| `diff -r dir1 dir2`   | Compare directories |
|  `diff -u old.conf new.conf` | Compare config files |  
|  `diff -y a.yaml b.yaml`     |Check YAML changes   |
| `diff -r prod/ stage/`      |Validate deployments | 

## 📣 echo Command
### Purpose: Print text or variables to output.  👉 echo hello java

---

## ⚡ File Permissions in Linux — Rapid Fire Q&A

| 🔢 Q#   | ❓ Question                                    | 💡 Answer                                                |
| ------- | --------------------------------------------- | ----------------------------------------------------------- |
| 🔹 Q1   | What are file permissions in Linux?           | 👉 Rules controlling access to `files and directories`.    |
| 🔹 Q2   | Three basic permissions?                      | 👉 Read (`r`) <br> Write (`w`) <br> Execute (`x`)          |
| 🔹 Q3   | Who can have permissions?                     | 👉 Owner (`user`) <br> Group <br> Others                     |
| 📖 Q4   | Meaning of read (r) permission?               | 👉 `View` file contents.                                     |
| ✏️ Q5   | Meaning of write (w) permission?              | 👉 `Modify` file contents.                                   |
| 🚀 Q6   | Meaning of execute (x) permission?            | 👉 `Run` file as `program/script`.                           |
| 🔍 Q7   | Command to view permissions?                  | 👉 `ls -l `                                                  |
| 🔍 Q8   | Example output?                               | 👉` -rwxr-xr-- `                                             |
| 🧠 Q9   | First character in ls -l output?              | 👉 File type.                                              |
| 🧠 Q10  | What does - mean?                             | 👉 Regular file.                                           |
| 🧠 Q11  | What does d mean?                             | 👉 `Directory`.                                              |
| 👤 Q12  | What is file owner?                           | 👉 User `who owns the file`.                                 |
| 👥 Q13  | What is group ownership?                      | 👉 Group associated with file.                             |
| ⚙️ Q14  | Command to change permissions?                | 👉 chmod                                                   |
| ⚙️ Q15  | Add execute permission?                       | 👉 `chmod +x file.sh `                                       |
| ⚙️ Q16  | Remove write permission?                      | 👉 `chmod -w file.txt    `                                   |
| 🔢 Q17  | Numeric values of permissions?                | 👉 Read = `4` <br> Write = `2` <br> Execute = `1 `         |
| 🔢 Q18  | Meaning of 777?                               | 👉 `rwx` for everyone.                                       |
| 🔢 Q19  | Meaning of 755?                               | 👉 Owner: `rwx`, Group/Others: `rx  `                      |
| 🔢 Q20  | Meaning of 644?                               | 👉 Owner: `rw`, Group/Others: `r`                              |
| 🔑 Q21  | Change file owner?                            | 👉 chown user file                                         |
| 🔑 Q22  | Change group ownership?                       | 👉 chgrp group file                                        |
| 📂 Q23  | Read permission on directory means?           | 👉 `List files`.                                             |
| 📂 Q24  | Write permission on directory means?          | 👉 `Create/delete files`.                                    |
| 📂 Q25  | Execute permission on directory means?        | 👉 `Enter/access directory`.                                 |
| 🛡️ Q26 | What is SUID?                                 | 👉 Execute file with owner privileges.                     |
| 🛡️ Q27 | Numeric value of SUID?                        | 👉 `4 `                                                      |
| 🛡️ Q28 | What is SGID?                                 | 👉 Execute with group privileges / shared group ownership. |
| 🛡️ Q29 | Numeric value of SGID?                        | 👉 `2   `                                                    |
| 🛡️ Q30 | What is Sticky Bit?                           | 👉 Only file owner can delete files in directory.          |
| 🛡️ Q31 | Common sticky bit example?                    | 👉 `/tmp   `                                                 |
| ⚡ Q32   | Set SUID?                                     | 👉 `chmod 4755 file  `                                       |
| ⚡ Q33   | Set SGID?                                     | 👉` chmod 2755 dir   `                                       |
| ⚡ Q34   | Set Sticky Bit?                               | 👉 `chmod 1777 dir  `                                        |
| 🔧 Q35  | What is umask?                                | 👉 Default permission mask for `new files/directories`.      |
| 🔧 Q36  | View current umask?                           | 👉 umask                                                   |
| 🔐 Q37  | Why avoid 777 permissions?                    | 👉 `Major security risk`.                                    |
| 🔐 Q38  | Best practice for scripts?                    | 👉 Least required permissions.                             |
| 🛠️ Q39 | Permission denied error?                      | 👉 Check: `Ownership`, `Permissions`, `SELinux `            |
| 🛠️ Q40 | Script not executing?                         | 👉 Missing `execute permission`.                             |
| 🎯 Q41  | User cannot edit file — what do you check?    | 👉 Owner, group, write permission.                         |
| 🎯 Q42  | Multiple users need shared access — solution? | 👉 Use `groups + SGID`.                                      |
| 🎯 Q43  | Why sticky bit used in /tmp?                  | 👉 Prevent users deleting others’ files.                   |
| 🚀 Q44  | Difference between symbolic & numeric mode?   | 👉 Symbolic → `chmod u+x file` <br> Numeric → `chmod 755 file` |
| 🚀 Q45  | Recursive permission change?                  | 👉 `chmod -R 755 dir   `                                     |

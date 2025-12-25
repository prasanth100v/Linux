# 🔐 passwd Command

### 1️⃣ Set password for a user (as root)
```
sudo passwd devuser
      You’ll be prompted:
New password:
Retype new password:
```
### 2️⃣ Change your own password
```
passwd
  Prompts:
Current password:
New password:
Retype new password:
```
### 3️⃣ Verify password status
```
sudo passwd -S devuser
```
### 5️⃣ Lock / Unlock a user password
```
sudo passwd -l devuser   # lock
sudo passwd -u devuser   # unlock
```
### 5️⃣ Allow / Disable password login via SSH
```
Edit SSH config:
sudo vi /etc/ssh/sshd_config
Set:
PasswordAuthentication yes   # allow
PasswordAuthentication no    # disable (recommended)
Restart SSH:
sudo systemctl restart sshd
```
Best practice:
```
✅ SSH keys → enabled
❌ Password login → disabled
```
# 📋 chage Command 🔐 Password Expiry with chage command in Linux
| Command                            | Purpose                               |
| ---------------------------------- | ------------------------------------- |
| `sudo chage -l devuser`            | Show password aging details           |
| `sudo chage -M 30 devuser`         | Expire password after 30 days         |
| `sudo chage -W 7 devuser`          | Warn user 7 days before expiry        |
| `sudo chage -m 1 devuser`          | Minimum days between password changes |
| `sudo chage -d 0 devuser`          | Force password change at next login   |
| `sudo chage -M -1 devuser`         | Disable password expiry               |
| `sudo chage -E 2025-12-31 devuser` | Set account expiry date               |
| `sudo passwd -S devuser`           | Check password status                 |
| `cat /etc/shadow`                  | View updated values                   |


# 🔍 What is lid in Linux?
lid stands for List IDs (identities). List all users List groups, It comes from the libuser package.

📌 Common lid commands
```
lid                # list all users
lid devuser        # show info about a user
lid -g devops      # list users in group devops
lid -n             # show only names
lid -G devuser     # show groups of a user
```
### If lid is not installed, install it :
```
sudo yum install libuser -y
```
# id vs groups
| Command           | Shows UID | Shows GID | Shows Groups | Best Use          |
| ----------------- | --------- | --------- | ------------ | ----------------- |
| `id prasanth`     | ✅         | ✅         | ✅            | Debug permissions |
| `groups prasanth` | ❌         | ❌         | ✅            | Quick group check |
```
id prasanth          # Shows UID, GID, and group membership
groups prasanth      # Lists all groups the user belongs to
```
## 📥 stdin vs stdout
```
    stdin   —  (Standard Input)
    stdout  —  (Standard Output)
```

# 🖥️ wc (Word Count)
### The wc command counts lines, words, bytes, and characters in a file.
```
wc file.txt       # Show line, word, and character count
wc -l file.txt    # Count number of lines
wc -w file.txt    # Count number of words
wc -c file.txt    # Count number of bytes/characters
```

# man command is used to display the manual pages of Linux commands
```
man command  👉  man ls 👉  Shows the full manual for the ls command.
```
# mkdir = make directory
  Used to create new directories (folders) in Linux.
| **Purpose**                  | **Command**                    | **Explanation**                          |
| ---------------------------- | ------------------------------ | ---------------------------------------- |
| Create a directory           | `mkdir mydir`                  | Creates `mydir`                          |
| Create multiple directories  | `mkdir dir1 dir2 dir3`         | Creates multiple folders                 |
| Create nested directories    | `mkdir -p /opt/app/logs`       | Creates parent directories automatically |
| Set permissions              | `mkdir -m 755 secure_dir`      | Sets permissions at creation             |
| Create directory with spaces | `mkdir "My Folder"`            | Handles spaces                           |
| Create hidden directory      | `mkdir .secret`                | Hidden folder                            |


# cd = change directory
| **Purpose**              | **Command**      | **Explanation**       |
| ------------------------ | ---------------- | --------------------- |
| Go to home directory     | `cd`             | Takes you to `$HOME`  |
| Go to specific directory | `cd /var/log`    | Absolute path         |
| Go to parent directory   | `cd ..`          | One level up          |
| Go up two levels         | `cd ../..`       | Two levels up         |
| Go to previous directory | `cd -`           | Toggle last directory |
| Go to root directory     | `cd /`           | Filesystem root       |
| Go to home using tilde   | `cd ~`           | Same as `cd`          |
| Go to user’s home        | `cd /home/user`  | Specific user         |
| Directory with spaces    | `cd "My Folder"` | Use quotes            |
| Change & list            | `cd /etc && ls`  | Chain commands        |

# rmdir = remove directory
| **Purpose**                     | **Command**                            | **Explanation**             |
| ------------------------------- | -------------------------------------- | --------------------------- |
| Remove empty directory          | `rmdir testdir`                        | Deletes empty folder        |
| Remove multiple directories     | `rmdir dir1 dir2`                      | Deletes multiple empty dirs |
| Remove nested empty directories | `rmdir -p a/b/c`                       | Removes child → parent      |
| Remove hidden directory         | `rmdir .secret`                        | Removes hidden empty dir    |

# rm = remove
### Used to delete files and directories in Linux.
| **Purpose**                    | **Command**                       | **Explanation**          |
| ------------------------------ | --------------------------------- | ------------------------ |
| Remove a file                  | `rm file.txt`                     | Deletes file             |
| Remove multiple files          | `rm f1.txt f2.txt`                | Deletes multiple files   ||
| Force delete                   | `rm -f file.txt`                  | No confirmation ⚠️       |
| Force recursive delete         | `rm -rf mydir`                    | ⚠️ Dangerous             |
| Delete hidden files            | `rm .file`                        | Deletes hidden file      |
| Deletes entire system          | `rm -rf /`                        | remove everything starting from root (/). ⚠️ VERY DANGEROUS |
| Deletes everything in current directory    | `rm -rf *` | ⚠️ Removes all files & folders in the present working directory  |
| System wipe         | `rm -rf /*`           | Deletes all top-level directories like /bin, /etc, /home, /var ⚠️ Dangerous  |

# touch command : Create empty files
| **Purpose**           | **Command**                      | **Explanation**             |
| --------------------- | -------------------------------- | --------------------------- |
| Create empty file     | `touch file.txt`                 | Creates file if not exists  |
| Create multiple files | `touch f1.txt f2.txt`            | Creates multiple files      |
| Create file with path | `touch /tmp/test.log`            | Creates file in directory   |
| Create hidden file    | `touch .env`                     | Hidden config file          |












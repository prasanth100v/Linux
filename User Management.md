## 🔎 Linux Commands to Search User Details
| Command                  | What it Shows              | Example                     | Use Case               |
| ------------------------ | -------------------------- | --------------------------- | ---------------------- |
| `id username`            | UID, GID, groups           | `id prasanth`               | Check user ID & groups |
| `whoami`                 | Current logged-in user     | `whoami`                    | Verify active user     |
| `who`                    | Logged-in users            | `who`                       | See active sessions    |
| `w`                      | Logged-in users + activity | `w`                         | Check user activity    |
| `users`                  | Logged-in usernames        | `users`                     | Quick user list        |
| `last`                   | Login history              | `last prasanth`             | Audit logins           |
| `lastlog`                | Last login of users        | `lastlog -u prasanth`       | Security checks        |
| `getent passwd username` | User account details       | `getent passwd prasanth`    | NSS-based lookup       |
| `cat /etc/passwd`        | All users                  | `cat /etc/passwd`           | Local users list       |
| `grep user /etc/passwd`  | Search specific user       | `grep prasanth /etc/passwd` | Quick lookup           |
| `groups username`        | User groups                | `groups prasanth`           | Permission check       |
| `finger username`        | User info (if enabled)     | `finger prasanth`           | User profile           |
| `chage -l username`      | Password expiry info       | `chage -l prasanth`         | Account aging          |
| `passwd -S username`     | Password status            | `passwd -S prasanth`        | Locked/unlocked        |


## ✅ switches to root
sudo = temporary admin power
```hcl
❌ sudo su     → root with user environment  ⚠️ Does NOT load root’s full login profile (Some root commands may not work)
✅ sudo su -   → root with root environment  ⚠️  Switches to root user
⭐ sudo -i     → Best option    ✔️ Recommended on modern systems
✅ sudo systemctl restart nginx  → Single command as root (safest)  ✔️ No root shell needed
```
## 🔐 Linux User Login & Switching Commands

| Command         | Purpose                          | Password Required | Environment Loaded | Notes                     |
| --------------- | -------------------------------- | ----------------- | ------------------ | ------------------------- |
| `su`            | Switch to root                   | **Root password** | Partial            | Root env NOT fully loaded |
| `su -`          | Switch to root (login shell)     | **Root password** | Full root env      | Same as root login        |
| `su username`   | Switch to another user           | Target user       | Partial            | Keeps current env         |
| `su - username` | Login as another user            | Target user       | Full user env      | Recommended               |
| `sudo command`  | Run single command as root       | Your password     | No shell           | Safest method             |
| `sudo -i`       | Login as root                    | Your password     | Full root env      | **Best practice**         |
| `sudo su`       | Switch to root                   | Your password     | Partial            | Not recommended           |
| `sudo su -`     | Login as root                    | Your password     | Full root env      | Works but extra step      |
| `exit`          | Logout current user              | ❌                 | —                  | Returns to previous user  |
| `logout`        | Logout login shell               | ❌                 | —                  | Works in TTY              |


# 🧾 User & Group Management
👤 User Management
| **Task**               | **Command**                             | **Notes**                                         |
| ---------------------- | --------------------------------------- | ------------------------------------------------- |
| Create a user          | `sudo useradd username`                 | Basic user, no home by default (varies by distro) |
| Create user with home  | `sudo useradd -m username`              | Creates `/home/username`                          |
| Create user with UID   | `sudo useradd -u 1050 username`         | Useful for LDAP/NFS                               |
| Set / change password  | `sudo passwd username`                  | Prompts securely                                  |
| Delete user only       | `sudo userdel username`                 | Keeps home directory                              |
| Delete user + home     | `sudo userdel -r username`              | Removes files                                     |
| Lock user account      | `sudo usermod -L username`              | Disable login                                     |
| Unlock user account    | `sudo usermod -U username`              | Enable login                                      |
| Change login name      | `sudo usermod -l newname oldname`       | Home not renamed automatically                    |
| Change home directory  | `sudo usermod -d /new/home -m username` | `-m` moves files                                  |
| Set account expiry     | `sudo usermod -e 2025-12-31 username`   | YYYY-MM-DD                                        |
| Show user info         | `id username`                           | UID, GID, groups                                  |

# 👥 Group Management
| **Task**               | **Command**                           | **Notes**                     |
| ---------------------- | ------------------------------------- | ----------------------------- |
| Create group           | `sudo groupadd groupname`             | Creates entry in `/etc/group` |
| Create group with GID  | `sudo groupadd -g 2000 groupname`     | Fixed GID                     |
| Delete group           | `sudo groupdel groupname`             | Must not be primary group     |
| Rename group           | `sudo groupmod -n newgroup oldgroup`  | GID unchanged                 |
| Change group GID       | `sudo groupmod -g 3000 groupname`     | Be careful with files         |
| Add user to group      | `sudo usermod -aG groupname username` | `-a` is IMPORTANT             |
| Remove user from group | `sudo gpasswd -d username groupname`  | Safe removal                  |
| List group members     | `getent group groupname`              | Reliable                      |
| List all groups        | `cut -d: -f1 /etc/group`              | Local groups                  |

# 📂 ls -l /home

| **Task**               | **Command**                           | **output**                     |
| ---------------------- | ------------------------------------- | ----------------------------- |
| Lists all user home directories  | `ls -l /home`   | drwx------  5 prasanth prasanth 4096 Jan 10  prasanth |
| All user accounts (system + normal users)  | `cat /etc/passwd`    | username:x:UID:GID:comment:home:shell |
| All groups on the system          | `cat /etc/group`     | groupname:x:GID:user1,user2     |
| Encrypted passwords (Root only)   | `cat /etc/shadow`  | username:encrypted_pw:last_change:min:max:warn:inactive:expire |


# 🔐 Ownership & Permissions (related but essential)
| **Task**                  | **Command**                    | **Notes**             |
| ------------------------- | ------------------------------ | --------------------- |
| Change file owner         | `sudo chown user file`         | User ownership        |
| Change group owner        | `sudo chown :group file`       | Group ownership       |
| Change both               | `sudo chown user:group file`   | Most common           |


## ⚡ User Management in Linux — Rapid Fire Q&A
| 🔢 Q#   | ❓ Question                                               | 💡 Answer                                               |
| ------- | -------------------------------------------------------- | --------------------------------------------------------- |
| 🔹 Q1   | What is a user in Linux?                                 | 👉 An account that can log in and use system resources. |
| 🔹 Q2   | What is the root user?                                   | 👉 `Superuser with full system access`.                   |
| 🔹 Q3   | Default UID of root user?                                | 👉 `0  `                                                  |
| 👤 Q4   | Command to create a user?                                | 👉 `useradd username `                                    |
| 👤 Q5   | Create user with home directory?                         | 👉 `useradd -m username `                                 |
| 👤 Q6   | Set password for user?                                   | 👉 passwd username                                      |
| 📄 Q7   | User details stored in which file?                       | 👉 `/etc/passwd `                                         |
| 📄 Q8   | Password hashes stored in?                               | 👉 `/etc/shadow   `                                       |
| 📄 Q9   | Group information stored in?                             | 👉 `/etc/group`                                           |
| 🔍 Q10  | Show current logged-in user?                             | 👉 whoami                                               |
| 🔍 Q11  | Show logged-in users?                                    | 👉 who                                                  |
| 🔍 Q12  | Check user ID (UID/GID)?                                 | 👉 `id username `                                         |
| 🔐 Q13  | Force password change on next login?                     | 👉` passwd -e username   `                                |
| 🔐 Q14  | Lock user account?                                       | 👉 `passwd -l username  `                                 |
| 🔐 Q15  | Unlock user account?                                     | 👉 `passwd -u username    `                               |
| ⚙️ Q16  | Change username?                                         | 👉 `usermod -l newname oldname   `                        |
| ⚙️ Q17  | Change user shell?                                       | 👉 `usermod -s /bin/bash username     `                   |
| ⚙️ Q18  | Add user to group?                                       | 👉` usermod -aG groupname username    `                   |
| 🗑️ Q19 | Delete user?                                             | 👉 `userdel username    `                                 |
| 🗑️ Q20 | Delete user with home directory?                         | 👉 `userdel -r username   `                               |
| 👥 Q21  | What is a group in Linux?                                | 👉 Collection of users for permission management.       |
| 👥 Q22  | Create group?                                            | 👉` groupadd developers    `                              |
| 👥 Q23  | Delete group?                                            | 👉 `groupdel developers  `                                |
| 🛡️ Q24 | What is sudo?                                            | 👉 Allows user to execute commands as root.             |
| 🛡️ Q25 | Sudo configuration file?                                 | 👉 `/etc/sudoers  `                                       |
| 🛡️ Q26 | Safest way to edit sudoers?                              | 👉 `visudo   `                                            |
| 💻 Q27  | What is a login shell?                                   | 👉 Command interpreter assigned to user.                |
| 💻 Q28  | List available shells?                                   | 👉 `cat /etc/shells `                                     |
| 🏠 Q29  | Default home directory path?                             | 👉 `/home/username    `                                   |
| 🏠 Q30  | User startup files examples?                             | 👉 .bashrc, .profile                                    |
| ⏰ Q31   | Set account expiry date?                                 | 👉 `chage -E 2026-12-31 username   `                      |
| ⏰ Q32   | View password aging info?                                | 👉 `chage -l username  `                                  |
| 🔄 Q33  | Switch user?                                             | 👉 `su - username     `                                   |
| 🔄 Q34  | Switch to root?                                          | 👉` sudo su -    `                                        |
| 🔑 Q35  | Change file owner?                                       | 👉 `chown user file  `                                    |
| 🔑 Q36  | Change group ownership?                                  | 👉 `chgrp group file    `                                 |
| 🛠️ Q37 | User cannot login?                                       | 👉 Check: `Password, Shell, Account lock, SSH config `    |
| 🛠️ Q38 | Permission denied issue?                                 | 👉 `Check ownership and permissions. `                    |
| 🔐 Q39  | Why disable root SSH login?                              | 👉 `Security best practice`.                              |
| 🔐 Q40  | Best practice for admin access?                          | 👉 `Use sudo` instead of `direct root login`.               |
| 🎯 Q41  | Developer needs temporary admin access — what do you do? | 👉 Add to `sudo group temporarily`.                       |
| 🎯 Q42  | User deleted accidentally — recovery possible?           | 👉 `Restore from backup`.                                 |
| 🎯 Q43  | Why use groups instead of individual permissions?        | 👉 Easier management.                                   |
| 🚀 Q44  | What is PAM?                                             | 👉 Pluggable Authentication Modules.                    |
| 🚀 Q45  | What is `/etc/skel`?                                     | 👉 Template files for new users.                        |
| 🚀 Q46  | What is `passwd`?                                       | 👉 The passwd command is used to manage user passwords and account access. |


### 🔐 passwd Command

1️⃣ Set password for a user (as root)
```
sudo passwd devuser
      You’ll be prompted:
New password:
Retype new password:
```
2️⃣ Change your own password
```
passwd
  Prompts:
Current password:
New password:
Retype new password:
```
3️⃣ Verify password status
```
sudo passwd -S devuser
```
5️⃣ Lock / Unlock a user password
```
sudo passwd -l devuser   # lock
sudo passwd -u devuser   # unlock
```
6️⃣ Allow / Disable password login via SSH
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
### 📋 chage Command 🔐 Password Expiry with chage command in Linux
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


### 🔍 What is lid in Linux?
lid stands for List IDs (identities). List all users List groups, It comes from the libuser package.

📌 Common lid commands
```
lid                # list all users
lid devuser        # show info about a user
lid -g devops      # list users in group devops
lid -n             # show only names
lid -G devuser     # show groups of a user
```
If lid is not installed, install it :
```
sudo yum install libuser -y
```
### id vs groups
| Command           | Shows UID | Shows GID | Shows Groups | Best Use          |
| ----------------- | --------- | --------- | ------------ | ----------------- |
| `id prasanth`     | ✅         | ✅         | ✅            | Debug permissions |
| `groups prasanth` | ❌         | ❌         | ✅            | Quick group check |
```
id prasanth          # Shows UID, GID, and group membership
groups prasanth      # Lists all groups the user belongs to
```
### 📥 stdin vs stdout
```
    stdin   —  (Standard Input)
    stdout  —  (Standard Output)
```





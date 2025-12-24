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

✅ SSH keys → enabled

❌ Password login → disabled










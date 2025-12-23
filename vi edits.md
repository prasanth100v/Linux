### Use vi for normal work. Use sudo vi only for system files.
vi edits a file with your normal user permissions.

sudo vi edits a file with root (administrator) permissions.
### 🔹 vi (Normal user)   Opens a file using your current user  :   Safer for everyday work  (Code, scripts, docs)
```
vi myfile.txt
If you try:    vi /etc/hosts   ➡️ You can open it, but saving will fail: E212: Can't open file for writing
```
### 🔹 sudo vi (Root access) : Opens the file as root  ➡️ Can edit and save system/critical files, Config files.
```
sudo vi /etc/hosts        ✔️ File opens and saves successfully
 Powerful ⚠️ — mistakes can break the system
```

### 📝 Example: Add a user to sudo
Using visudo: Never edit /etc/sudoers directly with vi. Always use visudo.
```
sudo visudo
```
Add at the bottom:
```
prasanth ALL=(ALL) ALL
```
Meaning:
```
prasanth → username
ALL → any host
(ALL) → any user
ALL → any command
```
🧠 Pro tip (even safer)

### Instead of editing /etc/sudoers directly, create a file:
```
sudo visudo -f /etc/sudoers.d/prasanth
```
This is:  ✔️Cleaner  ✔️Safer  ✔️Easier to manage





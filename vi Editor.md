# 📝 What is vi Editor?
vi (Visual Editor) is a powerful, lightweight, terminal-based text editor
### 🚀 Open a file  ➡️ If file doesn’t exist → it will be created.
```bash
vi filename.txt
vi /etc/nginx/nginx.conf
```
# vi Editor Modes (VERY IMPORTANT)
| Mode             | Purpose                             |
| ---------------- | ----------------------------------- |
| **Normal mode**  | Default mode, navigation & commands |
| **Insert mode**  | Editing text                        |
| **Command mode** | Save, quit, search, etc.            |

# 🧭 Navigation (Normal Mode)
| Key  | Action            |
| ---- | ----------------- |
| `h`  | left              |
| `l`  | right             |
| `j`  | down              |
| `k`  | up                |
| `0`  | start of line     |
| `gg` | first line        |
| `G`  | last line         |
| `:n` | go to line number |
| `dd`       | delete line              |
| `yy`       | copy line                |
| `p`        | paste                    |
| `u`        | undo                     |
| `Ctrl + r` | redo                     |
| `$`        | End of line              |
| `/word` | Search forward  |
| `?word` | Search backward |


# ✏️ Insert Mode (Editing)
| Command | Explanation                 |
| ------- | --------------------------- |
| `i`     | Insert before cursor        |
| `I`     | Insert at beginning of line |
| `a`     | Append after cursor         |
| `A`     | Append at end of line       |
| `o`     | New line below              |
| `O`     | New line above              |
| `ESC`   | Exit insert mode            |

# 💾 Save & Exit (Command Mode)
Press : in Normal mode
| Command       | Action              |
| ------------- | ------------------- |
| `:w`          | save                |
| `:q`          | quit                |
| `:wq`         | save & quit         |
| `:q!`         | quit without saving |
| `:%s/old/new/g`  | 🔁 Find & Replace ➡️ :%s/http/https/gc |
| `:set nu`    | show line numbers  |



### Use vi for normal work. Use sudo vi only for system files.
vi edits a file with your normal user permissions.

sudo vi edits a file with root (administrator) permissions.
### 🔹 vi (Normal user)   Opens a file using your current user  :   Safer for everyday work  (Code, scripts, docs)
```hcl
vi myfile.txt
If you try :    vi /etc/hosts   ➡️ You can open it, but saving will fail: E212: Can't open file for writing
```
### 🔹 sudo vi (Root access) : Opens the file as root  ➡️ Can edit and save system/critical files, Config files.
```hcl
sudo vi /etc/hosts        ✔️ File opens and saves successfully
                           Powerful ⚠️ — mistakes can break the system
```

### 📝 Example: Add a user to sudo
Using visudo: Never edit /etc/sudoers directly with vi. Always use visudo.
```bash
sudo visudo
```
Add at the bottom:
```hcl
prasanth ALL=(ALL) ALL
```
Meaning:
```hcl
prasanth → username
ALL → any host
(ALL) → any user
ALL → any command
```
🧠 Pro tip (even safer)

### Instead of editing /etc/sudoers directly, create a file:
```hcl
sudo visudo -f /etc/sudoers.d/prasanth
```
This is:  ✔️Cleaner  ✔️Safer  ✔️Easier to manage





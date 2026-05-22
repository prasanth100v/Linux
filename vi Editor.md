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


## ⚡ vi / vim Editor in Linux — Rapid Fire Q&A
| 🔢 Q#   | ❓ Question                                | 💡 Answer                                            |
| ------- | ----------------------------------------- | ---------------------------------------------------- |
| 🔹 Q1   | What is vi editor?                        | 👉 A command-line text editor in Linux/Unix.         |
| 🔹 Q2   | What is vim?                              | 👉 “Vi Improved” — enhanced version of vi.           |
| 🔹 Q3   | Open file in vi?                          | 👉 👉 vi filename                                   |
| 📂 Q5   | Open file at specific line?               | 👉 `vi +10 file.txt `                                  |
| 🧠 Q6   | Main modes in vi?                         | 👉 Command mode <br> Insert mode <br> Last-line mode |
| 🧠 Q7   | Default mode when vi opens?               | 👉 `Command mode `                                     |
| 🧠 Q8   | Enter insert mode?                        | 👉 Press `i    `                                       |
| 🧠 Q9   | Exit insert mode?                         | 👉 Press `Esc   `                                      |
| 💾 Q10  | Save file?                                | 👉 `:w  `                                              |
| 💾 Q11  | Quit vi?                                  | 👉` :q    `                                            |
| 💾 Q12  | Save and quit?                            | 👉 `:wq       `                                        |
| 💾 Q13  | Quit without saving?                      | 👉` :q!     `                                          |
| 🧭 Q14  | Move left/right/up/down?                  | 👉 `h, l, k, j   `                                     |
| 🧭 Q15  | Go to beginning of line?                  | 👉 `0   `                                              |
| 🧭 Q16  | Go to end of line?                        | 👉` $      `                                           |
| 🧭 Q17  | Go to specific line?                      | 👉` :25    `                                           |
| 🧭 Q18  | Go to last line?                          | 👉 `G `                                                |
| 🧭 Q19  | Go to first line?                         | 👉 `gg  `                                              |
| ✏️ Q20  | Delete character?                         | 👉 `x  `                                               |
| ✏️ Q21  | Delete line?                              | 👉 `dd  `                                              |
| ✏️ Q22  | Delete multiple lines?                    | 👉 `5dd    `                                           |
| ✏️ Q23  | Copy (yank) line?                         | 👉 `yy  `                                              |
| ✏️ Q24  | Paste copied text?                        | 👉 `p   `                                              |
| ✏️ Q25  | Undo last change?                         | 👉 `u `                                                |
| ✏️ Q26  | Redo change?                              | 👉 `Ctrl + r `                                         |
| 🔍 Q27  | Search text?                              | 👉 `/word `                                            |
| 🔍 Q28  | Search next occurrence?                   | 👉 `n  `                                               |
| 🔍 Q29  | Replace word globally?                    | 👉 `:%s/old/new/g    `                                 |
| 🚀 Q30  | Open new line below?                      | 👉 `o `                                                |
| 🚀 Q31  | Open new line above?                      | 👉 `O `                                                |
| 🚀 Q32  | Replace character?                        | 👉 `r  `                                               |
| 📄 Q33  | Show line numbers?                        | 👉 `:set number   `                                    |
| 📄 Q34  | Hide line numbers?                        | 👉` :set nonumber    `                                 |
| 🎯 Q35  | Enter visual mode?                        | 👉 `v   `                                              |
| 🎯 Q36  | Why visual mode?                          | 👉 Select text for `copy/delete.    `                  |
| 📚 Q37  | Open multiple files?                      | 👉` vim file1 file2`                                   |
| 📚 Q38  | Switch files?                             | 👉 `:n    `                                            |
| ⚙️ Q39  | vim config file?                          | 👉 `~/.vimrc   `                                       |
| ⚙️ Q40  | Common vim setting?                       | 👉 `syntax on    `                                     |
| 🛠️ Q41 | Stuck in insert mode?                     | 👉 Press `Esc   `                                      |
| 🛠️ Q42 | Cannot quit vi?                           | 👉 Use:` :q!   `                                       |
| 🎯 Q43  | Why vi preferred in servers?              | 👉 Lightweight and always available.                 |
| 🎯 Q44  | How to edit config quickly in production? | 👉 Use `vi/vim.   `                                    |
| 🎯 Q45  | Why learn vi despite GUI editors?         | 👉 Most servers are `CLI-only`.                        |
| ⚡ Q46   | Copy entire file?                         | 👉 `:%y  `                                             |
| ⚡ Q47   | Delete entire file content?               | 👉` :%d   `                                            |

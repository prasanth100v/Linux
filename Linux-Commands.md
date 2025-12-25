 ### Most Frequently Used Linux Commands (DevOps-Focused) 🔥
 ```
ls        # list files
ls -l     # detailed list
ls -a     # show hidden files
pwd       # current directory
cd dir    # change directory
mkdir dir # create directory
rm file   # delete file
rm -rf dir# force delete directory
cp src dst# copy
mv src dst# move / rename
```
### Process & System Monitoring
```
ps -ef
top
htop
uptime
free -m
df -h
du -sh dir
kill PID
kill -9 PID
```
### 🔍 tail -f (Follow logs in real time)
tail -f shows the last lines of a file
Perfect for:

application logs ➡️ Kubernetes logs ➡️ system troubleshooting

### Basic usage  
```
tail -f app.log                ➡️ Shows last 10 lines and keeps following
tail -n 50 -f app.log          ➡️ Show last 50 lines
tail -f app1.log app2.log      ➡️ Follow multiple files  
tail -f app.log | grep ERROR   ➡️ Watch errors only
kubectl logs -f pod-name       ➡️ Kubernetes pod logs
```
### find — find files/directories
 Find a file by name
 ```
find /var/log -name "*.log"
```
### 🔹 The command  (Shows system memory usage Refresh every 5 seconds)
```
free -hs 5
watch free -h         # alternative live view
```
### 🔹 Stop the command
   CTRL + C

### wget is a command-line tool in Linux used to download files from the internet (HTTP, HTTPS, FTP).
🔹 Most Common Uses
1️⃣ Download a file ➡️ Saves file.zip in the current directory
```
wget https://example.com/file.zip
```
2️⃣ Download & save with a custom name
```
wget -O myfile.zip https://example.com/file.zip
```
3️⃣ Download to a specific directory
```
wget -P /opt/downloads https://example.com/file.zip
```
### Install a package on RHEL / CentOS / Amazon Linux.

| Command                    | Purpose                |
| -------------------------- | ---------------------- |
| `sudo yum install nginx`   | Install nginx          |
| `sudo yum remove nginx`    | Uninstall nginx        |
| `sudo yum reinstall nginx` | Reinstall same package |
| `sudo yum update nginx`    | Update nginx only      |
| `sudo yum update`          | Update all packages    |




### ✅ switches to root
```
❌ sudo su     → root with user environment
✅ sudo su -   → root with root environment
⭐ sudo -i     → Best option    ✔️ Recommended on modern systems
✅ sudo systemctl restart nginx  → Single command as root (safest)  ✔️ No root shell needed
```
### 🧾 User & Group Management
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

👥 Group Management
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

📂 ls -l /home

| **Task**               | **Command**                           | **output**                     |
| ---------------------- | ------------------------------------- | ----------------------------- |
| Lists all user home directories  | `ls -l /home`   | drwx------  5 prasanth prasanth 4096 Jan 10  prasanth |
| All user accounts (system + normal users)  | `cat /etc/passwd`    | username:x:UID:GID:comment:home:shell |
| All groups on the system          | `cat /etc/group`     | groupname:x:GID:user1,user2     |
| Encrypted passwords (Root only)   | `cat /etc/shadow`  | username:encrypted_pw:last_change:min:max:warn:inactive:expire |


🔐 Ownership & Permissions (related but essential)
| **Task**                  | **Command**                    | **Notes**             |
| ------------------------- | ------------------------------ | --------------------- |
| Change file owner         | `sudo chown user file`         | User ownership        |
| Change group owner        | `sudo chown :group file`       | Group ownership       |
| Change both               | `sudo chown user:group file`   | Most common           |

### 🧾 ps (Process Status) – Commands Table
| **Task**                        | **Command**            | **What it Shows**       |
| ------------------------------- | ---------------------- | ----------------------- |
| Show processes of current shell | `ps`                   | Only current terminal   |
| Show all processes (BSD style)  | `ps aux`               | All users, full details |
| Show all processes (SysV style) | `ps -ef`               | All users with PPID     |
| Show tree format                | `ps -ef --forest`      | Parent-child hierarchy  |
| Show processes of a user        | `ps -u username`       | User-owned processes    |
| Search process by name          | `ps -ef \| grep nginx` | Find specific process   |
| Sort by CPU usage               | `ps aux --sort=-%cpu`  | High CPU first          |
| Sort by memory usage            | `ps aux --sort=-%mem`  | High memory first       |
| Watch live output               | `watch ps -ef`         | Refresh every 2 sec     |

### 🧾 kill – Commands Table
| **Task**                | **Command**         | **Signal / Behavior**  |
| ----------------------- | ------------------- | ---------------------- |
| Gracefully stop process | `kill PID`          | SIGTERM (15)           |
| Force kill process      | `kill -9 PID`       | SIGKILL (9)            |
| Reload process config   | `kill -HUP PID`     | SIGHUP                 |
| Pause process           | `kill -STOP PID`    | SIGSTOP                |
| Resume process          | `kill -CONT PID`    | SIGCONT                |
| Kill process by name    | `killall nginx`     | All matching processes |
| Kill user’s processes   | `pkill -u username` | User scope             |
| Kill by pattern         | `pkill -f demo.sh`  | Match command line     |

### 🆔 PID (Process ID)  Every process has one PID

PID is a unique number assigned by Linux to each running process.
The OS uses it to track, manage, and control processes.
🔍 How to find a PID
| Task                        | Command                |
| --------------------------- | ---------------------- |
| Show current shell PID      | `echo $$`              |
| List all processes with PID | `ps -ef`               |
| Find PID by process name    | `ps -ef \| grep nginx` |
| Find PID quickly            | `pgrep nginx`          |
| Interactive view            | `top` / `htop`         |

### 🧠 Special PIDs you should know
| PID  | Meaning                        |
| ---- | ------------------------------ |
| `1`  | Init / systemd (first process) |
| `$$` | Current shell PID              |
| `0`  | Kernel process (not killable)  |

### 🔑 Useful signal reference
| Signal  | Number | Meaning        |
| ------- | ------ | -------------- |
| SIGTERM | 15     | Graceful stop  |
| SIGKILL | 9      | Immediate stop |
| SIGHUP  | 1      | Reload config  |
| SIGSTOP | 19     | Pause          |
| SIGCONT | 18     | Continue       |

### 🔐 Permissions rule
```
You can kill your own processes
To kill other users’ processes, use:  sudo kill PID
```
### 📄 more and less command

Both are pagers: they display long text one screen at a time so your terminal doesn’t flood.
```
more → older, simpler      ✔️ less → newer, powerful (and ironically “more” 😄) command
```
```
Basic usage : less filename
less doesn’t load the full file → fast & memory-efficient
Use less instead of cat for big files
```
Powerful navigation keys
| Key           | Action                |
| ------------- | --------------------- |
| `Space` / `f` | Forward one page      |
| `b`           | Back one page         |
| `↑ ↓`         | Line by line          |
| `g`           | Go to start           |
| `G`           | Go to end             |
| `q`           | Quit                  |

### 🔄 nohup sh — what it means & how to use it

nohup sh starts a shell (sh) that ignores hangup signals, so anything you run inside it keeps running after you log out.
```
nohup sh demo.sh &
```
Redirect output (best practice)
```
  nohup sh demo.sh > demo.log 2>&1 &
```
🔹 Check status
```
ps -ef | grep demo.sh
echo $!                    #if you just started it
```
🔹 Stop the process
```
kill PID
kill -9 PID
```
### 🔑 Differences you should know
| Command                | Behavior                           |
| ---------------------- | ---------------------------------- |
| `nohup sh`             | Interactive shell immune to logout |
| `nohup sh script.sh &` | Run script safely in background    |
| `sh script.sh`         | Stops on logout                    |
| `./script.sh`          | Needs execute permission           |



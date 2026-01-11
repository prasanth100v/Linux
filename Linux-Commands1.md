# 🐧 Basic Essential Linux Commands
| Command    | Example                  | Explanation                                            |
| ---------- | ------------------------ | ------------------------------------------------------ |
| `pwd`      | `pwd`                    | Shows the **current working directory**                |
| `ls`       | `ls`                     | Lists files and directories                            |
| `ls -l`    | `ls -l`                  | Lists files with **details** (permissions, size, date) |
| `ls -a`    | `ls -a`                  | Shows **hidden files**                                 |
| `cd`       | `cd /home/user`          | Changes directory                                      |
| `cd ..`    | `cd ..`                  | Moves **one directory up**                             |
| `mkdir`    | `mkdir test`             | Creates a new directory                                |
| `rmdir`    | `rmdir test`             | Deletes an **empty directory**                         |
| `touch`    | `touch file.txt`         | Creates an empty file                                  |
| `cat`      | `cat file.txt`           | Displays file content                                  |
| `less`     | `less file.txt`          | Reads large files page by page                         |
| `head`     | `head file.txt`          | Shows first **10 lines**                               |
| `head -20` | `head -20 file.txt`      | Shows first 20 lines                                   |
| `tail`     | `tail file.txt`          | Shows last **10 lines**                                |
| `tail -f`  | `tail -f log.txt`        | Live log monitoring                                    |
| `cp`       | `cp a.txt b.txt`         | Copies file                                            |
| `cp -r`    | `cp -r dir1 dir2`        | Copies directory                                       |
| `mv`       | `mv a.txt /tmp/`         | Moves or renames file                                  |
| `rm`       | `rm file.txt`            | Deletes file                                           |
| `rm -r`    | `rm -r dir`              | Deletes directory recursively                          |
| `rm -rf`   | `rm -rf dir`             | **Force delete** (⚠ dangerous)                         |
| `clear`    | `clear`                  | Clears terminal screen                                 |
| `history`  | `history`                | Shows command history                                  |
| `man`      | `man ls`                 | Opens manual for a command                             |
| `which`    | `which python`           | Shows command path                                     |
| `whoami`   | `whoami`                 | Displays current user                                  |
| `uname -a` | `uname -a`               | System & kernel info                                   |
| `date`     | `date`                   | Shows current date & time                              |
| `df -h`    | `df -h`                  | Disk usage (human readable)                            |
| `free -h`  | `free -h`                | Memory usage                                           |
| `top`      | `top`                    | Real-time process monitoring                           |
| `ps`       | `ps -ef`                 | Shows running processes                                |
| `kill`     | `kill 1234`              | Stops a process                                        |
| `chmod`    | `chmod 755 file.sh`      | Changes file permissions                               |
| `chown`    | `chown user:file.txt`    | Changes file owner                                     |
| `grep`     | `grep "error" log.txt`   | Searches text                                          |
| `wc`       | `wc -l file.txt`         | Counts lines                                           |
| `echo`     | `echo "Hello"`           | Prints output                                          |
| `tar`      | `tar -cvf a.tar dir/`    | Archive files                                          |
| `zip`      | `zip a.zip file.txt`     | Compress files                                         |
| `unzip`    | `unzip a.zip`            | Extract zip                                            |
| `wget`     | `wget url`               | Download files                                         |
| `curl`     | `curl url`               | Fetch API/web data                                     |
| `ssh`      | `ssh user@ip`            | Remote server login                                    |

# ⚠️ Most Dangerous Commands (Must Know)
| Command     | Why Dangerous                        |                           |
| ----------- | ------------------------------------ | ------------------------- |
| `rm -rf /`  | Deletes entire system                |                           |
| `rm -rf *`  | Deletes everything in current folder |                           |
| `chmod 777` | Security risk                        |                           |
| `kill -9 `  | Can crash system                     |                           |


# w Command in Linux
### The w command shows who is logged in and what they are doing right now.
| Command      | Explanation                         |
| ------------ | ----------------------------------- |
| `w`          | Show all logged-in users            |
| `w username` | Show activity of a specific user    |
| `w -i`       | Show IP address instead of hostname |


## Shows system memory usage Refresh every 5 seconds
```
free -hs 5
watch free -h         # alternative live view
```
## 🔹 Stop the command
   CTRL + C

## wget is a command-line tool in Linux used to download files from the internet (HTTP, HTTPS, FTP).
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
## Install a package on RHEL / CentOS / Amazon Linux.

| Command                    | Purpose                |
| -------------------------- | ---------------------- |
| `sudo yum install nginx`   | Install nginx          |
| `sudo yum remove nginx`    | Uninstall nginx        |
| `sudo yum reinstall nginx` | Reinstall same package |
| `sudo yum update nginx`    | Update nginx only      |
| `sudo yum update`          | Update all packages    |


# 🧾 ps (Process Status) – Commands Table
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

# 🧾 kill – Commands Table
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

# 🆔 PID (Process ID)  Every process has one PID
### PID is a unique number assigned by Linux to each running process.
### The OS uses it to track, manage, and control processes.

## 🔍 How to find a PID
| Task                        | Command                |
| --------------------------- | ---------------------- |
| Show current shell PID      | `echo $$`              |
| List all processes with PID | `ps -ef`               |
| Find PID by process name    | `ps -ef \| grep nginx` |
| Find PID quickly            | `pgrep nginx`          |
| Interactive view            | `top` / `htop`         |

## 🧠 Special PIDs you should know
| PID  | Meaning                        |
| ---- | ------------------------------ |
| `1`  | Init / systemd (first process) |
| `$$` | Current shell PID              |
| `0`  | Kernel process (not killable)  |

## 🔑 Useful signal reference
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




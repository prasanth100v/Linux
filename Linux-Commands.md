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



### grep – alternative for simple filtering
grep is the BEST alternative for awk/sed when your goal is only simple filtering.
```
grep ERROR app.log       👉 Shows lines containing ERROR
```

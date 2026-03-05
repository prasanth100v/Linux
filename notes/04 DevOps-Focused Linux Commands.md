# 🚀 DevOps-Focused Linux Commands Guide

A practical quick-reference guide for **Linux commands commonly used by DevOps Engineers**.

---

# 📁 1. File & Directory Operations

| Command | Description |
|-------|-------------|
| `ls` | List files |
| `ls -l` | Detailed file listing |
| `ls -a` | Show hidden files |
| `pwd` | Show current directory |
| `cd` | Change directory |
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `rm` | Remove file |
| `rm -r` | Remove directory recursively |
| `cp` | Copy files |
| `mv` | Move or rename files |
| `touch` | Create empty file |
| `find` | Search files |
| `locate` | Search using indexed database |
| `top` | Real-time process monitoring |

---

# 📄 2. File Viewing & Editing

| Command | Description |
|-------|-------------|
| `cat` | View file contents |
| `head` | Show first lines of file |
| `tail -f` | Monitor logs in real time |
| `nano` | Simple text editor |
| `vim` | Advanced text editor |
| `vi` | Classic Unix text editor |
| `grep` | Search text in files |
| `egrep` | Extended regex search |
| `awk` | Pattern scanning and processing |
| `sed` | Stream editor for modifying text |

---

# 🔐 3. Permissions & Ownership

| Command | Description |
|-------|-------------|
| `chmod` | Change file permissions |
| `chown` | Change file owner |
| `chgrp` | Change file group |

---

# 👥 4. User & Group Management

| Command | Description |
|-------|-------------|
| `whoami` | Show current logged-in user |
| `id` | Display UID and GID information |
| `useradd` | Create a new user |
| `usermod` | Modify existing user |
| `userdel` | Delete a user |
| `groupadd` | Create new group |
| `groupdel` | Delete group |
| `passwd` | Change user password |

### Example Commands

| Command | Description |
|-------|-------------|
| `sudo useradd prasanth` | Create user |
| `sudo useradd -m prasanth` | Create user with home directory |
| `sudo useradd -m -G devops prasanth` | Add user to devops group |
| `sudo passwd alice` | Change password for alice |
| `sudo userdel alice` | Delete user alice |
| `sudo passwd prasanth` | Set password for prasanth |

---

# ⚡ 5. Process & Resource Monitoring

| Command | Description |
|-------|-------------|
| `ps aux` | List running processes |
| `top` | Real-time process monitor |
| `htop` | Interactive process viewer |
| `kill` | Terminate process |
| `df -h` | Disk usage |
| `du -sh` | Directory size |
| `free -m` | Memory usage (MB) |
| `free -h` | Memory usage (human readable) |
| `uptime` | System load |
| `vmstat` | System performance statistics |

---

# 🧠 Understanding sudo

| Command | Description |
|-------|-------------|
| `sudo` | Run commands with administrator privileges |

Example

| Command | Description |
|-------|-------------|
| `sudo apt update` | Update package list |

---

# 🔄 Understanding su

| Command | Description |
|-------|-------------|
| `su` | Switch to root user |
| `su devops` | Switch to devops user |
| `exit` | Return to previous user |

---

# 🌐 6. Networking Commands

| Command | Description |
|-------|-------------|
| `ping google.com` | Test network connectivity |
| `curl -I http://example.com` | Fetch HTTP headers |
| `wget URL` | Download files |
| `ifconfig` | Show network interfaces |
| `netstat -an` | Show active connections |
| `ss -tulnp` | Show listening ports |
| `nslookup google.com` | DNS lookup |
| `dig google.com` | Detailed DNS query |
| `ssh user@host` | Remote login |
| `telnet google.com 80` | Test host and port |

---

# 📦 7. Package Management

### Debian / Ubuntu

| Command | Description |
|-------|-------------|
| `apt update` | Update package index |
| `apt install nginx` | Install nginx |
| `sudo apt install docker` | Install Docker |

### RHEL / CentOS

| Command | Description |
|-------|-------------|
| `yum install nginx` | Install nginx |
| `sudo yum install docker` | Install Docker |

---

# 📜 8. Logs & System Information

| Command | Description |
|-------|-------------|
| `journalctl` | View system logs |
| `dmesg` | Kernel messages |
| `history` | Command history |
| `date` | Show current date and time |
| `lscpu` | CPU information |
| `alias` | Create command shortcuts |
| `crontab -e` | Schedule tasks |
| `shutdown -h now` | Shutdown system |
| `reboot` | Restart system |
| `openssl` | Generate SSL certificates |

---

# 🧰 Extra Useful Commands

| Command | Description |
|-------|-------------|
| `uname` | Show kernel name |
| `uname -r` | Show kernel version |
| `clear` | Clear terminal screen |
| `whoami` | Show logged-in user |
| `rm -rf myfolder` | Delete folder recursively |
| `rm -f file.txt` | Force delete file |
| `tar -xvf archive.tar` | Extract tar archive |
| `tar -cvf archive.tar file1 file2 folder1` | Create tar archive |
| `tar -tvf archive.tar` | List tar contents |
| `tar -tzvf archive.tar.gz` | List tar.gz contents |

⚠ **Warning:** `rm -rf` permanently deletes files.

---

# ⚙️ systemctl (Service Management)

| Command | Description |
|-------|-------------|
| `systemctl start nginx` | Start nginx service |
| `systemctl stop nginx` | Stop nginx service |
| `systemctl restart nginx` | Restart nginx service |
| `systemctl status nginx` | Check service status |
| `systemctl enable nginx` | Enable service at boot |
| `systemctl disable nginx` | Disable service at boot |

---

# 🏁 Conclusion

These Linux commands form the **core toolkit for DevOps Engineers** working with:

- Linux Servers  
- Kubernetes Nodes  
- Cloud Infrastructure  
- CI/CD Pipelines  

Mastering these commands improves **troubleshooting, automation, and system management skills**.

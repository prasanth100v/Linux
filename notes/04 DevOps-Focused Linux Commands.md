# 🚀 DevOps-Focused Linux Commands Guide

A practical quick-reference guide for **Linux commands commonly used by
DevOps Engineers**.

------------------------------------------------------------------------

# 📁 1. File & Directory Operations

  Command                  Description
  ------------------------ ------------------------------
  `ls`, `ls -l`, `ls -a`   List files
  `pwd`                    Show current directory
  `cd`                     Change directory
  `mkdir`                  Create directory
  `rmdir`                  Remove empty directory
  `rm`, `rm -r`            Remove files/folders
  `cp`                     Copy files
  `mv`                     Move or rename files
  `touch`                  Create empty file
  `find`                   Search files
  `locate`                 Search files using index
  `top`                    Real-time process monitoring

------------------------------------------------------------------------

# 📄 2. File Viewing & Editing

  Command               Description
  --------------------- ----------------------------------
  `cat`                 View file contents
  `head`                Show first lines of file
  `tail -f`             Monitor logs in real-time
  `nano`, `vim`, `vi`   Edit files
  `grep`, `egrep`       Search text inside files
  `awk`                 Pattern scanning and processing
  `sed`                 Stream editor for modifying text

------------------------------------------------------------------------

# 🔐 3. Permissions & Ownership

  Command   Description
  --------- -------------------------
  `chmod`   Change file permissions
  `chown`   Change file owner
  `chgrp`   Change file group

------------------------------------------------------------------------

# 👥 4. User & Group Management

  Command                           Description
  --------------------------------- -------------------------
  `whoami`                          Current logged-in user
  `id`                              UID and GID information
  `useradd`, `usermod`, `userdel`   Manage users
  `groupadd`, `groupdel`            Manage groups
  `passwd`                          Change password

### Example Commands

``` bash
sudo useradd prasanth
sudo useradd -m prasanth
sudo useradd -m -G devops prasanth
sudo passwd alice
sudo userdel alice
sudo passwd prasanth
```

------------------------------------------------------------------------

# ⚡ 5. Process & Resource Monitoring

  Command                Description
  ---------------------- -------------------------
  `ps aux`               List processes
  `top`, `htop`          Live process monitoring
  `kill`                 Kill processes
  `df -h`                Disk usage
  `du -sh`               Directory size
  `free -m`, `free -h`   Memory usage
  `uptime`               System load
  `vmstat`               Performance statistics

------------------------------------------------------------------------

# 🧠 Understanding sudo

**sudo = "Superuser Do"**

Allows normal users to run commands with **root privileges**.

### Example

``` bash
sudo apt update
```

💡 You will be asked for your password before execution.

------------------------------------------------------------------------

# 🔄 Understanding su

**su = Substitute User**

Switch to another user.

### Examples

``` bash
su
su devops
exit
```

------------------------------------------------------------------------

# 🌐 6. Networking Commands

  Command                        Description
  ------------------------------ -------------------------
  `ping google.com`              Test connectivity
  `curl -I http://example.com`   Fetch HTTP headers
  `wget URL`                     Download files
  `ifconfig`                     Show network interfaces
  `netstat -an`                  Show active connections
  `ss -tulnp`                    Show listening ports
  `nslookup google.com`          DNS lookup
  `dig google.com`               Detailed DNS query
  `ssh user@host`                Remote login
  `telnet google.com 80`         Test host & port

------------------------------------------------------------------------

# 📦 7. Package Management

### Debian / Ubuntu

``` bash
apt update
apt install nginx
sudo apt install docker
```

### RHEL / CentOS

``` bash
yum install nginx
sudo yum install docker
```

------------------------------------------------------------------------

# 📜 8. Logs & System Information

  Command             Description
  ------------------- ---------------------------
  `journalctl`        View system logs
  `dmesg`             Kernel logs
  `history`           Command history
  `date`              Show current date/time
  `lscpu`             CPU information
  `alias`             Create command shortcuts
  `crontab -e`        Schedule tasks
  `shutdown -h now`   Shutdown system
  `reboot`            Restart system
  `openssl`           Generate SSL certificates

------------------------------------------------------------------------

# 🧰 Extra Useful Commands

``` bash
uname
uname -r
clear
whoami
rm -rf myfolder
rm -f file.txt
tar -xvf archive.tar
tar -cvf archive.tar file1 file2 folder1
tar -tvf archive.tar
tar -tzvf archive.tar.gz
```

⚠ **Warning:** `rm -rf` is dangerous and deletes files permanently.

------------------------------------------------------------------------

# ⚙️ systemctl (Service Management)

`systemctl` is used to manage **systemd services**.

### Examples

``` bash
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl status nginx
systemctl enable nginx
systemctl disable nginx
```

------------------------------------------------------------------------

# 🏁 Conclusion

These Linux commands form the **core toolkit for DevOps Engineers**
working with:

-   Linux Servers
-   Kubernetes Nodes
-   Cloud Infrastructure
-   CI/CD Pipelines

Mastering these commands will significantly improve **system
troubleshooting and automation skills**.

# 🚀 DevOps-Focused Linux Commands (Quick Reference)

A **colorful DevOps Linux cheat sheet** covering commonly used commands
for system administration, troubleshooting, and automation.

------------------------------------------------------------------------

# 📁 File & Directory Operations

  Command                  Description
  ------------------------ -------------------------
  `ls`, `ls -l`, `ls -a`   List files
  `pwd`                    Show current directory
  `cd`                     Change directory
  `mkdir`                  Create directory
  `rmdir`                  Remove empty directory
  `rm`, `rm -r`            Remove files or folders
  `cp`                     Copy files
  `mv`                     Move or rename files
  `touch`                  Create empty file
  `find`                   Search files
  `locate`                 Search files via index
  `top`                    Real-time process view

------------------------------------------------------------------------

# 📄 File Viewing & Editing

  Command               Description
  --------------------- ----------------------------------
  `cat`                 View file contents
  `head`                Show first lines of file
  `tail -f`             Monitor logs in real time
  `nano`, `vim`, `vi`   Edit files
  `grep`, `egrep`       Search text inside files
  `awk`                 Pattern scanning and processing
  `sed`                 Stream editor for modifying text

------------------------------------------------------------------------

# 🔐 Permissions & Ownership

  Command   Description
  --------- -------------------------
  `chmod`   Change file permissions
  `chown`   Change file owner
  `chgrp`   Change file group

------------------------------------------------------------------------

# 👤 User & Group Management

  Command      Description
  ------------ -------------------------
  `whoami`     Current logged in user
  `id`         UID and GID information
  `useradd`    Create new user
  `usermod`    Modify user
  `userdel`    Delete user
  `groupadd`   Create group
  `groupdel`   Delete group
  `passwd`     Change password

### Examples

``` bash
sudo useradd prasanth
sudo useradd -m prasanth
sudo useradd -m -G devops prasanth
sudo passwd alice
sudo userdel alice
sudo passwd prasanth
```

------------------------------------------------------------------------

# ⚙️ Process & Resource Monitoring

  Command                Description
  ---------------------- ------------------------
  `ps aux`               List running processes
  `top`, `htop`          Monitor processes live
  `kill`                 Kill process
  `df -h`                Disk usage
  `du -sh`               Directory size
  `free -m`, `free -h`   Memory usage
  `uptime`               System load
  `vmstat`               Performance statistics

------------------------------------------------------------------------

# 🔑 sudo vs su

### sudo

`sudo` means **Superuser Do**.\
Allows normal users to execute commands with **root privileges**.

Example:

``` bash
sudo apt update
```

💡 Requires your password for security.

### su

`su` means **Substitute User**.

``` bash
su
su devops
exit
```

------------------------------------------------------------------------

# 🌐 Networking Commands

  Command                  Description
  ------------------------ -------------------------
  `ping google.com`        Test connectivity
  `curl -I URL`            Fetch HTTP headers
  `wget URL`               Download files
  `ifconfig`               Show network interfaces
  `netstat -an`            Active connections
  `ss -tulnp`              Open ports and services
  `nslookup google.com`    DNS lookup
  `dig google.com`         Detailed DNS query
  `ssh user@host`          Remote login
  `telnet google.com 80`   Test port connectivity

------------------------------------------------------------------------

# 📦 Package Management

  -----------------------------------------------------------------------
  OS                                  Commands
  ----------------------------------- -----------------------------------
  Debian / Ubuntu                     `apt update`, `apt install`,
                                      `sudo apt install docker`

  RHEL / CentOS                       `yum install`,
                                      `sudo yum install docker`
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 📜 Logs & System Information

  Command             Description
  ------------------- ---------------------------
  `journalctl`        View system logs
  `dmesg`             Kernel messages
  `history`           Command history
  `date`              Current date/time
  `uptime`            System uptime
  `lscpu`             CPU information
  `alias`             Create command shortcuts
  `crontab -e`        Schedule tasks
  `shutdown -h now`   Shutdown system
  `reboot`            Restart system
  `openssl`           Generate SSL certificates

------------------------------------------------------------------------

# 🧰 Extra Useful Commands

  Command                     Description
  --------------------------- -------------------------
  `uname`                     Show OS kernel
  `uname -r`                  Kernel version
  `clear`                     Clear terminal
  `whoami`                    Current user
  `rm -rf folder`             Force delete folder
  `rm -f file.txt`            Force delete file
  `tar -xvf file.tar`         Extract archive
  `tar -cvf file.tar files`   Create tar archive
  `tar -tvf file.tar`         List archive contents
  `tar -tzvf file.tar.gz`     List compressed archive

⚠ **Warning:** `rm -rf` permanently deletes files.

------------------------------------------------------------------------

# 🔧 systemctl (Service Management)

  Command                     Description
  --------------------------- ----------------------
  `systemctl start nginx`     Start service
  `systemctl stop nginx`      Stop service
  `systemctl restart nginx`   Restart service
  `systemctl status nginx`    Check service status
  `systemctl enable nginx`    Start on boot
  `systemctl disable nginx`   Disable startup

------------------------------------------------------------------------

# 🎯 Conclusion

These commands are **core tools for DevOps engineers** working with:

-   Linux Servers
-   Kubernetes nodes
-   Cloud infrastructure
-   CI/CD pipelines

Mastering them helps with **automation, troubleshooting, and system
reliability**.


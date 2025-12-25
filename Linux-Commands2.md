# cat command used to display the contents of a file,
| Command             | Purpose                  |
| ------------------- | ------------------------ |
| `cat devops.txt`    | Display file             |
| `cat file1 file2`   | Display two files        |
| `cat -n devops.txt` | Show line numbers        |
| `cat > file.txt`  | Create file            |
| `cat >> file.txt` | Append to file  (add on, usually to the end of file )  |
| `cat file1 file2 > combined.txt` | Merges file1 & file2   |



# 🫗 tee Command in Linux
 ### tee = see output + save output (at the same time)

## Common use cases (with examples)
```
1️⃣ View output and save it     You see the listing on screen   It’s also saved to output.txt   
          🔸 ls -l | tee output.txt

2️⃣ Append instead of overwrite   ➡️    -a → append mode
          🔸 date | tee -a log.txt

3️⃣ Save output to multiple files
          🔸 uname -a | tee file1.txt file2.txt

4️⃣ Capture output of a root command (very common)
          🔸 sudo dnf install nginx | tee install.log

⚠️ If the command needs sudo, tee may need it too:
          🔸 command | sudo tee /etc/config.conf  ➡️   echo "Hello" | sudo tee /etc/test.conf
```

# uniq Command in Linux —  uniq filters duplicate lines
```
1️⃣ Remove duplicate lines        ➡️   sort names.txt | uniq
3️⃣ Show only duplicate lines     ➡️  sort file.txt | uniq -d
```
# 📦 zcat — view compressed files
✅ One-line memory trick  🔸 zcat = cat  🔸 zgrep = grep 

Common examples
```
zcat app.log.gz
zcat app.log.gz | less          # safe for large logs
zcat app.log.gz | head
zcat app.log.gz | tail
```
# 🔍 zgrep — search inside compressed files
Common examples
```
zgrep ERROR app.log.gz
zgrep -i warning app.log.gz     # ignore case
zgrep -n ERROR app.log.gz       # show line numbers
zgrep -c ERROR app.log.gz       # count matches
zgrep "500" *.log.gz            # Search across many logs
```
# 🌐 ping Command (Network Check) (internet connectivity)
```
ping google.com
ping 8.8.8.8
ping -c 4 google.com     # send 4 packets
ping -i 2 8.8.8.8        # interval 2 sec
ping -s 1000 8.8.8.8     # packet size
```
# 📦 yum Command (Package Manager) 
### Installs, updates, removes software on RHEL / CentOS / Amazon Linux systems.
```
sudo yum install nginx
sudo yum remove nginx
sudo yum update
```
# 🖥️ System Information – Commands
| Task            | Command               |
| --------------- | --------------------- |
| OS details      | `cat /etc/os-release` |
| Kernel version  | `uname -r`            |
| Architecture    | `uname -m`            |
| Hostname        | `hostname`            |
| All system info | `uname -a`            |
| CPU details    | `lscpu`             |
| CPU info file  | `cat /proc/cpuinfo` |
| Live CPU usage | `top` / `htop`      |
| Memory usage         | `free -h`           |
| Detailed memory      | `cat /proc/meminfo` |
| Top memory processes | `top`               |
| Watch memory live    | `watch free -h`     | Refresh every 2 sec |
| Disk usage          | `df -h`        |
| Directory size      | `du -sh /path` |
| Block devices       | `lsblk`        |
| Mounted filesystems | `mount`        |
| Partition info      | `fdisk -l`     |
| IP addresses       | `ip a`                 |
| Routing table      | `ip r`                 |
| Connectivity test  | `ping google.com`      |
| System uptime     | `uptime` |
| Load average      | `uptime` |
| Logged-in users   | `who`    |
| Detailed sessions | `w`      |
| Hardware summary | `lshw`        |
| PCI devices      | `lspci`       |
| USB devices      | `lsusb`       |
| System clock     | `timedatectl` |
| Current user  | `whoami` |
| User sessions | `who`    |
| Login history | `last`   |

# 🔌 Shutdown / Reboot Commands
| Task                | Command               | Notes               |
| ------------------- | --------------------- | ------------------- |
| Shutdown now        | `sudo shutdown now`   | Immediate power off |
| Shutdown with delay | `sudo shutdown +5`    | After 5 minutes     |
| Shutdown at time    | `sudo shutdown 23:30` | Scheduled           |
| Cancel shutdown     | `sudo shutdown -c`    | Cancel scheduled    |
| Power off           | `sudo poweroff`       | Turns off machine   |
| Reboot now        | `sudo reboot`           | Immediate restart   |
| Reboot with delay | `sudo shutdown -r +5`   | Restart after 5 min |
| Fast reboot       | `sudo systemctl reboot` | systemd way         |

# 🔑 What is a UID?
### Every Linux user has a UID (integer number)
```
🔸 cat /etc/passwd:
🔸 username:x:UID:GID:comment:home_directory:shell
🔸 ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash   👉 Here, UID = 1000
```


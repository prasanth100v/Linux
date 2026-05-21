⚡ Linux — Rapid Fire Q&A
| 🔢 Q#   | ❓ Question                             | 💡 Answer                                                        |
| ------- | -------------------------------------- | ---------------------------------------------------------------- |
| 🔹 Q1   | What is Linux?                         | 👉 Open-source Unix-like operating system kernel.                |
| 🔹 Q2   | Who created Linux?                     | 👉 Linus Torvalds                                                |
| 🔹 Q3   | What is a Linux distribution (distro)? | 👉 OS built using Linux kernel + tools (Ubuntu, CentOS, Debian). |
| 🔹 Q4   | What is the kernel?                    | 👉 Core part of OS managing hardware and processes.              |
| 📁 Q5   | Root directory in Linux?               | 👉 /                                                             |
| 📁 Q6   | Home directory path?                   | 👉 /home                                                         |
| 📁 Q7   | Purpose of /etc?                       | 👉 Configuration files.                                          |
| 📁 Q8   | Purpose of /var?                       | 👉 Variable data (logs, spool files).                            |
| 📁 Q9   | Purpose of /tmp?                       | 👉 Temporary files.                                              |
| 💻 Q10  | Command to list files?                 | 👉 ls                                                            |
| 💻 Q11  | Show current directory?                | 👉 pwd                                                           |
| 💻 Q12  | Change directory?                      | 👉 cd                                                            |
| 💻 Q13  | Create file?                           | 👉 touch filename                                                |
| 💻 Q14  | Remove file?                           | 👉 rm file                                                       |
| 💻 Q15  | Copy file?                             | 👉 cp source dest                                                |
| 💻 Q16  | Move/rename file?                      | 👉 mv                                                            |
| 🔐 Q17  | Command to change permissions?         | 👉 chmod                                                         |
| 🔐 Q18  | Command to change ownership?           | 👉 chown                                                         |
| 🔐 Q19  | Permission values?                     | 👉 Read = 4 <br> Write = 2 <br> Execute = 1                      |
| 🔐 Q20  | Meaning of 755?                        | 👉 Owner: rwx, Group: rx, Others: rx                             |
| 👤 Q21  | Create user?                           | 👉 useradd                                                       |
| 👤 Q22  | Set password?                          | 👉 passwd                                                        |
| 👤 Q23  | Switch user?                           | 👉 su                                                            |
| 👤 Q24  | Run command as root?                   | 👉 sudo                                                          |
| ⚙️ Q25  | View running processes?                | 👉 ps -ef                                                        |
| ⚙️ Q26  | Real-time process monitoring?          | 👉 top                                                           |
| ⚙️ Q27  | Kill process?                          | 👉 kill PID                                                      |
| ⚙️ Q28  | Force kill?                            | 👉 kill -9 PID                                                   |
| 🔄 Q29  | Service manager in modern Linux?       | 👉 systemd                                                       |
| 🔄 Q30  | Start service?                         | 👉 systemctl start <service>                                     |
| 🔄 Q31  | Check service status?                  | 👉 systemctl status <service>                                    |
| 🔄 Q32  | Enable service at boot?                | 👉 systemctl enable <service>                                    |
| 🌐 Q33  | Check IP address?                      | 👉 ip addr                                                       |
| 🌐 Q34  | Test connectivity?                     | 👉 ping                                                          |
| 🌐 Q35  | DNS lookup command?                    | 👉 nslookup / dig                                                |
| 🌐 Q36  | Check open ports?                      | 👉 netstat -tulnp or ss -tulnp                                   |
| 💾 Q37  | Check disk usage?                      | 👉 df -h                                                         |
| 💾 Q38  | Check folder size?                     | 👉 du -sh                                                        |
| 💾 Q39  | Mount filesystem?                      | 👉 mount                                                         |
| 📜 Q40  | System logs location?                  | 👉 /var/log                                                      |
| 📜 Q41  | View logs live?                        | 👉 tail -f logfile                                               |
| 📜 Q42  | Systemd logs command?                  | 👉 journalctl                                                    |
| 📦 Q43  | Install package? (Ubuntu/Debian)       | 👉 apt install                                                   |
| 📦 Q44  | Update packages?                       | 👉 apt update && apt upgrade                                     |
| 📦 Q45  | Install package? (RHEL/CentOS)         | 👉 yum install / dnf install                                     |
| 🔑 Q46  | Remote login command?                  | 👉 ssh user@host                                                 |
| 🔑 Q47  | Secure copy file?                      | 👉 scp                                                           |
| 📦 Q48  | Create tar archive?                    | 👉 tar -cvf                                                      |
| 📦 Q49  | Extract tar archive?                   | 👉 tar -xvf                                                      |
| 📦 Q50  | Compress with gzip?                    | 👉 gzip                                                          |
| 📊 Q51  | Check memory usage?                    | 👉 free -h                                                       |
| 📊 Q52  | CPU info?                              | 👉 lscpu                                                         |
| 📊 Q53  | Disk I/O monitoring?                   | 👉 iostat                                                        |
| ⏰ Q54   | What is cron?                          | 👉 Job scheduler in Linux.                                       |
| ⏰ Q55   | Edit cron jobs?                        | 👉 crontab -e                                                    |
| 🛡️ Q56 | Firewall tool in Linux?                | 👉 iptables / firewalld                                          |
| 🛡️ Q57 | What is SELinux?                       | 👉 Security layer enforcing access control.                      |
| 🛠️ Q58 | Server slow — first checks?            | 👉 CPU, memory, disk, processes, logs.                           |
| 🛠️ Q59 | File deleted but disk not freed?       | 👉 Process may still hold file handle.                           |
| 🛠️ Q60 | SSH not working?                       | 👉 Check: SSH service, Firewall, Network, Credentials            |



⚡ Linux Troubleshooting — Rapid Fire Q&A
| 🔢 Q#   | ❓ Question                                      | 💡 Answer                                     |
| ------- | ----------------------------------------------- | --------------------------------------------- |
| 🔹 Q1   | First step in Linux troubleshooting?            | 👉 Understand the issue & check logs.         |
| 🔹 Q2   | Most important troubleshooting skill?           | 👉 Reading logs carefully.                    |
| 🔹 Q3   | Common areas to check?                          | 👉 CPU, memory, disk, network, services.      |
| 📊 Q4   | Check system uptime?                            | 👉 uptime                                     |
| 📊 Q5   | Check CPU usage?                                | 👉 top / htop                                 |
| 📊 Q6   | Check memory usage?                             | 👉 free -h                                    |
| 📊 Q7   | Check disk usage?                               | 👉 df -h                                      |
| 📊 Q8   | Check directory size?                           | 👉 du -sh *                                   |
| ⚙️ Q9   | View running processes?                         | 👉 ps -ef                                     |
| ⚙️ Q10  | Find high CPU process?                          | 👉 top                                        |
| ⚙️ Q11  | Kill stuck process?                             | 👉 kill -9 PID                                |
| ⚙️ Q12  | Find process by port?                           | 👉 lsof -i :PORT                              |
| 🔄 Q13  | Check service status?                           | 👉 systemctl status <service>                 |
| 🔄 Q14  | Restart service?                                | 👉 systemctl restart <service>                |
| 🔄 Q15  | View service logs?                              | 👉 journalctl -u <service>                    |
| 💾 Q16  | Disk full troubleshooting?                      | 👉 Check: Large logs, Old backups, Temp files |
| 💾 Q17  | Find large files?                               | 👉 find / -type f -size +1G                   |
| 💾 Q18  | Deleted file but space not freed?               | 👉 Process still holding file handle.         |
| 💾 Q19  | Command to identify open deleted files?         | 👉 lsof | grep deleted                        |
| 🧠 Q20  | Check swap usage?                               | 👉 swapon -s                                  |
| 🧠 Q21  | System slow due to memory?                      | 👉 High swap usage indicates memory pressure. |
| 🚀 Q22  | High load average means?                        | 👉 CPU/process overload.                      |
| 🚀 Q23  | Command to check CPU load?                      | 👉 uptime                                     |
| 🌐 Q24  | Check IP address?                               | 👉 ip addr                                    |
| 🌐 Q25  | Test connectivity?                              | 👉 ping                                       |
| 🌐 Q26  | Check DNS resolution?                           | 👉 nslookup / dig                             |
| 🌐 Q27  | Check listening ports?                          | 👉 ss -tulnp                                  |
| 🌐 Q28  | Trace network path?                             | 👉 traceroute                                 |
| 🔑 Q29  | SSH connection refused?                         | 👉 Check SSH service & firewall.              |
| 🔑 Q30  | SSH timeout issue?                              | 👉 Check network/security groups/firewall.    |
| 🔑 Q31  | Restart SSH service?                            | 👉 systemctl restart sshd                     |
| 📜 Q32  | System logs location?                           | 👉 /var/log                                   |
| 📜 Q33  | Live log monitoring?                            | 👉 tail -f /var/log/messages                  |
| 📜 Q34  | Authentication logs?                            | 👉 `/var/log/secure` or `/var/log/auth.log`   |
| 🖥️ Q35 | System stuck during boot?                       | 👉 Check `GRUB & system logs`.                 |
| 🖥️ Q36 | Boot logs command?                              | 👉 journalctl -b                               |
| 💽 Q37  | Filesystem corruption check?                    | 👉 fsck                                       |
| 💽 Q38  | Read-only filesystem issue?                     | 👉 Possible disk corruption/full disk.        |
| 📦 Q39  | Broken package dependencies?                    | 👉 Use: apt --fix-broken install              |
| 🔐 Q40  | Permission denied error?                        | 👉 Check ownership & permissions.             |
| 🔐 Q41  | View permissions?                               | 👉 ls -l                                      |
| 📈 Q42  | Tools for performance analysis?                 | 👉 top, vmstat, iostat, sar                   |
| 📈 Q43  | Check I/O bottleneck?                           | 👉 iostat                                     |
| ⏰ Q44   | Cron job not running?                           | 👉 Check: Cron service, Permissions, Logs     |
| ⏰ Q45   | Edit cron jobs?                                 | 👉 crontab -e                                 |
| 🛡️ Q46 | Firewall status check?                          | 👉 firewall-cmd --list-all                    |
| 🛡️ Q47 | SELinux status?                                 | 👉 getenforce                                 |
| 🎯 Q48  | Server suddenly slow — what do you check first? | 👉 CPU, memory, disk, load average.           |
| 🎯 Q49  | Application not reachable?                      | 👉 Check: Service, Port, Firewall, Logs       |
| 🎯 Q50  | High disk usage root cause?                     | 👉 Logs, backups, temp files.                 |



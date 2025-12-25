# 🔍 What is find?
find searches files & directories based on name, type, size, time, owner, permissions.

## 🔍 Linux find Command – DevOps Use-Cases Table
| #  | Use Case (DevOps)                  | Command                                                     | Explanation                              |
| -- | ---------------------------------- | ----------------------------------------------------------- | ---------------------------------------- |
| 1  | Find a file by name                | `find / -name app.log`                                      | Search file recursively (case-sensitive) |
| 2  | Case-insensitive search            | `find / -iname app.log`                                     | Finds `App.log`, `APP.LOG`, etc          |
| 3  | Find only files                    | `find /var/log -type f`                                     | `f` = file                               |
| 4  | Find only directories              | `find /opt -type d`                                         | `d` = directory                          |
| 5  | Find large files                   | `find / -type f -size +1G`                                  | Disk usage troubleshooting               |
| 6  | Find files modified in last 24 hrs | `find /app -type f -mtime -1`                               | Debug recent changes                     |
| 7  | Find files older than 30 days      | `find /data -type f -mtime +30`                             | Cleanup old data                         |
| 8  | Find files by permission           | `find / -type f -perm 777`                                  | Security audit                           |
| 9  | Find SUID files                    | `find / -type f -perm -4000`                                | Privilege escalation check               |
| 10 | Find files owned by user           | `find / -type f -user nginx`                                | Ownership issues                         |
| 11 | Find files by group                | `find / -type f -group docker`                              | Access control                           |
| 12 | Find YAML files                    | `find / -type f \( -name "*.yml" -o -name "*.yaml" \)`      | Kubernetes configs                       |
| 13 | Find empty files                   | `find /app -type f -empty`                                  | Cleanup useless files                    |













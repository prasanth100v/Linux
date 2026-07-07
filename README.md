## 🐧 Linux Glossary
| 🌟 **Term** 🌟               | 📘 **Explanation** 📘                                                               |
| ----------------------------- | ------------------------------------------------------------------------------------ |
| 🐧 **Linux**                 | An open-source operating system kernel used in servers, desktops, mobiles, and cloud |
| ⚙️ **Kernel**                | The core of Linux that manages CPU, memory, hardware, and processes                  |
| 💿 **Distribution (Distro)** | A complete Linux OS built using the Linux kernel (Ubuntu, CentOS, etc.)              |
| 💻 **Shell**                 | A command-line interface that allows users to interact with Linux                    |
| 🖥️ **Terminal**             | The application where you type Linux commands                                        |
| ⌨️ **Command**               | An instruction given to Linux to perform a task                                      |
| 👑 **Root**                  | The superuser with full system access                                                |
| 👤 **User**                  | A person or service account using the system                                         |
| 🏠 **Home Directory**        | Personal folder for a user (e.g., `/home/prasanth`)                                  |
| 📂 **File System**           | Structure that organizes files and directories in Linux                              |
| 🌍 **/ (Root Directory)**    | Top-level directory of the Linux file system                                         |
| 📦 **/bin**                  | Essential user command binaries (ls, cp, mv)                                         |
| 🛠️ **/sbin**                | System administration binaries                                                       |
| ⚙️ **/etc**                  | Configuration files                                                                  |
| 📝 **/var**                  | Variable data like logs and mail                                                     |
| 🗑️ **/tmp**                 | Temporary files                                                                      |
| 📚 **/usr**                  | User applications and utilities                                                      |
| 🔄 **Process**               | A running program                                                                    |
| 🆔 **PID**                   | Process ID (unique number for a process)                                             |
| 🤖 **Daemon**                | A background process (e.g., sshd)                                                    |
| 🚀 **Systemd**               | Service manager used in modern Linux                                                 |
| 📥 **Package**               | Software installed on Linux                                                          |
| 📦 **Package Manager**       | Tool to install/update software (yum, apt)                                           |
| 🔐 **Permission**            | Rules defining who can read/write/execute a file                                     |
| 👥 **Ownership**             | File owner and group information                                                     |
| 🔧 **chmod**                 | Command to change file permissions                                                   |
| 🛡️ **chown**                | Command to change file ownership                                                      |
| 🔗 **Symbolic Link**         | Shortcut to another file or directory                                                |
| ⛓️ **Hard Link**             | Another name for the same file                                                       |
| 💽 **Mount**                 | Attaching a filesystem to Linux                                                      |
| ❌ **Unmount**                | Detaching a filesystem                                                               |
| 🧩 **Disk Partition**        | Dividing a disk into sections                                                        |
| 💾 **Swap**                  | Disk space used as virtual RAM                                                       |
| 🌐 **Environment Variable**  | A variable that affects system behavior                                              |
| 🛤️ **PATH**                 | Variable that tells Linux where to find commands                                      |
| ⏰ **Cron**                   | Scheduler for automated tasks                                                       |
| 📅 **Crontab**               | File that defines cron jobs                                                          |
| 🔑 **SSH**                   | Secure remote login protocol                                                         |
| 🔥 **Firewall**              | Controls network traffic                                                             |
| 🌍 **IP Address**            | Unique network address                                                               |
| 🚪 **Port**                  | Communication endpoint (e.g., 22 for SSH)                                            |
| 📜 **Log File**              | File that records system events                                                      |
| ⏳ **Uptime**                 | How long the system has been running                                                 |
| 📊 **Load Average**          | System workload over time                                                            |
| 🚀 **Booting**               | Process of starting Linux                                                            |
| 🥾 **GRUB**                  | Bootloader that loads Linux                                                          |
| 🖥️ **Virtual Machine (VM)**  | A virtual computer running Linux                                                     |
| 📦 **Container**             | Lightweight isolated application environment                                         |
| 💥 **Kernel Panic**          | Critical system crash                                                                |


---

## 🐧 Linux Permission Commands — Interview Cheat Sheet

| 💻 **Command** | 📝 **Full Form**            | 🎯 **Purpose**                                                           | ⚙️ **Syntax**                                          | 💡 **Example**                                            | 🗣️ **Interview Explanation**                                                                                          |
| -------------- | --------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------ | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `umask`        | **User File Creation Mask** | Sets the **default permissions** for newly created files and directories | `umask <value>`                                        | `umask 022`                                               | *"It defines which permission bits are removed when new files and directories are created."*                           |
| `chmod`        | **Change Mode**             | Changes the **permissions** of a file or directory                       | `chmod <permissions> <file>`                           | `chmod 755 app.sh`                                        | *"It is used to grant or remove read, write, and execute permissions for the owner, group, and others."*               |
| `chown`        | **Change Owner**            | Changes the **owner** (and optionally the group) of a file or directory  | `chown <user> <file>`<br>`chown <user>:<group> <file>` | `chown ubuntu app.sh`<br>`chown ubuntu:developers app.sh` | *"It is used to transfer ownership of files or directories to another user, and optionally change the group as well."* |
| `chgrp`        | **Change Group**            | Changes only the **group ownership** of a file or directory              | `chgrp <group> <file>`                                 | `chgrp developers app.sh`                                 | *"It is used when only the group ownership of a file or directory needs to be changed."*                               |


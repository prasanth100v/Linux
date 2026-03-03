# ✅ The Linux File System

The Linux file system is how Linux organizes and stores data. It starts from the root directory `/` and uses a hierarchical structure where everything, including devices, is treated as a file.

It contains specific directories for programs, configuration files, user data, and system files. This structure keeps the system organized, makes it easy to manage permissions, and ensures that software and hardware can work together smoothly.

Think of it like an inverted tree:

```
/ (root)
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

## 1️⃣ / – Root Directory

* Starting point of the Linux file system.
* Every file and folder exists under `/`.

**Example:**

```bash
cd /
```

---

## 2️⃣ /bin – Essential User Commands

* Contains basic executable commands needed for system boot and repair.
* Examples: `ls`, `cp`, `mv`, `cat`, `bash`

```bash
ls /bin
```

---

## 3️⃣ /boot – Boot Files

* Contains files needed to boot Linux.
* Includes kernel and bootloader configs.
* Examples: `vmlinuz`, `initrd.img`, `grub/`

---

## 4️⃣ /dev – Device Files

* Hardware devices are treated as files.
* Examples:

  * `/dev/sda` → First hard disk
  * `/dev/tty` → Terminal devices

**Useful commands:**

```bash
lsblk
fdisk -l
```

---

## 5️⃣ /etc – Configuration Files

* Stores system-wide configuration files.
* Examples:

  * `/etc/passwd`
  * `/etc/shadow`
  * `/etc/ssh/sshd_config`

---

## 6️⃣ /home – User Home Directories

* Stores personal files for each user.
* Example:

  * `/home/prasanth`

SSH key example:

```
/home/prasanth/.ssh/id_rsa
```

---

## 7️⃣ /lib – Essential Libraries

* Contains shared libraries needed by `/bin` and `/sbin` programs.
* Linux: `.so` files
* Windows equivalent: `.dll`

Example:

```
/lib/x86_64-linux-gnu/libc.so.6
```

---

## 8️⃣ /media – Removable Media

* Auto-mount location for USB drives and external devices.

Example:

```
/media/username/MyUSB
```

---

## 9️⃣ /mnt – Temporary Mount Point

* Used for manual mounting.

```bash
sudo mount /dev/sdb1 /mnt
```

---

## 🔟 /opt – Optional Software

* Stores third-party software.
* Examples:

  * `/opt/google/chrome`
  * `/opt/vmware`

---

## 1️⃣1️⃣ /proc – Process Information

* Virtual filesystem with real-time system information.

```bash
cat /proc/cpuinfo
cat /proc/meminfo
```

---

## 1️⃣2️⃣ /root – Root User Home

* Home directory of the root user.
* Example:

  * `/root/.bashrc`
  * `/root/backup.sh`

---

## 1️⃣3️⃣ /run – Runtime Data

* Stores temporary runtime data.
* Cleared after reboot.

Example:

```
/run/systemd
/run/sshd.pid
```

---

## 1️⃣4️⃣ /sbin – System Administration Binaries

* Essential system commands.
* Examples:

  * `reboot`
  * `shutdown`
  * `iptables`

```bash
sudo /sbin/reboot
```

---

## 1️⃣5️⃣ /srv – Service Data

* Stores service-related data.
* Examples:

  * `/srv/www`
  * `/srv/ftp`

---

## 1️⃣6️⃣ /sys – Kernel & Hardware Info

* Real-time view of kernel and device data.

Examples:

```
/sys/class/net
/sys/block
/sys/devices
```

---

## 1️⃣7️⃣ /tmp – Temporary Files

* Stores temporary files.
* Usually cleared after reboot.

---

## 1️⃣8️⃣ /usr – User System Resources

* Stores user-level programs and documentation.

Subdirectories:

* `/usr/bin`
* `/usr/sbin`
* `/usr/share`

---

## 1️⃣9️⃣ /var – Variable Data

* Stores frequently changing data.

Examples:

* `/var/log/`
* `/var/lib/docker/`
* `/var/www/html/`

---

# 📌 Summary

* `/` is the root of everything.
* Linux treats everything as a file.
* Each directory has a specific purpose.
* Understanding the filesystem is essential for Linux administration and DevOps.

---

**End of Document**

# ✅ The Linux File System

The Linux file system is how Linux organizes and stores data. It starts
from the root directory `/` and uses a hierarchical structure where
everything, including devices, is treated as a file.

It contains specific directories for programs, configuration files, user
data, and system files. This structure keeps the system organized, makes
it easy to manage permissions, and ensures that software and hardware
can work together smoothly.

Think of it like an inverted tree:

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

------------------------------------------------------------------------

## 1. / -- Root Directory

-   Starting point of the Linux file system.

-   Every file and folder exists under `/`.

-   Example:

    ``` bash
    cd /
    ```

------------------------------------------------------------------------

## 2. /bin -- Essential User Commands

-   Basic executable commands required for system boot and repair.
-   Examples: `ls`, `cp`, `mv`, `cat`, `bash`

``` bash
ls /bin
```

------------------------------------------------------------------------

## 3. /boot -- Boot Files

-   Contains files needed to boot Linux.
-   Includes kernel and bootloader configs.
-   Examples:
    -   `vmlinuz`
    -   `initrd.img`
    -   `grub/`

------------------------------------------------------------------------

## 4. /dev -- Device Files

-   Hardware devices are treated as files.
-   Examples:
    -   `/dev/sda` → First hard disk
    -   `/dev/tty` → Terminal devices

Useful commands:

``` bash
lsblk
fdisk -l
```

------------------------------------------------------------------------

## 5. /etc -- Configuration Files

-   Stores editable text configuration files.
-   Examples:
    -   `/etc/passwd`
    -   `/etc/shadow`
    -   `/etc/ssh/sshd_config`

------------------------------------------------------------------------

## 6. /home -- User Home Directories

-   Stores personal files for regular users.

-   Example:

        /home/prasanth

------------------------------------------------------------------------

## 7. /lib -- Essential Libraries

-   Shared libraries required by programs in `/bin` and `/sbin`.
-   Linux uses `.so` (Shared Object) files.
-   Example:
    -   `/lib/x86_64-linux-gnu/libc.so.6`

------------------------------------------------------------------------

## 8. /media -- Removable Media

-   Auto-mount location for USB drives and CDs.

-   Example:

        /media/prasanth/MyUSB

------------------------------------------------------------------------

## 9. /mnt -- Temporary Mount Point

-   Used for manually mounting file systems.

-   Example:

    ``` bash
    sudo mount /dev/sdb1 /mnt
    ```

------------------------------------------------------------------------

## 10. /opt -- Optional Software

-   Third-party applications.
-   Examples:
    -   `/opt/google/chrome`
    -   `/opt/vmware`

------------------------------------------------------------------------

## 11. /proc -- Process & System Info

-   Virtual filesystem with real-time system information.

-   Examples:

    ``` bash
    cat /proc/cpuinfo
    cat /proc/meminfo
    ```

------------------------------------------------------------------------

## 12. /root -- Root User Home

-   Home directory of root (superuser).
-   Examples:
    -   `/root/.bashrc`
    -   `/root/backup.sh`

------------------------------------------------------------------------

## 13. /run -- Runtime Files

-   Temporary runtime data.
-   Cleared after reboot.
-   Example:
    -   `/run/systemd`
    -   `/run/sshd.pid`

------------------------------------------------------------------------

## 14. /sbin -- System Binaries

-   Essential system administration commands.
-   Examples:
    -   `ifconfig`
    -   `reboot`
    -   `shutdown`
    -   `iptables`
    -   `mount`

Example:

``` bash
sudo /sbin/reboot
```

------------------------------------------------------------------------

## 15. /srv -- Service Data

-   Stores data for services like web and FTP servers.
-   Examples:
    -   `/srv/www`
    -   `/srv/ftp`

------------------------------------------------------------------------

## 16. /sys -- Kernel & Hardware Info

-   Provides real-time kernel and device information.
-   Examples:
    -   `/sys/class/net`
    -   `/sys/block`
    -   `/sys/devices`

------------------------------------------------------------------------

## 17. /tmp -- Temporary Files

-   Stores temporary files.
-   Usually cleared after reboot.

------------------------------------------------------------------------

## 18. /usr -- User System Resources

-   Stores user-level programs, libraries, and documentation.
-   Common subdirectories:
    -   `/usr/bin`
    -   `/usr/sbin`
    -   `/usr/share/doc`

------------------------------------------------------------------------

## 19. /var -- Variable Data

-   Stores frequently changing data.
-   Examples:
    -   `/var/log/syslog`
    -   `/var/lib/docker`
    -   `/var/www/html`

Example: If Apache is running, logs are stored in:

    /var/log/apache2/

# What is umask in Linux?
### umask (User File Creation Mask) is a setting that controls the default permissions of newly created files and directories.

## 📊 umask → Permission Mapping Table
| umask | File Permission   | Directory Permission | Use Case                    |
| ----- | ----------------- | -------------------- | --------------------------- |
| `000` | `666` (rw-rw-rw-) | `777` (rwxrwxrwx)    | Very open (not recommended) |
| `002` | `664` (rw-rw-r--) | `775` (rwxrwxr-x)    | Shared/team environment     |
| `007` | `660` (rw-rw----) | `770` (rwxrwx---)    | Private group access        |
| `022` | `644` (rw-r--r--) | `755` (rwxr-xr-x)    | **Default (RHEL 9.x)**      |
| `027` | `640` (rw-r-----) | `750` (rwxr-x---)    | Secure servers              |
| `033` | `644` (rw-r--r--) | `744` (rwxr--r--)    | Limited group write         |
| `077` | `600` (rw-------) | `700` (rwx------)    | Highly secure systems       |
| `222` | `444` (r--r--r--) | `555` (r-xr-xr-x)    | Read-only creation          |
| `666` | `000` (---------) | `111` (--x--x--x)    | Rare / testing only         |

## 🔧 Commands & Usage
| Command                 | Description                             |
| ----------------------- | --------------------------------------- |
| `umask`                 | Display current umask value             |
| `umask 022`             | Set umask temporarily (current session) |
| `umask -S`              | Show umask in symbolic format           |
| `umask u=rwx,g=rx,o=rx` | Set symbolic umask                      |
| `umask u=rwx,g=rx,o=rx` | Owner full, group & others read+execute   |
| `umask u=rwx,g=rw,o=`   | Owner full, group read/write, others none |
| `umask u=rw,g=r,o=`     | Files with restricted permissions         |

#### 🔸umask defines default permission removal for new files, while 🔸chmod changes permissions of existing files or directories.







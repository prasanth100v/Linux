## 🔐 What is UFW in Linux?
It is a simple and user-friendly firewall tool used in Linux (especially Ubuntu) to control network traffic.
> 👉 Think of UFW = Security Group for Linux VM  (**Uncomplicated Firewall.*)

🔍 What can UFW do?
```
✔ Allow or block ports
✔ Allow traffic from specific IPs
✔ Allow specific services (ssh, http)
✔ Enable / disable firewall
```

## 🔐 UFW (Uncomplicated Firewall) Commands
### 🟢 Basic Firewall Control
| Command                   | Explanation                    | When to Use             |
| ------------------------- | ------------------------------ | ----------------------- |
| `sudo ufw status`         | Show current firewall status   | Check if firewall is ON |
| `sudo ufw status verbose` | Show detailed rules + defaults | Debug rules             |
| `sudo ufw enable`         | Enable firewall                | Start protection        |
| `sudo ufw disable`        | Disable firewall               | Temporary testing       |
| `sudo ufw reload`         | Reload rules without restart   | After rule changes      |
| `sudo ufw reset`          | Remove all rules               | Start fresh             |

## 🔓 Allow Rules
| Command               | Explanation           | Example Use    |
| --------------------- | --------------------- | -------------- |
| `sudo ufw allow ssh`  | Allow SSH (port 22)   | Remote login   |
| `sudo ufw allow 22`   | Allow port 22         | Custom SSH     |
| `sudo ufw allow 80`   | Allow HTTP            | Web server     |
| `sudo ufw allow 443`  | Allow HTTPS           | Secure website |
| `sudo ufw allow 8080` | Allow custom app port | Spring Boot    |
| `sudo ufw allow 6443` | Allow Kubernetes API  | K8s master     |

## 🔐 Allow From Specific IP (Security Best Practice)
| Command                                             | Explanation                  |
| --------------------------------------------------- | ---------------------------- |
| `sudo ufw allow from 192.168.1.10`                  | Allow all ports from one IP  |
| `sudo ufw allow from 192.168.1.10 to any port 22`   | Allow SSH from only your PC  |
| `sudo ufw allow from 10.0.0.0/24`                   | Allow entire subnet          |
| `sudo ufw allow from 192.168.1.10 to any port 3306` | Allow MySQL from specific IP |


## ❌ Deny / Block Rules
| Command                                 | Explanation       |
| --------------------------------------- | ----------------- |
| `sudo ufw deny 22`                      | Block SSH         |
| `sudo ufw deny 3306`                    | Block MySQL       |
| `sudo ufw deny from 192.168.1.100`      | Block specific IP |
| `sudo ufw deny from any to any port 23` | Block Telnet      |


## 🔄 Default Policies
| Command                           | Explanation                       |
| --------------------------------- | --------------------------------- |
| `sudo ufw default deny incoming`  | Block all incoming traffic        |
| `sudo ufw default allow outgoing` | Allow all outgoing traffic        |
| `sudo ufw default deny outgoing`  | Block all outgoing traffic (rare) |

## 🗑️ Delete Rules
| Command                    | Explanation             |
| -------------------------- | ----------------------- |
| `sudo ufw status numbered` | Show rules with numbers |
| `sudo ufw delete 2`        | Delete rule number 2    |
| `sudo ufw delete allow 22` | Delete specific rule    |

## ☸ Kubernetes / Docker Common Ports
| Service         | Port        | Command                          |
| --------------- | ----------- | -------------------------------- |
| Kubernetes API  | 6443        | `sudo ufw allow 6443`            |
| NodePort        | 30000–32767 | `sudo ufw allow 30000:32767/tcp` |
| Docker Registry | 5000        | `sudo ufw allow 5000`            |
| Spring Boot App | 8080        | `sudo ufw allow 8080`            |


# 🔓 Allow ALL Traffic in UFW
### ✅ Allow all incoming and outgoing traffic
```
sudo ufw default allow incoming
sudo ufw default allow outgoing
```
➡️ This removes all firewall restrictions.

✅ Better Alternative (Recommended) 🔐 Secure + practical (AWS-style security).
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443
```

# 🔐 What is firewalld?
firewalld is a dynamic firewall management tool for Linux.
## 🔥 UFW vs firewalld (Complete Comparison)
```
UFW = simple firewall for Ubuntu / Debian
firewalld = advanced, zone-based firewall for RHEL / Amazon Linux
```
## 🔥 firewalld – Important Commands
 🟢 Firewall Service Control
| Command                            | Explanation                                |
| ---------------------------------- | ------------------------------------------ |
| `sudo systemctl status firewalld`  | Check firewalld service status             |
| `sudo systemctl start firewalld`   | Start firewall service                     |
| `sudo systemctl stop firewalld`    | Stop firewall service (allows all traffic) |
| `sudo systemctl enable firewalld`  | Start firewall at boot                     |
| `sudo systemctl disable firewalld` | Disable firewall at boot                   |
| `sudo firewall-cmd --state`        | Check if firewall is running               |

## 🔓 Allow Traffic (Most Used)
| Command                                             | Explanation           |
| --------------------------------------------------- | --------------------- |
| `sudo firewall-cmd --add-service=ssh --permanent`   | Allow SSH             |
| `sudo firewall-cmd --add-service=http --permanent`  | Allow HTTP            |
| `sudo firewall-cmd --add-service=https --permanent` | Allow HTTPS           |
| `sudo firewall-cmd --add-port=8080/tcp --permanent` | Allow custom TCP port |
| `sudo firewall-cmd --add-port=53/udp --permanent`   | Allow UDP port        |
| `sudo firewall-cmd --reload`                        | Apply permanent rules |

## 🔁 Runtime vs Permanent Rules
| Command                                             | Explanation                       |
| --------------------------------------------------- | --------------------------------- |
| `sudo firewall-cmd --add-port=9090/tcp`             | Temporary rule (lost on reboot)   |
| `sudo firewall-cmd --add-port=9090/tcp --permanent` | Permanent rule                    |

## 🧨 Allow ALL Traffic (Dangerous) ⚠️ Never do this on public servers
| Command                                        | Explanation      |
| ---------------------------------------------- | ---------------- |
| `sudo firewall-cmd --set-default-zone=trusted` | Allow everything |
| `sudo systemctl stop firewalld`                | Disable firewall |

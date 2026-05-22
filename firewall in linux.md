## 🔐 What is UFW in Linux?
It is a simple and user-friendly firewall tool used in Linux (especially Ubuntu) to control network traffic.
> 👉 Think of UFW = Security Group for Linux VM  🔥 Uncomplicated Firewall.

🔍 What can UFW do?
```hcl
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
```hcl
sudo ufw default allow incoming
sudo ufw default allow outgoing
```
➡️ This removes all firewall restrictions.

✅ Better Alternative (Recommended) 🔐 Secure + practical (AWS-style security).
```hcl
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443
```

# 🔐 What is firewalld?
firewalld is a dynamic firewall management tool for Linux.
## 🔥 UFW vs firewalld (Complete Comparison)
```hcl
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

⚡ Linux Firewall — Rapid Fire Q&A
| 🔢 Q#   | ❓ Question                                  | 💡 Answer                                                                  |
| ------- | ------------------------------------------- | -------------------------------------------------------------------------- |
| 🔹 Q1   | What is a firewall in Linux?                | 👉 Security mechanism that controls incoming and outgoing network traffic. |
| 🔹 Q2   | Why is firewall important?                  | 👉 Protects system from unauthorized access.                               |
| 🔹 Q3   | Common firewall tools in Linux?             | 👉 iptables, firewalld, ufw                                                |
| 🔥 Q4   | What is iptables?                           | 👉 Command-line firewall utility in Linux.                                 |
| 🔥 Q5   | What are iptables tables?                   | 👉 filter, nat, mangle                                                     |
| 🔥 Q6   | Default table in iptables?                  | 👉 filter                                                                  |
| 🔥 Q7   | Main chains in filter table?                | 👉 INPUT, OUTPUT, FORWARD                                                  |
| 💻 Q8   | View iptables rules?                        | 👉 iptables -L                                                             |
| 💻 Q9   | Allow SSH port 22?                          | 👉 iptables -A INPUT -p tcp --dport 22 -j ACCEPT                           |
| 💻 Q10  | Block IP address?                           | 👉 iptables -A INPUT -s 192.168.1.10 -j DROP                               |
| 💻 Q11  | Delete rule?                                | 👉 iptables -D INPUT 1                                                     |
| 🛡️ Q12 | What is firewalld?                          | 👉 Dynamic firewall manager using zones.                                   |
| 🛡️ Q13 | Default firewall tool in RHEL/CentOS 7+?    | 👉 firewalld                                                               |
| 🛡️ Q14 | Main command for firewalld?                 | 👉 firewall-cmd                                                            |
| ⚙️ Q15  | Check firewall status?                      | 👉 systemctl status firewalld                                              |
| ⚙️ Q16  | Start firewalld?                            | 👉 systemctl start firewalld                                               |
| ⚙️ Q17  | Enable firewalld at boot?                   | 👉 systemctl enable firewalld                                              |
| 🌐 Q18  | Open port 80 permanently?                   | 👉 firewall-cmd --permanent --add-port=80/tcp                              |
| 🌐 Q19  | Reload firewall after changes?              | 👉 firewall-cmd --reload                                                   |
| 🌐 Q20  | List open ports?                            | 👉 firewall-cmd --list-ports                                               |
| 🔌 Q21  | Allow HTTP service?                         | 👉 firewall-cmd --permanent --add-service=http                             |
| 🔌 Q22  | Remove service?                             | 👉 firewall-cmd --permanent --remove-service=http                          |
| 🌍 Q23  | What is a zone in firewalld?                | 👉 Trust level for network connections.                                    |
| 🌍 Q24  | Default zone?                               | 👉 firewall-cmd --get-default-zone                                         |
| 🌍 Q25  | List all zones?                             | 👉 firewall-cmd --get-zones                                                |
| 🐧 Q26  | What is UFW?                                | 👉 Uncomplicated Firewall for Ubuntu.                                      |
| 🐧 Q27  | Enable UFW?                                 | 👉 ufw enable                                                              |
| 🐧 Q28  | Allow SSH in UFW?                           | 👉 ufw allow ssh                                                           |
| 🐧 Q29  | Check UFW status?                           | 👉 ufw status                                                              |
| 🌐 Q30  | Check listening ports?                      | 👉 ss -tulnp                                                               |
| 🌐 Q31  | Difference between TCP & UDP?               | 👉 TCP = connection-oriented, UDP = connectionless.                        |
| 🛠️ Q32 | Application not reachable?                  | 👉 Check: Firewall rules, Listening ports, Service status                  |
| 🛠️ Q33 | SSH blocked accidentally?                   | 👉 Access console and re-add SSH rule.                                     |
| 🛠️ Q34 | Changes not applied in firewalld?           | 👉 Reload firewall.                                                        |
| 🔐 Q35  | What is DROP rule?                          | 👉 Silently discard traffic.                                               |
| 🔐 Q36  | What is REJECT rule?                        | 👉 Reject traffic with response.                                           |
| 🔐 Q37  | What is ACCEPT rule?                        | 👉 Allow traffic.                                                          |
| 🚀 Q38  | What is NAT in firewall?                    | 👉 Network Address Translation.                                            |
| 🚀 Q39  | What is port forwarding?                    | 👉 Redirect traffic from one port to another.                              |
| 💾 Q40  | Are iptables rules persistent after reboot? | 👉 ❌ Not unless saved.                                                     |
| 💾 Q41  | Save iptables rules?                        | 👉 service iptables save                                                   |
| 🎯 Q42  | Website not accessible externally?          | 👉 Check: Firewall, Security Groups, Web service, Port listening           |
| 🎯 Q43  | Port open but app unreachable?              | 👉 Application may not be listening.                                       |
| 🎯 Q44  | Why use firewalld over iptables?            | 👉 Easier management & dynamic updates.                                    |
| ☸️ Q45  | Why firewall important in Kubernetes nodes? | 👉 Controls node-level traffic.                                            |
| ☸️ Q46  | Common Kubernetes ports?                    | 👉 6443 → API Server <br> 10250 → kubelet                                  |



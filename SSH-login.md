🔐 SSH Key-Based Login for devuser in EC2 — Complete Explanation

 * This setup allows a new Linux user (devuser) to log in to an EC2 instance securely using the same `.pem private key` already used by ec2-user.
 * Instead of `passwords`, `SSH` uses `public/private key authentication`.

### SSH key-based login for devuser
Copied SSH keys from `ec2-user to devuser` and correctly locked down ownership and permissions so SSH login works securely.

1️⃣ Create .ssh directory   🔹 SSH will not work without this configuration directory
```
sudo adduser devuser
sudo mkdir -p /home/devuser/.ssh                 #(-p avoids errors if it already exists)
```
2️⃣ Copy authorized keys   🔹 Copies SSH public keys from ec2-user
```
sudo cp /home/ec2-user/.ssh/authorized_keys /home/devuser/.ssh/    #Allows devuser to log in using the same private key
```
3️⃣ Fix ownership (VERY IMPORTANT)    🔹 Sets correct UID:GID ownership
```
sudo chown -R devuser:devuser /home/devuser/.ssh
```
4️⃣ Secure directory permissions        🔹 Only devuser can read/write/enter the directory
```
sudo chmod 700 /home/devuser/.ssh
```
5️⃣ Secure authorized_keys file       🔹 Only devuser can read/write the file
```
sudo chmod 600 /home/devuser/.ssh/authorized_keys
```
✅ Final Permission Check (Recommended)
```
ls -ld /home/devuser/.ssh
ls -l /home/devuser/.ssh/authorized_keys
```
Expected output:
```
🔸drwx------ devuser devuser .ssh
🔸-rw------- devuser devuser authorized_keys
```
### (EC2 Best Practice)
```
sudo adduser devuser
sudo mkdir -p /home/devuser/.ssh
sudo cp ~/.ssh/authorized_keys /home/devuser/.ssh/
sudo chown -R devuser:devuser /home/devuser/.ssh
sudo chmod 700 /home/devuser/.ssh
sudo chmod 600 /home/devuser/.ssh/authorized_keys
```
### ✅ How to Login as devuser
From your local machine
```
ssh -i your-key.pem devuser@<EC2_PUBLIC_IP>       📌 ssh -i mykey.pem devuser@54.210.xxx.xxx
```
* Local machine → sends authentication request EC2 SSH server (sshd) → checks authorized_keys If matching public key found → `login allowed`

🔁 If You Are Already Logged In as ec2-user  You don’t need SSH again:
```
sudo su - devuser
```
### 🛠 If Login Fails (Quick Checklist)
```
sudo systemctl status sshd
sudo systemctl restart sshd
```
### ✅ Login as devuser via MobaXterm
```
Open MobaXterm → Session → SSH
     🔸Remote host: EC2_PUBLIC_IP / DNS
     ✅ Check Specify username → enter devuser
Go to Advanced SSH settings
     ✅ Use private key
     🔸 Select the same .pem key used for ec2-user
Click OK → you’ll log in directly as devuser
```
✅ password is NOT required 👍 You’re using SSH key-based authentication, so no password prompt will appear.

### 🔐 Why no password?
```
🔸Because:
    Your public key is in /home/devuser/.ssh/authorized_keys
    Your private key (.pem) is configured in MobaXterm
           SSH matches the keys → login allowed
```
```
🔸/etc/ssh/sshd_config
     PubkeyAuthentication yes
     PasswordAuthentication no
🔸sudo systemctl restart sshd        #Restart if changed
```

/bin/bash = interactive shell that allows a user to log in and run commands.
🔍 Where /bin/bash appears
```
cat /etc/passwd:
devuser:x:1001:1001::/home/devuser:/bin/bash
    👉 If shell is /bin/bash → user can log in
    👉 If shell is /sbin/nologin or /bin/false → SSH login blocked
```

### 🔐 IAM-based access vs EC2 login — clear, real-world comparison
| Layer             | IAM-based access               | EC2 login                          |
| ----------------- | ------------------------------ | ---------------------------------- |
| What it controls  | **AWS resources**              | **Linux OS on EC2**                |
| Who authenticates | IAM User / Role                | Linux user (`ec2-user`, `devuser`) |
| How               | IAM policies + temporary creds | SSH key / password                 |
| Scope             | S3, EC2 API, RDS, EKS, etc.    | Files, processes, sudo             |
| Audit             | CloudTrail                     | OS logs                            |
| Best use          | Service-to-service access      | System administration              |

```    
 🔑 IAM-based access (AWS side)  ➡️ IAM controls what EC2 can do in AWS.
 🧑‍💻 EC2 login (OS side)          ➡️ EC2 login controls who can use the Linux machine.
```
🚫 Common misunderstanding (very important)
```
❌ “I have IAM access, so I can log in to EC2”  ➡️ Wrong
❌ “I can SSH into EC2, so I can access S3”     ➡️ Wrong
```
They are independent systems.

### ✅ EC2 login through SSM (Session Manager) over SSH
```
❌ No SSH keys  ❌ No open port 22
✅ IAM-based login to EC2 ✅ Reduced attack surface
```
### 🧑‍💻 How to connect 
```
🔹 AWS Console → EC2 → Connect → Session Manager → Click Connect
```

## 🔐 EC2 SSH & IAM — Rapid Fire Interview Q&A
| 🔢 Q#   | ❓ Question                                  | 💡 Answer                                                                                      |
| ------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| 👤 Q1   | Command to create a new Linux user?         | 👉 `useradd username` <br> or <br> `adduser username`                                            |
| 👤 Q2   | What does adduser devuser do?               | 👉 Creates a `Linux user`, `group`, `home directory`, and `login shell`.                         |
| 👤 Q3   | Where is user information stored?           | 👉 `/etc/passwd  `                                                                                 |
| 👤 Q4   | Which field defines the login shell?        | 👉 Last field in `/etc/passwd` <br><br> Example: <br> `devuser:x:1001:1001::/home/devuser:/bin/bash` |
| 👤 Q5   | What does `/bin/bash` mean?                 | 👉 Interactive `login shell. `                                                                     |
| 👤 Q6   | Which shell blocks login?                   | 👉 `/sbin/nologin` <br> `/bin/false`                                                                 |
| 🔐 Q7   | What is SSH?                                | 👉 `Secure Shell protocol` for remote login.                                                       |
| 🔐 Q8   | Default SSH port?                           | 👉 `22  `                                                                                          |
| 🔐 Q9   | Which service handles SSH connections?      | 👉 `sshd  `                                                                                        |
| 🔐 Q10  | Command to check SSH service status?        | 👉 `systemctl status sshd`                                                                         |
| 🔐 Q11  | Command to restart SSH service?             | 👉 `systemctl restart sshd `                                                                       |
| 🔑 Q12  | What file stores trusted public keys?       | 👉 `authorized_keys `                                                                              |
| 🔑 Q13  | Location of authorized_keys for devuser?    | 👉 `/home/devuser/.ssh/authorized_keys `                                                           |
| 🔑 Q14  | What is stored in `.pem file`?              | 👉 `Private SSH key`.                                                                              |
| 🔑 Q15  | What is stored in authorized_keys?          | 👉 `Public SSH key`.                                                                               |
| 🔑 Q16  | How does SSH key authentication work?       | 👉 SSH matches `private key with public key`.                                                      |
| 🔑 Q17  | Why is password not required?               | 👉 `SSH key-based authentication is used`.                                                         |
| 🔑 Q18  | Command to login using private key?         | 👉 `ssh -i mykey.pem devuser@IP`                                                                   |
| 🔑 Q19  | What does -i mean in SSH?                   | 👉 `Identity/private key file`.                                                                    |
| 🔑 Q20  | Why create .ssh directory?                  | 👉 `SSH expects authentication files there`.                                                       |
| 📁 Q21  | Required permission for .ssh directory?     | 👉 `700  `                                                                                         |
| 📁 Q22  | Meaning of 700 permission?                  | 👉 Owner → `rwx` <br> Group → --- <br> Others → ---                                                |
| 📁 Q23  | Required permission for authorized_keys?    | 👉 `600 `                                                                                          |
| 📁 Q24  | Meaning of 600 permission?                  | 👉 Owner → `rw`- <br> Group → --- <br> Others → ---                                                |
| 📁 Q25  | Why are SSH permissions important?          | 👉 `SSH refuses insecure permissions`.                                                             |
| 📁 Q26  | Command to change ownership?                | 👉 `chown `                                                                                        |
| 📁 Q27  | Command used to fix `SSH ownership`?        | 👉 `chown -R devuser:devuser /home/devuser/.ssh    `                                               |
| 📁 Q28  | Meaning of -R in chown?                     | 👉 Recursive.                                                                                    |
| 📁 Q29  | Command to change permissions?              | 👉 chmod                                                                                         |
| 📁 Q30  | Command to secure .ssh directory?           | 👉 `chmod 700 /home/devuser/.ssh `                                                                 |
| 📁 Q31  | Command to secure authorized_keys?          | 👉 `chmod 600 /home/devuser/.ssh/authorized_keys   `                                               |
| 📂 Q32  | What does mkdir -p do?                      | 👉 Creates directory and avoids error if exists.                                                 |
| 📂 Q33  | Command to create `.ssh directory`?         | 👉 `mkdir -p ~/.ssh    `                                                                           |
| 📂 Q34  | Command to copy authorized_keys?            | 👉 cp `~/.ssh/authorized_keys /home/devuser/.ssh/  `                                               |
| 📂 Q35  | Command to verify permissions?              | 👉 `ls -ld ~/.ssh` <br> `ls -l ~/.ssh/authorized_keys   `                                          |
| 🔄 Q36  | Command to switch user?                     | 👉 `su - username  `                                                                               |
| 🔄 Q37  | Command to switch to devuser?               | 👉 `sudo su - devuser  `                                                                           |
| 🔄 Q38  | Purpose of - in su -?                       | 👉 Loads full login environment.                                                                 |
| ⚙️ Q39  | SSH configuration file location?            | 👉 `/etc/ssh/sshd_config `                                                                         |
| ⚙️ Q40  | Setting to enable key authentication?       | 👉 PubkeyAuthentication `yes  `                                                                    |
| ⚙️ Q41  | Setting to disable password login?          | 👉 PasswordAuthentication `no  `                                                                   |
| ⚙️ Q42  | Why disable password authentication?        | 👉 Prevent `brute-force attacks`.  hacking method that uses `trial and error` to crack `passwords` and `login credentials` |
| ☁️ Q43  | What controls AWS resource permissions?     | 👉 `IAM`.                                                                                          |
| ☁️ Q44  | What controls Linux server login?           | 👉 `SSH/Linux users`.                                                                              |
| ☁️ Q45  | IAM stands for?                             | 👉 Identity and Access Management.                                                               |
| ☁️ Q46  | Can IAM login directly to Linux EC2?        | 👉 `No`.                                                                                           |
| ☁️ Q47  | Can SSH login automatically access S3?      | 👉 `No`.                                                                                           |
| ☁️ Q48  | What grants EC2 access to AWS services?     | 👉 `IAM Role`.                                                                                     |
| ☁️ Q49  | Which` logs` IAM activities?                | 👉 `AWS CloudTrail    `                                                                            |
| ☁️ Q50  | Which logs Linux login activity?            | 👉 Linux OS logs.                                                                                |
| 🔒 Q51  | What is Session Manager?                    | 👉 `Secure EC2 access through IAM without SSH`.                                                    |
| 🔒 Q52  | Which AWS service provides Session Manager? | 👉 AWS Systems Manager Session Manager                                                           |
| 🔒 Q53  | Does SSM require port 22?                   | 👉 No.                                                                                           |
| 🔒 Q54  | Does SSM require SSH keys?                  | 👉 No.                                                                                           |
| 🔒 Q55  | Main advantage of SSM?                      | 👉 `Reduced attack surface`.                                                                       |
| 🔒 Q56  | How does SSM authenticate users?            | 👉 `IAM authentication`.                                                                           |
| 🔒 Q57  | Where to connect using SSM?                 | 👉 `EC2 → Connect → Session Manager    `                                                           |
| 🛡️ Q58 | Best practice for EC2 login?                | 👉 Use SSH keys instead of passwords.                                                            |
| 🛡️ Q59 | Best practice for AWS permissions?          | 👉 Least privilege IAM policies.                                                                 |
| 🛡️ Q60 | More secure: SSH or SSM?                    | 👉 SSM.                                                                                          |
| 🛡️ Q61 | Why is SSM more secure?                     | 👉 No public SSH exposure.                                                                       |
| 🛡️ Q62 | Why rotate SSH keys periodically?           | 👉 Improve security.                                                                             |
| 🛡️ Q63 | Why avoid root login?                       | 👉 Security risk.                                                                                |


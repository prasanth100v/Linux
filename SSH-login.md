### SSH key-based login for devuser
Copied SSH keys from ec2-user to devuser and correctly locked down ownership and permissions so SSH login works securely.

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








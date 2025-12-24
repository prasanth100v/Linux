### SSH key-based login for devuser
Copied SSH keys from ec2-user to devuser and correctly locked down ownership and permissions so SSH login works securely.
1️⃣ Create .ssh directory   🔹 SSH will not work without this configuration directory
```
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
drwx------ devuser devuser .ssh
-rw------- devuser devuser authorized_keys
```


















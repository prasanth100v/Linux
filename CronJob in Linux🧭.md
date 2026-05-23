### ✅ What is a Cron Job?
 * A cron job is a scheduled task that runs automatically at a fixed time or interval (`minutes`, `hours`, `days`, etc.).
 * Examples:
     * Run a backup every night
     * Clean logs every week
     * Restart a service daily

### For system-wide crontab:
```hcl
System cron jobs are in /etc/crontab or /etc/cron.d/
```
### 🔑 How cron access actually works in Linux
 * There are two files that control who can use cron :
     * /etc/cron.allow
     * /etc/cron.deny

### 1️⃣ If /etc/cron.allow exists
  * ➡️ ONLY users listed in this file can use cron
  * ➡️ All other users are blocked, even if they’re not in cron.deny

# Now add allowed users:
```hcl
sudo touch /etc/cron.allow
sudo vi /etc/cron.allow
```
### Example:
```yaml
root
ec2-user
prasanth
```
## 🔐 Best Practice (Production / Servers)

 * ✔️ Use /etc/cron.allow only
 * ✔️ Add only required users
 * ✔️ Keep /etc/cron.deny empty or remove it

###  Cron job syntax (very important)
```hcl
* * * * * command_to_run
│ │ │ │ │
│ │ │ │ └── Day of week (0–7) (Sun=0 or 7)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```

### STEP 1: Check if cron service is running
```hcl
systemctl status cron        # Ubuntu / Debian
systemctl status crond       # RHEL / CentOS / Amazon Linux
```
If not running:
```bash
sudo systemctl start cron
sudo systemctl enable cron
```

### STEP 2: Open crontab editor
```hcl
crontab -e      # Edit your personal cron jobs
crontab -l      # List your cron jobs
crontab -r      # Remove all cron jobs (be careful!)
```

### STEP 3: Add your first cron job (examples)
▶ Example 1: Run script every day at 2 AM
```hcl
0 2 * * * /home/user/backup.sh
```
▶ Example 2: Run every 5 minutes
```hcl
*/5 * * * * /home/user/health_check.sh
```
### STEP 4: Save and exit
```hcl
vi → :wq           # Cron installs automatically 🎉
```
### STEP 5: Verify cron jobs
```hcl
crontab -l
```
### STEP 6: Make sure script is executable
```hcl
chmod +x /home/user/backup.sh
```
⚠️ Cron will NOT run non-executable scripts.

### STEP 8: Use absolute paths (VERY IMPORTANT)
```hcl
❌ Bad: backup.sh
✅ Good: /home/user/backup.sh
```

### 1️⃣ Create the script
```hcl
vi hello.sh
```
```hcl
#!/bin/bash

echo "welcome to KK FUNDA"
echo "today date is:"
date
uptime
```
### 2️⃣ How to run the shell script
✅ Method 1: Using sh (no execute permission needed) ✔️ Works even without chmod
```hcl
sh hello.sh
```
✅ Method 2: Using ./ Give execute permission : x = executable ✔️
```hcl
chmod u+x hello.sh
./hello.sh
```
✔️ This is the correct way for cron jobs
### Add cron job (every 1 minute)
Edit crontab:
```hcl
crontab -e
```
Add:
```hcl
*/1 * * * * /home/ec2-user/hello.sh >> /home/ec2-user/hello.log 2>&1
```
### TL;DR
```hcl
✔️ Use > when you want to replace a file
✔️ Use >> when you don’t want to lose previous output
```
### 🔍 Compare > vs >>
```hcl
Symbol   	Meaning          	What happens
  >	      overwrite	          Old output ❌ deleted
  >>	    append            	Old output ✅ preserved
```
🔍 Breakdown:

 * */1 * * * * → every 1 minute
 * /home/ec2-user/hello.sh → absolute path (`mandatory`)
 * >> hello.log → append output
 * 2>&1 → capture errors too (`VERY IMPORTANT`)

### Validate cron job
Check cron list:
```hcl
crontab -l
```
Check logs after a minute:
```hcl
tail -f /home/ec2-user/hello.log
```

---

## ⏰ Linux Cron Job — Rapid Fire Interview Questions & Answers

| 🔢 Q#   | ❓ Question                                        | 💡 Answer                                                               |
| ------- | --------------------------------------------------- | ----------------------------------------------------------------------- |
| 🔹 Q1   | What is a cron job?                                 | 👉 A scheduled task that runs automatically at fixed time.         |
| 🔹 Q2   | Common uses of cron jobs?                           | 👉 Backups, log cleanup, monitoring, service restart.                   |
| 🔹 Q3   | Which daemon runs cron jobs?                        | 👉 `cron` or `crond`                                                        |
| 🔹 Q4   | Cron service name in Ubuntu/Debian?                 | 👉 `cron`                                                                 |
| 🔹 Q5   | Cron service name in RHEL/CentOS/Amazon Linux?      | 👉 `crond `                                                               |
| ⚙️ Q6   | Command to check cron service status in Ubuntu?     | 👉 `systemctl status cron  `                                              |
| ⚙️ Q7   | Command to check cron service in RHEL/Amazon Linux? | 👉 `systemctl status crond`                                               |
| ⚙️ Q8   | Command to start cron service?                      | 👉 `sudo systemctl start cron  `                                          |
| ⚙️ Q9   | Command to enable cron service at boot?             | 👉 `sudo systemctl enable cron  `                                         |
| 📂 Q10  | System-wide crontab location?                       | 👉 `/etc/crontab `                                                        |
| 📂 Q11  | Directory for additional cron jobs?                 | 👉 /etc/cron.d/                                                         |
| 🔐 Q12  | Which file allows specific users to use cron?       | 👉 `/etc/cron.allow  `                                                    |
| 🔐 Q13  | Which file blocks users from cron?                  | 👉 `/etc/cron.deny  `                                                     |
| 🔐 Q14  | If /etc/cron.allow exists, who can use cron?        | 👉 Only listed users.                                                   |
| 🔐 Q15  | Best practice for cron access?                      | 👉 Use `/etc/cron.allow only`.                                            |
| 🔐 Q16  | Command to create cron.allow?                       | 👉 `sudo touch /etc/cron.allow    `                                       |
| 🔐 Q17  | Command to edit cron.allow?                         | 👉 `sudo vi /etc/cron.allow  `                                            |
| 📝 Q18  | Command to edit cron jobs?                          | 👉 `crontab -e  `                                                         |
| 📝 Q19  | Command to list cron jobs?                          | 👉 `crontab -l`                                                           |
| 📝 Q20  | Command to remove all cron jobs?                    | 👉 `crontab -r `                                                          |
| ⚠️ Q21  | Why is `crontab -r` dangerous?                      | 👉 Deletes all cron jobs permanently.                                   |
| 🧠 Q22  | Basic cron syntax?                                  | 👉 * * * * * command                                                    |
| 🧠 Q23  | Cron field order?                                   | 👉 `Minute Hour Day Month Weekday `Command                                |
| 🧠 Q24  | Minute range in cron?                               | 👉 0-59                                                                 |
| 🧠 Q25  | Hour range in cron?                                 | 👉 0-23                                                                 |
| 🧠 Q26  | Month range in cron?                                | 👉 1-12                                                                 |
| 🧠 Q27  | Day of week range?                                  | 👉 0-7                                                                  |
| 🧠 Q28  | Which values represent Sunday?                      | 👉 `0 or 7`                                                               |
| ⏰ Q29   | Run job every day at 2 AM?                          | 👉 0 2 * * * /home/user/backup.sh                                       |
| ⏰ Q30   | Run job every 5 minutes?                            | 👉 */5 * * * * /home/user/health_check.sh                               |
| ⏰ Q31   | Run job every minute?                               | 👉 * * * * * command                                                    |
| ⏰ Q32   | Meaning of */5 in cron?                             | 👉 Every 5 units.                                                       |
| ⏰ Q33   | Cron expression for every Sunday midnight?          | 👉 0 0 * * 0 command                                                    |
| ⏰ Q34   | Cron expression for every month 1st day?            | 👉 0 0 1 * * command                                                    |
| 📜 Q35  | Command to create shell script?                     | 👉 `vi hello.sh  `                                                        |
| 📜 Q36  | What is shebang in shell script?                    | 👉` #!/bin/bash  `                                                        |
| 📜 Q37  | Purpose of shebang?                                 | 👉 Defines `script interpreter`.                                          |
| 📜 Q38  | Run script without execute permission?              | 👉 `sh hello.sh  `                                                        |
| 📜 Q39  | Command to make script executable?                  | 👉` chmod u+x hello.sh   `                                                |
| 📜 Q40  | Run executable script?                              | 👉` ./hello.sh  `                                                         |
| 📜 Q41  | Which method is preferred for cron jobs?            | 👉 Executable script using `./script.sh `                                 |
| 📄 Q42  | Cron job with logging example?                      | 👉 */1 * * * * /home/ec2-user/hello.sh >> /home/ec2-user/hello.log 2>&1 |
| 📄 Q43  | Meaning of >>?                                      | 👉 Append output. (adding `new data`, `text`, or `results` without overwriting or deleting what was previously there.) |
| 📄 Q44  | Meaning of >?                                       | 👉 Overwrite output.                                                    |
| 📄 Q45  | Difference between > and >>?                        | 👉 `> replaces` file, `>> appends`.                                         |
| 📄 Q46  | Meaning of 2>&1?                                    | 👉 Redirect stderr to stdout.                                           |
| 📄 Q47  | Why use 2>&1 in cron?                               | 👉 `Capture errors in log file`.                                          |
| 📄 Q48  | Why use log files in cron jobs?                     | 👉 Troubleshooting and monitoring.                                      |
| 📌 Q49  | Why use absolute paths in cron?                     | 👉 Cron has limited environment variables.                              |
| 📌 Q50  | Bad cron example?                                   | 👉 `backup.sh   `                                                         |
| 📌 Q51  | Good cron example?                                  | 👉 `/home/user/backup.sh `                                                |
| 🔍 Q52  | Command to verify cron jobs?                        | 👉 `crontab -l`                                                           |
| 🔍 Q53  | Command to monitor cron log output?                 | 👉 `tail -f /home/ec2-user/hello.log `                                    |
| 🔍 Q54  | Which command follows logs in real time?            | 👉 `tail -f `                                                             |
| 🛠️ Q55 | Why cron jobs sometimes fail?                       | 👉 Wrong paths, permissions, or cron service stopped.                   |
| 🛠️ Q56 | Most common cron mistake?                           | 👉 Using relative paths.                                                |
| 🛠️ Q57 | Why executable permission is required?              | 👉 `Cron cannot execute non-executable scripts`.                          |
| 🚀 Q58  | Cron use case for backups?                          | 👉 `Daily database backup automation`.                                    |
| 🚀 Q59  | Cron use case for monitoring?                       | 👉 Health check scripts every 5 minutes.                                |
| 🚀 Q60  | Cron use case for cleanup?                          | 👉 `Delete old logs weekly.`                                              |
| 🚀 Q61  | Cron use case for restart?                          | 👉 Restart services during maintenance windows.                         |
| 🛠️ Q62 | Why cron jobs work manually but fail in cron?       | 👉 Different environment variables.                                     |
| 🛠️ Q63 | What should be checked first if cron fails?         | 👉 `Cron service status`.                                                 |
| 🛠️ Q64 | Why use full command paths in cron?                 | 👉 PATH variable may not be available.                                  |

### ✅ What is a Cron Job?

A cron job is a scheduled task that runs automatically at a fixed time or interval (minutes, hours, days, etc.).

Examples:

Run a backup every night

Clean logs every week

Restart a service daily
### For system-wide crontab:
```
System cron jobs are in /etc/crontab or /etc/cron.d/
```
### 🔑 How cron access actually works in Linux
There are two files that control who can use cron:

/etc/cron.allow

/etc/cron.deny

### 1️⃣ If /etc/cron.allow exists
➡️ ONLY users listed in this file can use cron ➡️ All other users are blocked, even if they’re not in cron.deny
# Now add allowed users:
```
sudo touch /etc/cron.allow
sudo vi /etc/cron.allow
```
Example:
```
root
ec2-user
prasanth
```
### 🔐 Best Practice (Production / Servers)

✔️ Use /etc/cron.allow only
✔️ Add only required users
✔️ Keep /etc/cron.deny empty or remove it
###  Cron job syntax (very important)
```
* * * * * command_to_run
│ │ │ │ │
│ │ │ │ └── Day of week (0–7) (Sun=0 or 7)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```

### STEP 1: Check if cron service is running
```
systemctl status cron        # Ubuntu / Debian
systemctl status crond       # RHEL / CentOS / Amazon Linux
```
If not running:
```
sudo systemctl start cron
sudo systemctl enable cron
```
### STEP 2: Open crontab editor
```
crontab -e      # Edit your personal cron jobs
crontab -l      # List your cron jobs
crontab -r      # Remove all cron jobs (be careful!)
```
### STEP 3: Add your first cron job (examples)
▶ Example 1: Run script every day at 2 AM
```
0 2 * * * /home/user/backup.sh
```
▶ Example 2: Run every 5 minutes
```
*/5 * * * * /home/user/health_check.sh
```
### STEP 4: Save and exit
```
vi → :wq   #Cron installs automatically 🎉
```
### STEP 5: Verify cron jobs
```
crontab -l
```
### STEP 6: Make sure script is executable
```
chmod +x /home/user/backup.sh
```
⚠️ Cron will NOT run non-executable scripts.
### STEP 8: Use absolute paths (VERY IMPORTANT)
```
❌ Bad: backup.sh      ✅ Good: /home/user/backup.sh
```

# 🔍 What is find?
find searches files & directories based on name, type, size, time, owner, permissions.

## 🔍 Linux find Command – DevOps Use-Cases Table
| #  | Use Case (DevOps)                  | Command                                                     | Explanation                              |
| -- | ---------------------------------- | ----------------------------------------------------------- | ---------------------------------------- |
| 1  | Find a file by name                | `find / -name app.log`                                      | Search file recursively (case-sensitive) |
| 2  | Case-insensitive search            | `find / -iname app.log`                                     | Finds `App.log`, `APP.LOG`, etc          |
| 3  | Find only files                    | `find /var/log -type f`                                     | `f` = file                               |
| 4  | Find only directories              | `find /opt -type d`                                         | `d` = directory                          |
| 5  | Find large files                   | `find / -type f -size +1G`                                  | Disk usage troubleshooting               |
| 6  | Find files modified in last 24 hrs | `find /app -type f -mtime -1`                               | Debug recent changes                     |
| 7  | Find files older than 30 days      | `find /data -type f -mtime +30`                             | Cleanup old data                         |
| 8  | Find files by permission           | `find / -type f -perm 777`                                  | Security audit                           |
| 9  | Find SUID files                    | `find / -type f -perm -4000`                                | Privilege escalation check               |
| 10 | Find files owned by user           | `find / -type f -user nginx`                                | Ownership issues                         |
| 11 | Find files by group                | `find / -type f -group docker`                              | Access control                           |
| 12 | Find YAML files                    | `find / -type f \( -name "*.yml" -o -name "*.yaml" \)`      | Kubernetes configs                       |
| 13 | Find empty files                   | `find /app -type f -empty`                                  | Cleanup useless files                    |


# ✂️ Linux sed Command – Complete DevOps Table
### sed = Stream Editor
  Used for search, replace, insert, delete, and modify text in files.
  
## 🧰 sed Commands & DevOps Use-Cases
| #  | Use Case (DevOps)              | Command                                   | Explanation               |
| -- | ------------------------------ | ----------------------------------------- | ------------------------- |
| 1  | Print entire file              | `sed 'p' file.txt`                        | Prints all lines          |
| 2  | Print specific line            | `sed -n '5p' file.txt`                    | Prints only line 5        |
| 3  | Print line range               | `sed -n '10,20p' file.txt`                | Prints lines 10–20        |
| 4  | Delete a line                  | `sed '5d' file.txt`                       | Deletes line 5            |
| 5  | Delete range                   | `sed '10,20d' file.txt`                   | Deletes lines 10–20       |
| 6  | Delete empty lines             | `sed '/^$/d' file.txt`                    | Cleanup configs           |
| 7  | Search & replace (first match) | `sed 's/http/https/' file.txt`            | Replaces first occurrence |
| 8  | Replace all matches            | `sed 's/http/https/g' file.txt`           | Global replace            |
| 9  | Replace in file (in-place)     | `sed -i 's/dev/prod/g' app.conf`          | No new file               |
| 10 | Case-insensitive replace       | `sed 's/error/ERROR/gi' file.log`         | Ignore case               |
| 11 | Replace only in line range     | `sed '10,20s/foo/bar/g' file.txt`         | Scoped replace            |
| 12 | Config value replace           | `sed -i 's/^port=.*/port=8080/' app.conf` | Real config edit          |


# 🧮 awk Linux Command 
### awk is a pattern scanning & text processing

## 🧰 awk Commands & Real DevOps Use-Cases
| #  | Use Case (DevOps)      | Command                                                | Explanation                  |               |
| -- | ---------------------- | ------------------------------------------------------ | ---------------------------- | ------------- |
| 1  | Print entire file      | `awk '{print}' file.txt`                               | Prints all lines             |               |
| 2  | Print specific column  | `awk '{print $1}' file.txt`                            | `$1` = first column          |               |
| 3  | Print multiple columns | `awk '{print $1,$3}' file.txt`                         | Space-separated output       |               |
| 4  | Print with row number  | `awk '{print NR,$0}' file.txt`                         | `NR` = line number           |               |
| 5  | Print last column      | `awk '{print $NF}' file.txt`                           | `NF` = last field            |               |
| 6  | Print selected rows    | `awk 'NR==5' file.txt`                                 | Prints line 5                |               |
| 7  | Print range of rows    | `awk 'NR>=10 && NR<=20' file.txt`                      | Lines 10–20                  |               |
| 8  | Pattern matching       | `awk '/ERROR/ {print}' app.log`                        | Log filtering                |               |


# 🔎 Linux grep Command – Complete DevOps Table
### grep = Global Regular Expression Print
### Used to search text patterns in files, logs, and command output.

## 🧰 grep Commands & Real DevOps Use-Cases
| #  | Use Case (DevOps)        | Command                                    | Explanation            |               |
| -- | ------------------------ | ------------------------------------------ | ---------------------- | ------------- |
| 1  | Search word in file      | `grep "error" app.log`                     | Finds matching lines   |               |
| 2  | Case-insensitive search  | `grep -i "error" app.log`                  | Ignores case           |               |
| 3  | Search recursively       | `grep -r "DB_HOST" /etc/`                  | Search in all files    |               |
| 4  | Exact word match         | `grep -w "root" /etc/passwd`               | Whole-word match       |               |
| 5  | Count matches            | `grep -c "ERROR" app.log`                  | Count occurrences      |               |
| 6  | Show line numbers        | `grep -n "ERROR" app.log`                  | Debug faster           |               |
| 7  | Invert match             | `grep -v "INFO" app.log`                   | Exclude pattern        |               |
| 8  | Multiple patterns        | `grep -E "ERROR                            | WARN" app.log`         | OR condition  |
| 9  | Show matching filename   | `grep -l "ERROR" *.log`                    | Identify bad logs      |               |
| 10 | Before context only      | `grep -B 2 "ERROR" app.log`                | Pre-error context      |               |
| 11 | After context only       | `grep -A 2 "ERROR" app.log`                | Post-error context     |               |
| 12 | Search compressed logs   | `zgrep "ERROR" app.log.gz`                 | No unzip needed        |               |
| 13 | Ignore binary files      | `grep -I "ERROR" /var/log/*`               | Safe scan              |               |
| 14 | Filter running processes | `ps -ef                                    | grep nginx`            | Process check |
| 15 | **Before** context       | `grep -B5 "error" demo.txt`                | 5 lines *before* each match |
| 16 | **After** context        | `grep -A5 "error" demo.txt`                | 5 lines *after* each match  |
| 17 | **Context**              | `grep -C5 "error" demo.txt`                | 5 lines *before & after*    |


### grep – alternative for simple filtering
grep is the BEST alternative for awk/sed when your goal is only simple filtering.

# 🔍 tail -f (Follow logs in real time)
### tail -f shows the last lines of a file
## Perfect for:
application logs ➡️ Kubernetes logs ➡️ system troubleshooting

## Basic usage  
```
tail -f app.log                ➡️ Shows last 10 lines and keeps following
tail -n 50 -f app.log          ➡️ Show last 50 lines
tail -f app1.log app2.log      ➡️ Follow multiple files  
tail -f app.log | grep ERROR   ➡️ Watch errors only
kubectl logs -f pod-name       ➡️ Kubernetes pod logs
head -50 file.txt | tail -15   ➡️ Show lines 36 through 50, shows the last 15 lines
```

# 📌 head Command
| **Purpose**                      | **Command**                        | **Explanation**          |
| -------------------------------- | ---------------------------------- | ------------------------ |
| Display first 10 lines (default) | `head file.txt`                    | Shows top 10 lines       |
| Display first N lines            | `head -n 5 file.txt`               | Shows first 5 lines      |
| Short option for lines           | `head -5 file.txt`                 | Same as `-n 5`           |
| Display first N bytes            | `head -c 20 file.txt`              | Shows first 20 bytes     |

# 📄 more and less command
### Both are pagers: they display long text one screen at a time so your terminal doesn’t flood.
```
more → older, simpler      ✔️ less → newer, powerful (and ironically “more” 😄) command
```
```
Basic usage : less filename
less doesn’t load the full file → fast & memory-efficient
Use less instead of cat for big files
```
Powerful navigation keys
| Key           | Action                |
| ------------- | --------------------- |
| `Space` / `f` | Forward one page      |
| `b`           | Back one page         |
| `↑ ↓`         | Line by line          |
| `g`           | Go to start           |
| `G`           | Go to end             |
| `q`           | Quit                  |


# 🔄 nohup sh — what it means & how to use it
### nohup sh starts a shell (sh) that ignores hangup signals, so anything you run inside it keeps running after you log out.
```
nohup sh demo.sh &
```
Redirect output (best practice)
```
  nohup sh demo.sh > demo.log 2>&1 &
```
🔹 Check status
```
ps -ef | grep demo.sh
echo $!                    #if you just started it
```
🔹 Stop the process
```
kill PID
kill -9 PID
```
## 🔑 Differences you should know
| Command                | Behavior                           |
| ---------------------- | ---------------------------------- |
| `nohup sh`             | Interactive shell immune to logout |
| `nohup sh script.sh &` | Run script safely in background    |
| `sh script.sh`         | Stops on logout                    |
| `./script.sh`          | Needs execute permission           |

---

## ⚡ Linux File Processing & Log Monitoring — Rapid Fire Interview Q&A
| 🔢 Q#   | ❓ Question                                       | 💡 Answer                                               |
| ------- | ------------------------------------------------ | --------------------------------------------------------- |
| 🔍 Q1   | What is `find` command?                          | 👉 Searches `files` and `directories` recursively.       |
| 🔍 Q2   | Command to find a file by name?                  | 👉 `find / -name app.log`                                 |
| 🔍 Q3   | Difference between -name and -iname?             | 👉 `-name` is case-sensitive, `-iname` is case-insensitive. |
| 🔍 Q4   | Command to find files only?                      | 👉 `find /var/log -type f `                               |
| 🔍 Q5   | Command to find directories only?                | 👉 `find /opt -type d `                                   |
| 🔍 Q6   | Meaning of -type f?                              | 👉 Regular files.                                       |
| 🔍 Q7   | Meaning of -type d?                              | 👉 Directories.                                         |
| 🔍 Q8   | Command to find files larger than 1GB?           | 👉` find / -type f -size +1G     `                        |
| 🔍 Q9   | Command to find files modified in last 24 hours? | 👉` find /app -type f -mtime -1  `                        |
| 🔍 Q10  | Command to find files older than 30 days?        | 👉` find /data -type f -mtime +30  `                      |
| 🔍 Q11  | Meaning of mtime?                                | 👉 `File modification time`.                              |
| 🔍 Q12  | Command to find files with permission 777?       | 👉 `find / -type f -perm 777 `                            |
| 🔍 Q13  | Why is finding 777 files important?              | 👉 Security auditing.                                   |
| 🔍 Q14  | Command to find SUID files?                      | 👉 `find / -type f -perm -4000  `                         |
| 🔍 Q15  | Why check SUID files?                            | 👉 Detect privilege escalation risks.                   |
| 🔍 Q16  | Command to find files owned by nginx user?       | 👉 `find / -type f -user nginx   `                        |
| 🔍 Q17  | Command to find files by group?                  | 👉 `find / -type f -group docker  `                       |
| 🔍 Q18  | Command to find YAML files?                      | 👉 `find / -type f ( -name "*.yml" -o -name "*.yaml" )`   |
| 🔍 Q19  | Command to find empty files?                     | 👉 `find /app -type f -empty    `                         |
| ✂️ Q20  | What is sed?                                     | 👉 Stream editor for `modifying text`. a powerful non-interactive text editor used to find, replace, delete, and insert text within files |
| ✂️ Q21  | Command to print entire file using sed?          | 👉 `sed 'p' file.txt`                                     |
| ✂️ Q22  | Command to print only line 5?                    | 👉 `sed -n '5p' file.txt  `                               |
| ✂️ Q23  | Meaning of -n in sed?                            | 👉 Suppresses automatic printing.                       |
| ✂️ Q24  | Command to print lines 10–20?                    | 👉 `sed -n '10,20p' file.txt   `                          |
| ✂️ Q25  | Command to delete line 5?                        | 👉 `sed '5d' file.txt   `                                 |
| ✂️ Q26  | Command to delete lines 10–20?                   | 👉 `sed '10,20d' file.txt   `                             |
| ✂️ Q27  | Command to delete empty lines?                   | 👉 sed '/^$/d' file.txt                                 |
| ✂️ Q28  | Command for first occurrence replace?            | 👉 `sed 's/http/https/' file.txt  `                       |
| ✂️ Q29  | Command for global replace?                      | 👉 `sed 's/http/https/g' file.txt `  every occurrence      |
| ✂️ Q30  | Meaning of g in sed replace?                     | 👉 Global replacement.                                  |
| ✂️ Q31  | Command for in-place modification?               | 👉 `sed -i 's/dev/prod/g' app.conf    `                   |
| ✂️ Q32  | Meaning of -i in sed?                            | 👉 `Edit file directly`.                                  |
| ✂️ Q33  | Command for case-insensitive replace?            | 👉 `sed 's/error/ERROR/gi' file.log  `                    |
| ✂️ Q34  | Meaning of i in sed replace?                     | 👉` Ignore case`.                                         |
| ✂️ Q35  | Command to replace only between lines 10–20?     | 👉 `sed '10,20s/foo/bar/g' file.txt  `                    |
| ✂️ Q36  | Real DevOps sed use-case?                        | 👉 Updating configs automatically.                      |
| ✂️ Q37  | Command to change port in config?                | 👉 `sed -i 's/^port=.*/port=8080/' app.conf `             |
| 🧮 Q38  | What is awk?                                     | 👉 Pattern scanning and text processing tool.           |
| 🧮 Q39  | Command to print entire file?                    | 👉 `awk '{print}' file.txt     `                          |
| 🧮 Q40  | Command to print first column?                   | 👉` awk '{print $1}' file.txt    `                        |
| 🧮 Q41  | Meaning of $1 in awk?                            | 👉 `First column`.                                        |
| 🧮 Q42  | Command to print multiple columns?               | 👉 `awk '{print $1,$3}' file.txt  `                       |
| 🧮 Q43  | Command to print row numbers?                    | 👉 `awk '{print NR,$0}' file.txt   `                      |
| 🧮 Q44  | Meaning of NR?                                   | 👉 `Current line number`.                                 |
| 🧮 Q45  | Meaning of $0?                                   | 👉 `Entire current line`.                                 |
| 🧮 Q46  | Command to print last column?                    | 👉 `awk '{print $NF}' file.txt  `                         |
| 🧮 Q47  | Meaning of NF?                                   | 👉 Number of fields / last column.                      |
| 🧮 Q48  | Command to print line 5?                         | 👉 `awk 'NR==5' file.txt  `                               |
| 🧮 Q49  | Command to print lines 10–20?                    | 👉 `awk 'NR>=10 && NR<=20' file.txt  `                    |
| 🧮 Q50  | Command for pattern matching in logs?            | 👉` awk '/ERROR/ {print}' app.log`                        |
| 🔎 Q51  | What does grep stand for?                        | 👉 Global Regular Expression Print.                     |
| 🔎 Q52  | Main purpose of grep?                            | 👉 Search text patterns.                                |
| 🔎 Q53  | Command to search word in file?                  | 👉 `grep "error" app.log   `                              |
| 🔎 Q54  | Command for case-insensitive search?             | 👉` grep -i "error" app.log    `                          |
| 🔎 Q55  | Command for recursive search?                    | 👉 `grep -r "DB_HOST" /etc/ ` search through a starting `folder` (and their every `sub-subfolders`)  |
| 🔎 Q56  | Meaning of -r in grep?                           | 👉 Recursive search.                                    |
| 🔎 Q57  | Command for exact word match?                    | 👉` grep -w "root" /etc/passwd    `                       |
| 🔎 Q58  | Meaning of -w?                                   | 👉` Whole-word match`.                                    |
| 🔎 Q59  | Command to count matches?                        | 👉 `grep -c "ERROR" app.log      `                        |
| 🔎 Q60  | Meaning of -c?                                   | 👉 Count matching lines.                                |
| 🔎 Q61  | Command to show line numbers?                    | 👉` grep -n "ERROR" app.log  `                            |
| 🔎 Q62  | Meaning of -n in grep?                           | 👉 Show line numbers.                                   |
| 🔎 Q63  | Command for inverted match?                      | 👉 `grep -v "INFO" app.log ` except the `specific word `   |
| 🔎 Q64  | Meaning of -v?                                   | 👉 Exclude matching lines.                              |
| 🔎 Q65  | Command for multiple patterns?                   | 👉 grep -E "ERROR|WARN" app.log                       |
| 🔎 Q66  | Meaning of -E?                                   | 👉 Extended regular expressions.                        |
| 🔎 Q67  | Command to show filenames containing match?      | 👉 `grep -l "ERROR" *.log `                               |
| 🔎 Q68  | Meaning of -l?                                   | 👉 Show matching filenames only.                        |
| 🔎 Q69  | Command for before-context?                      | 👉 grep -B 2 "ERROR" app.log                            |
| 🔎 Q70  | Meaning of -B?                                   | 👉 Show lines `before match`.                             |
| 🔎 Q71  | Command for after-context?                       | 👉 grep -A 2 "ERROR" app.log                            |
| 🔎 Q72  | Meaning of -A?                                   | 👉 Show lines `after match`.                              |
| 🔎 Q73  | Command for full context?                        | 👉 grep -C 5 "ERROR" app.log                            |
| 🔎 Q74  | Meaning of -C?                                   | 👉 Show `before and after context`.                       |
| 🔎 Q75  | Command to search compressed logs?               | 👉 `zgrep "ERROR" app.log.gz `                            |
| 🔎 Q76  | Command to ignore binary files?                  | 👉 `grep -I "ERROR" /var/log/* `                          |
| 🔎 Q77  | Command to filter running process?               | 👉 ps -ef | grep nginx                                  |
| 📜 Q78  | What does tail do?                               | 👉 Shows `last lines of a file.  `                        |
| 📜 Q79  | Command to follow logs in real time?             | 👉 tail -f app.log                                      |
| 📜 Q80  | Meaning of -f in tail?                           | 👉 Follow file continuously.                            |
| 📜 Q81  | Command to show last 50 lines and follow?        | 👉 `tail -n 50 -f app.log      `                          |
| 📜 Q82  | Command to follow multiple logs?                 | 👉 `tail -f app1.log app2.log     `                       |
| 📜 Q83  | Command to monitor only errors?                  | 👉 tail -f app.log | grep ERROR                         |
| ☸️ Q84  | Kubernetes equivalent of tail -f?                | 👉 kubectl logs -f pod-name                             |
| 📌 Q85  | What does head do?                               | 👉 `Shows beginning lines of a file. `                    |
| 📌 Q86  | Default lines shown by head?                     | 👉 `10 lines`.                                            |
| 📌 Q87  | Command to show first 5 lines?                   | 👉 head -n 5 file.txt                                   |
| 📌 Q88  | Short form of head -n 5?                         | 👉 head -5 file.txt                                     |
| 📌 Q89  | Command to show first 20 bytes?                  | 👉 head -c 20 file.txt                                  |
| 📄 Q90  | What are less and more?                          | 👉 Pagers for viewing large files.                      |
| 📄 Q91  | Which is more powerful: less or more?            | 👉 `less   `                                              |
| 📄 Q92  | Why use less instead of cat?                     | 👉 `Efficient for large files. `                          |
| 📄 Q93  | Command to open file in less?                    | 👉 `less file.txt `                                       |
| 📄 Q94  | Key to quit less?                                | 👉 `q   `                                                 |
| 📄 Q95  | Key to go to end in less?                        | 👉 `G `                                                   |
| 📄 Q96  | Key to go to start in less?                      | 👉 `g  `                                                  |
| 🔄 Q97  | What is nohup?                                   | 👉 Runs process even after logout or or close your terminal. nohup stands for `no hang up`.   |
| 🔄 Q98  | Command to run script in background safely?      | 👉 nohup `sh demo.sh` &                                   |
| 🔄 Q99  | Best practice nohup command?                     | 👉 `nohup sh demo.sh > demo.log 2>&1 & ` `demo.sh` script in the background, You can safely close your terminal or log out, and the script will continue executing uninterrupted until it finishes.   |
| 🔄 Q100 | Meaning of 2>&1?                                 | 👉 Redirect stderr to stdout. (any errors printed out on `STDERR` should go to `STDOUT`).                          |
| 🔄 Q101 | Command to check running process?                | 👉 ps -ef | grep demo.sh                                |
| 🔄 Q102 | Command to display last background PID?          | 👉 `echo $! ` prints the Process ID (`PID`) of the most recently executed background job.     |
| 🔄 Q103 | Command to stop process gracefully?              | 👉 `kill PID `                                            |
| 🔄 Q104 | Command to force kill process?                   | 👉 `kill -9 PID   `                                       |

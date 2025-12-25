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
```

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





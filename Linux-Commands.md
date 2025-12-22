 ### Most Frequently Used Linux Commands (DevOps-Focused) 🔥
 ```
ls        # list files
ls -l     # detailed list
ls -a     # show hidden files
pwd       # current directory
cd dir    # change directory
mkdir dir # create directory
rm file   # delete file
rm -rf dir# force delete directory
cp src dst# copy
mv src dst# move / rename
```
### Process & System Monitoring
```
ps -ef
top
htop
uptime
free -m
df -h
du -sh dir
kill PID
kill -9 PID
```
### 🔍 tail -f (Follow logs in real time)
tail -f shows the last lines of a file
Perfect for:

application logs ➡️ Kubernetes logs ➡️ system troubleshooting

### Basic usage  
```
tail -f app.log                ➡️ Shows last 10 lines and keeps following
tail -n 50 -f app.log          ➡️ Show last 50 lines
tail -f app1.log app2.log      ➡️ Follow multiple files  
tail -f app.log | grep ERROR   ➡️ Watch errors only
kubectl logs -f pod-name       ➡️ Kubernetes pod logs
```
### find — find files/directories
 Find a file by name
 ```
find /var/log -name "*.log"
```

### grep – alternative for simple filtering



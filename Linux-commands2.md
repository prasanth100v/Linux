### 🫗 tee Command in Linux
  tee = see output + save output (at the same time)

### Common use cases (with examples)
```
1️⃣ View output and save it     You see the listing on screen   It’s also saved to output.txt   
          🔸 ls -l | tee output.txt

2️⃣ Append instead of overwrite   ➡️    -a → append mode
          🔸 date | tee -a log.txt

3️⃣ Save output to multiple files
          🔸 uname -a | tee file1.txt file2.txt

4️⃣ Capture output of a root command (very common)
          🔸 sudo dnf install nginx | tee install.log

⚠️ If the command needs sudo, tee may need it too:
          🔸 command | sudo tee /etc/config.conf  ➡️   echo "Hello" | sudo tee /etc/test.conf
```

### uniq Command in Linux —  uniq filters duplicate lines
```
1️⃣ Remove duplicate lines        ➡️   sort names.txt | uniq
3️⃣ Show only duplicate lines     ➡️  sort file.txt | uniq -d
```
### 📦 zcat — view compressed files
✅ One-line memory trick  🔸 zcat = cat  🔸 zgrep = grep 

Common examples
```
zcat app.log.gz
zcat app.log.gz | less          # safe for large logs
zcat app.log.gz | head
zcat app.log.gz | tail
```
### 🔍 zgrep — search inside compressed files
Common examples
```
zgrep ERROR app.log.gz
zgrep -i warning app.log.gz     # ignore case
zgrep -n ERROR app.log.gz       # show line numbers
zgrep -c ERROR app.log.gz       # count matches
zgrep "500" *.log.gz            # Search across many logs
```
### 🌐 ping Command (Network Check) (internet connectivity)
```
ping google.com
ping 8.8.8.8
ping -c 4 google.com     # send 4 packets
ping -i 2 8.8.8.8        # interval 2 sec
ping -s 1000 8.8.8.8     # packet size
```
### 📦 yum Command (Package Manager) 
Installs, updates, removes software on RHEL / CentOS / Amazon Linux systems.
```
sudo yum install nginx
sudo yum remove nginx
sudo yum update
```
### 🖥️ System Information – Commands
| Task            | Command               |
| --------------- | --------------------- |
| OS details      | `cat /etc/os-release` |
| Kernel version  | `uname -r`            |
| Architecture    | `uname -m`            |
| Hostname        | `hostname`            |
| All system info | `uname -a`            |
| CPU details    | `lscpu`             |
| CPU info file  | `cat /proc/cpuinfo` |
| Live CPU usage | `top` / `htop`      |















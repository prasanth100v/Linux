### 🫗 tee Command in Linux
tee = see output + save output (at the same time)

### Common use cases (with examples)
```
1️⃣ View output and save it     You see the listing on screen   It’s also saved to output.txt   
          🔸 ls -l | tee output.txt

2️⃣ Append instead of overwrite       -a → append mode
          🔸 date | tee -a log.txt

3️⃣ Save output to multiple files
          🔸 uname -a | tee file1.txt file2.txt

4️⃣ Capture output of a root command (very common)
          🔸 sudo dnf install nginx | tee install.log

⚠️ If the command needs sudo, tee may need it too:
          🔸 command | sudo tee /etc/config.conf     echo "Hello" | sudo tee /etc/test.conf
```














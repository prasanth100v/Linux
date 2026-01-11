## 🔎 Linux Commands to Search User Details
| Command                  | What it Shows              | Example                     | Use Case               |
| ------------------------ | -------------------------- | --------------------------- | ---------------------- |
| `id username`            | UID, GID, groups           | `id prasanth`               | Check user ID & groups |
| `whoami`                 | Current logged-in user     | `whoami`                    | Verify active user     |
| `who`                    | Logged-in users            | `who`                       | See active sessions    |
| `w`                      | Logged-in users + activity | `w`                         | Check user activity    |
| `users`                  | Logged-in usernames        | `users`                     | Quick user list        |
| `last`                   | Login history              | `last prasanth`             | Audit logins           |
| `lastlog`                | Last login of users        | `lastlog -u prasanth`       | Security checks        |
| `getent passwd username` | User account details       | `getent passwd prasanth`    | NSS-based lookup       |
| `cat /etc/passwd`        | All users                  | `cat /etc/passwd`           | Local users list       |
| `grep user /etc/passwd`  | Search specific user       | `grep prasanth /etc/passwd` | Quick lookup           |
| `groups username`        | User groups                | `groups prasanth`           | Permission check       |
| `finger username`        | User info (if enabled)     | `finger prasanth`           | User profile           |
| `chage -l username`      | Password expiry info       | `chage -l prasanth`         | Account aging          |
| `passwd -S username`     | Password status            | `passwd -S prasanth`        | Locked/unlocked        |







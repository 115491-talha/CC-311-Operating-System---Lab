
---

# 🐧 Linux Commands Cheat Sheet

---

## 📁 1. File & Directory Management

| Command | Purpose                      | Example            |
| ------- | ---------------------------- | ------------------ |
| `ls`    | List files                   | `ls -l`            |
| `pwd`   | Show current directory       | `pwd`              |
| `cd`    | Change directory             | `cd /home/user`    |
| `mkdir` | Create directory             | `mkdir test`       |
| `rmdir` | Remove empty directory       | `rmdir test`       |
| `rm`    | Delete files/directories     | `rm file.txt`      |
| `rm -r` | Delete directory recursively | `rm -r folder`     |
| `cp`    | Copy files                   | `cp a.txt b.txt`   |
| `mv`    | Move/rename files            | `mv a.txt new.txt` |
| `touch` | Create empty file            | `touch file.txt`   |

---

## 📄 2. File Viewing & Editing

| Command      | Purpose                | Example         |
| ------------ | ---------------------- | --------------- |
| `cat`        | Display file content   | `cat file.txt`  |
| `less`       | View file page by page | `less file.txt` |
| `more`       | Similar to less        | `more file.txt` |
| `head`       | First 10 lines         | `head file.txt` |
| `tail`       | Last 10 lines          | `tail file.txt` |
| `nano`       | Simple editor          | `nano file.txt` |
| `vi` / `vim` | Advanced editor        | `vim file.txt`  |

---

## 🔐 3. File Permissions

| Command | Purpose            | Example                |
| ------- | ------------------ | ---------------------- |
| `chmod` | Change permissions | `chmod 755 file.sh`    |
| `chown` | Change owner       | `chown user file.txt`  |
| `chgrp` | Change group       | `chgrp group file.txt` |

### Permission Values

| Number | Permission |
| ------ | ---------- |
| 7      | rwx        |
| 6      | rw-        |
| 5      | r-x        |
| 4      | r--        |

---

## 🔗 4. Links

| Command | Purpose       | Example              |
| ------- | ------------- | -------------------- |
| `ln`    | Hard link     | `ln file linkfile`   |
| `ln -s` | Symbolic link | `ln -s file symlink` |

---

## 🔍 5. Searching & Filtering

| Command  | Purpose      | Example                 |
| -------- | ------------ | ----------------------- |
| `find`   | Search files | `find . -name file.txt` |
| `grep`   | Search text  | `grep "word" file.txt`  |
| `locate` | Fast search  | `locate file.txt`       |
| `which`  | Command path | `which python`          |

---

## 📊 6. Process Management

| Command   | Purpose             | Example        |
| --------- | ------------------- | -------------- |
| `ps`      | Show processes      | `ps aux`       |
| `top`     | Real-time processes | `top`          |
| `htop`    | Better top          | `htop`         |
| `kill`    | Kill process        | `kill 1234`    |
| `kill -9` | Force kill          | `kill -9 1234` |
| `bg`      | Background job      | `bg`           |
| `fg`      | Foreground job      | `fg`           |

---

## 💾 7. Disk & Storage

| Command  | Purpose        | Example                |
| -------- | -------------- | ---------------------- |
| `df`     | Disk usage     | `df -h`                |
| `du`     | Directory size | `du -sh folder`        |
| `mount`  | Mount device   | `mount /dev/sda1 /mnt` |
| `umount` | Unmount device | `umount /mnt`          |

---

## 🌐 8. Networking

| Command    | Purpose             | Example            |
| ---------- | ------------------- | ------------------ |
| `ping`     | Test connection     | `ping google.com`  |
| `ifconfig` | Network config      | `ifconfig`         |
| `ip`       | Modern network tool | `ip a`             |
| `netstat`  | Network stats       | `netstat -tuln`    |
| `curl`     | Fetch data          | `curl example.com` |
| `wget`     | Download files      | `wget url`         |

---

## 📦 9. Package Management (Debian/Ubuntu)

| Command       | Purpose             | Example                |
| ------------- | ------------------- | ---------------------- |
| `apt update`  | Update package list | `sudo apt update`      |
| `apt upgrade` | Upgrade packages    | `sudo apt upgrade`     |
| `apt install` | Install package     | `sudo apt install git` |
| `apt remove`  | Remove package      | `sudo apt remove git`  |

---

## 🧵 10. Process & System Info

| Command   | Purpose         | Example    |
| --------- | --------------- | ---------- |
| `uname`   | System info     | `uname -a` |
| `whoami`  | Current user    | `whoami`   |
| `who`     | Logged users    | `who`      |
| `uptime`  | System uptime   | `uptime`   |
| `history` | Command history | `history`  |

---

## 📦 11. Compression & Archiving

| Command    | Purpose         | Example                  |
| ---------- | --------------- | ------------------------ |
| `tar -cvf` | Create archive  | `tar -cvf file.tar dir/` |
| `tar -xvf` | Extract archive | `tar -xvf file.tar`      |
| `gzip`     | Compress file   | `gzip file.txt`          |
| `gunzip`   | Decompress      | `gunzip file.txt.gz`     |
| `zip`      | Zip files       | `zip file.zip file.txt`  |
| `unzip`    | Unzip files     | `unzip file.zip`         |

---

## 🔄 12. Redirection & Pipes

| Symbol | Purpose           | Example         |     |           |
| ------ | ----------------- | --------------- | --- | --------- |
| `>`    | Redirect output   | `ls > out.txt`  |     |           |
| `>>`   | Append output     | `ls >> out.txt` |     |           |
| `<`    | Input redirection | `wc < file.txt` |     |           |
| `      | `                 | Pipe output     | `ls | grep txt` |

---

## ⚙️ 13. Useful Shortcuts

| Shortcut   | Meaning         |
| ---------- | --------------- |
| `Ctrl + C` | Stop process    |
| `Ctrl + Z` | Pause process   |
| `Ctrl + D` | Logout          |
| `Tab`      | Auto-complete   |
| `↑ / ↓`    | Command history |

---

## 🧠 Quick Exam Tips

* `ls -l` → detailed listing
* `chmod 755` → rwxr-xr-x
* Hard link → same inode
* Soft link → shortcut (→ symbol)
* `ps`, `top`, `kill` → process control
* `grep` + `|` → very common combo

---

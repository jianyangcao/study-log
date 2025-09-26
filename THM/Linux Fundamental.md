# Linux Fundamental

## 📌 General Commands
- `--help` : list possible options of a command  
  - Example: `ls --help`  
- `man <command>` : read manual documentation  
  - Example: `man ls`  
- `echo "text"` : output text  
  - Example: `echo "Hello Linux"`  
- `whoami` : display current logged-in user  

---

## 📂 Listing Files
- `ls` : list files in current directory  
- `ls folder1 folder2` : list files in given folders  
- `ls -R folder` : recursive listing (subfolders too)  
- `ls -a` : show hidden files (dotfiles)  
- `ls -l` : detailed info (permissions, owner, group, size, date)  
- `ls -lh` : human-readable file sizes (e.g., KB, MB, GB)  

---

## 📁 File & Directory Commands
- `cd <dir>` : change directory  
  - `cd ..` : go up one level  
  - `cd ~` : go to home directory  
- `pwd` : show full path of current directory  
- `cat <file>` : show file contents  
- `touch <file>` : create empty file  
- `mkdir <dir>` : create folder  
- `cp file1 file2` : copy file  
- `mv file1 file2` : move or rename file  
- `rm <file>` : remove file  
- `rm -R <dir>` : remove folder recursively  
- `file <name>` : check file type  
- `su` : switch user  

---

## 🔎 Searching & Filtering
- `find -name password.txt` : find file by name  
- `find -name *.txt` : find all `.txt` files  
- `grep "pattern" file` : search inside file  
- `wc -l <file>` : count lines in a file  

---

## ⚙️ Operators
- `&` : run command in background  
- `&&` : run multiple commands in one line  
  - Example: `mkdir test && cd test`  
- `>` : redirect output (overwrite file)  
- `>>` : redirect output (append to file)  

---

## 🔐 SSH (Secure Shell)
- `ssh user@ip` : log in to remote machine  
  - Example: `ssh tryhackme@10.201.40.207`  

---

## 🌐 Downloading & File Transfer
### wget
- `wget <url>` : download file via HTTP  
  - Example: `wget http://example.com/file.txt`

- Local → Remote:  
  `scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`  
- Remote → Local:  
  `scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt`  

---

## 📡 Serving Files from Host
- Start server: `python3 -m http.server`  
- Use a custom port (e.g., 8080): `python3 -m http.server 8080`  
- Download from another machine: `wget http://<your-ip>:8000/myfile`  

---

## 📝 Text Editors
### Nano
- `nano <file>` : open or create file  
- Shortcuts:  
  - `Ctrl + W` : search  
  - `Ctrl + K` : cut line  
  - `Ctrl + U` : paste line  
  - `Ctrl + _` : jump to line  
  - `Ctrl + C` : show line/column number  
  - `Ctrl + X` : exit  

### Vim
- `vim <file>` : advanced text editor  
- Modes:  
  - `i` : insert mode  
  - `Esc` : normal mode  
  - `:w` : save  
  - `:q` : quit  
  - `:wq` : save & quit  

---

## 🖥️ Process Management
- Each process has a **PID (Process ID)**.  

### Viewing Processes
- `ps` : list running processes  
- `ps aux` : show processes from all users  
- `top` : real-time process monitoring  
- `htop` : interactive process viewer (if installed)  

### Killing Processes
- `kill <PID>` : terminate process  
- Signals:  
  - `SIGTERM` → polite terminate (default)  
  - `SIGKILL` → force kill  
  - `SIGSTOP` → pause/suspend  

Example: `kill -9 3594`  

### Systemd Services
- Start service: `systemctl start <service>`  
- Stop service: `systemctl stop <service>`  
- Enable service: `systemctl enable <service>`  
- Disable service: `systemctl disable <service>`  

---

## ⏳ Background & Foreground in Linux
- Run process in background: `command &`  
- Suspend process: `Ctrl + Z`  
- Resume in foreground: `fg`  
- Resume in background: `bg`


# Crontab & Automation Notes

## 📌 What is Crontab?
- A **crontab** is a special file with formatting recognized by the `cron` process.  
- It executes each line step by step according to the defined schedule.  
- Each crontab entry requires **6 fields**:

---

## 📂 Field Descriptions
- **MIN** → What minute to execute at (0–59)  
- **HOUR** → What hour to execute at (0–23)  
- **DOM** → What day of the month to execute at (1–31)  
- **MON** → What month of the year to execute at (1–12)  
- **DOW** → What day of the week to execute at (0–6, Sunday=0)  
- **CMD** → The actual command that will be executed  

---

## 📝 Example
- Backup "Documents" directory every 12 hours:  

`0 */12 * * * cp -R /home/cmnnatic/Documents /var/backups/`  

Meaning:  
- `0` → Run on the 0th minute  
- `*/12` → Every 12 hours  
- `* * *` → Every day, month, and weekday  
- Command: `cp -R /home/cmnnatic/Documents /var/backups/`

---

## ⚙️ Managing Crontab
- Edit crontab: `crontab -e`  
- List crontab: `crontab -l`  
- Remove crontab: `crontab -r`  

Default editor is usually **Nano**, but can be changed.  

---

## ⏱️ Special Strings in Crontab
Instead of numeric values, you can use these shortcuts:  

- `@reboot` → Run once at startup  
- `@hourly` → Run once every hour  
- `@daily` → Run once a day (midnight)  
- `@weekly` → Run once a week (Sunday 00:00)  
- `@monthly` → Run once a month (1st day, 00:00)  
- `@yearly` or `@annually` → Run once a year (Jan 1, 00:00)  

---

# ✅ Quick Tips
- Use `crontab -l` to confirm your tasks are scheduled.  
- Always use full paths in commands (e.g., `/usr/bin/python3`).  
- Redirect output to a log file for debugging:  
  - Example: `* * * * * /script.sh >> /var/log/cron.log 2>&1`  


# Linux System & Package Management Notes

---

## 📦 Package Management with APT
- The `apt` command is part of the **package management system** on Ubuntu/Debian.  
- It allows you to **install, update, and remove** software.  
- `apt` manages both the **packages** and the **sources (repositories)** from which the packages are retrieved.  
- It provides a whole suite of tools for managing software at the same time.

---

## 📂 Managing Repositories (Adding and Removing)

- Normally we use the `apt` command to install software.  
- Repositories are sources that contain the packages.  
- Adding repositories allows us to install software that is **not part of the default Ubuntu repositories**.  
- Repositories can be added manually or with helper commands like `add-apt-repository`.  
- Packages can also be installed with tools like `dpkg`, but `apt` is preferred because it automatically checks for **updates**.  

### 🔐 GPG Keys
- Software integrity is guaranteed by **GPG (GNU Privacy Guard) keys**.  
- GPG keys act as digital signatures from developers.  
- If the GPG key does not match what your system trusts, the software will not be downloaded or installed.  

---

## 📝 Example: Adding Sublime Text Repository（look to THM)

# Maintaining Your system:Logs (/var/log)



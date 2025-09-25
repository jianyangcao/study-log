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

---

# 📊 Cheat Sheet (Quick Reference)

| Category | Command | Example |
|----------|---------|---------|
| List files | `ls -lh` | Show files with readable sizes |
| Change dir | `cd <dir>` | `cd /etc` |
| Show path | `pwd` | `/home/user` |
| Show file | `cat <file>` | `cat notes.txt` |
| Create file | `touch <file>` | `touch test.txt` |
| Create folder | `mkdir <dir>` | `mkdir logs` |
| Copy | `cp src dst` | `cp a.txt b.txt` |
| Move/Rename | `mv src dst` | `mv old.txt new.txt` |
| Remove | `rm <file>` | `rm data.log` |
| Find file | `find -name "*.txt"` | Find all `.txt` |
| Search text | `grep "root" /etc/passwd` | Search "root" |
| Count lines | `wc -l <file>` | Count lines in file |
| SSH login | `ssh user@ip` | `ssh ubuntu@192.168.1.30` |
| File transfer | `scp file user@ip:/path` | `scp a.txt ubuntu@ip:/tmp/` |
| Serve file | `python3 -m http.server 8080` | Serve files on port 8080 |
| Processes | `ps aux` | Show running processes |
| Kill process | `kill -9 <PID>` | Force kill process |
| Systemctl | `systemctl start nginx` | Start nginx service |
| Background | `command &` | Run in background |
| Foreground | `fg` | Bring back process |

---

# ✅ Tips
- Always check `pwd` before using `rm -R`.  
- Use `ls -lh` for readable sizes.  
- Use `ps aux | grep <name>` to find processes quickly.  
- When transferring files, confirm IP and paths.  

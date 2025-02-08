# 1. modifier keys & terminal: 
## command, ctrl, shift
- if you're on mac, ctrl does not work, then try command
- if you're on linux, ctrl does not work, then try ctrl+shift
## tab, ctrl+r, up, down, ctrl+a, ctrl+e, clear
- **`Tab` (Autocomplete)**: **auto-complete** a command, filename, or directory.
- `Tab` twice (`Tab Tab`) shows available options, if there are multiple possibilities.
- **`Ctrl+R` (Reverse Search)**: Type part of a previous command, and it will find the most recent match in the command history.
- **`Up` (↑) / `Down` (↓)**: **backward** or **forward** through the command history.
- **`Ctrl+A` (Move Cursor to Beginning)**
- **`Ctrl+E` (Move Cursor to End)**
- `Ctrl+L` **Clear the terminal screen (like `clear` command)**.
## ctrl+shift+t, ctrl+shift+w, ctrl+shift+n
- New Tab: ctrl+shift+t
- Wipe tab: ctrl+shift+w
- New window: ctrl+shift+n
## ctrl+shift+c, ctrl+shift+v
- Copy: Ctrl+Shift+C
- Paste: Ctrl+Shift+V

# 2. get information
## --help
- Quick Help: Many commands support the `--help` option to provide a brief summary of their usage and available options.
- Best for **quick reference** when you need basic information about a command.
```bash
ls --help
```
## man 
- Manual Pages: `man` (short for **manual**) opens the detailed documentation for a command.
- `man` pages are **more detailed** than `--help` and include in-depth explanations.
```bash
man ls
```
## --help vs. man
| Feature  | `--help` | `man` |
|----------|---------|------|
| Output | Short summary | Full manual page |
| Coverage | Command usage & options | Detailed documentation |
| Availability | Not all commands support it | Almost all commands have a man page |
## manpages.ubuntu, stackoverflow, askubuntu, chatgpt
- online man pages for ubuntu: https://manpages.ubuntu.com/
- finding questions and solutions: https://stackoverflow.com/
- finding questions and solutions: https://askubuntu.com/
- getting helps from AI: https://chatgpt.com/

# 3. absolute/relative path and read/write/execute
## /a, ~/a, ../a, ./a, a, a/
- `/` root: `/a`
- `~` home: `~/a`
- `..` previous folder: `../a`
- `.` explicit current folder: `./a`
- `` implicit current folder `a`
- `folder/` indicate it's a folder: `a/`
- `./` execute the executable file `./a`
## cd, ls, ls -la, pwd
- `cd` (Change Directory)**
```
cd /home/user      # Go to /home/user
```
- `ls` (List Files and Directories)**
```
ls                # List files and directories in the current location
```
- `ls -la` (List with Details)**
```
**`-l`** → Shows a detailed list (permissions, owner, size, modification date).
**`-a`** → Shows **all** files, including **hidden files** (files starting with `.`).

ls -la
drwxr-xr-x  5 user user 4096 Feb  7 10:00 .
drwxr-xr-x 10 user user 4096 Feb  7 09:30 ..
-rw-r--r--  1 user user 1234 Feb  7 09:45 .hiddenfile
-rw-r--r--  1 user user 5678 Feb  7 09:40 myfile.txt
```
- `pwd` (Print Working Directory)**
```
pwd
/home/user/Documents
```
## rm, mv, cp, mkdir
- **`rm` (Remove/Delete Files & Directories)**
```bash
rm myfile.txt        # Delete a file
rm -r myfolder       # Delete a directory and its contents
rm -i file.txt       # Ask for confirmation before deleting
rm -rf myfolder      # Force delete a directory without confirmation (Dangerous!)
```
- **`mv` (Move/Rename Files & Directories)**
```bash
mv oldname.txt newname.txt    # Rename a file
mv myfile.txt /home/user/     # Move a file to another directory
mv myfolder /home/user/       # Move a folder to another location
mv *.txt Documents/           # Move all `.txt` files into Documents folder
```
- **`cp` (Copy Files & Directories)**
```bash
cp file.txt /home/user/       # Copy a file to another directory
cp file1.txt file2.txt        # Copy a file to a new name
cp -r folder1 folder2         # Copy a directory and its contents
cp *.jpg /home/user/Pictures/ # Copy all `.jpg` files to another folder
```
- **`mkdir` (Make Directory)**
```bash
mkdir myfolder             # Create a directory
mkdir -p myfolder/subdir   # Create a directory and its parent if it doesn't exist
mkdir {folder1,folder2}    # Create multiple directories at once
```
## ln
- **`ln` symbolic link**
- - A symbolic link (or symlink) is a shortcut that points to another file or directory. It works like a reference, allowing you to access the target without moving or copying it.
```
ln -s /home/user/original.txt /home/user/link.txt
ls -l /home/user/link.txt
lrwxrwxrwx 1 user user 16 Feb 7 12:30 link.txt -> /home/user/original.txt
```
## ssh, scp
- **`ssh` (Secure Shell, log in to remote servers, or execute commands over a network)**
```bash
ssh user@remote-server      # Connect to a remote server
ssh -p 2222 user@remote-server  # Specify a different port
ssh user@remote-server "ls -l /var/www"    # Run a command on a remote server without opening an interactive shell
```
- **`scp` (Secure Copy)**
```bash
scp file.txt user@remote-server:/home/user/          # Copy a file from local to remote
scp user@remote-server:/home/user/file.txt .         # Copy a file from remote to local
scp -r myfolder user@remote-server:/home/user/       # Copy a directory recursively
scp -P 2222 file.txt user@remote-server:/home/user/  # Use a specific SSH port (default is 22).
```

# 4. find/search
## find, locate, which, whereis
- **`find` (Search for Files & Directories)**
```bash
find /home/user -name "file.txt"   # Search for a file named "file.txt" in /home/user
find /var/log -type f              # Find all files inside /var/log
find . -name "*.txt"               # Find all .txt files in the current directory
find folder -maxdepth 1 -type -f   # Ensures that the search only looks in the specified folder (not subdirectories).
```
- **`locate` (Quick File Search)**
```bash
locate myfile.txt      # Find all locations of "myfile.txt"
locate -i myfile       # Case-insensitive search
locate *.jpg           # Find all .jpg files
**Faster** than `find`, but results (pre-built database) may be outdated unless you run:
sudo updatedb
```
- **`which` (Find Executable Paths)**
```bash
which python         # Find the path of "python"
which ls             # Find the path of "ls" command
which -a python      # Show all locations of "python"
```
- **`whereis` (Finds **binary, source, and manual pages** for a command)**
```bash
whereis python       # Find the binary, source, and manual page for "python"
whereis ls           # Find all locations related to "ls"
```

# 5. editing files and texts
## echo, cat, head, tail, >, >>, 2>&1, /dev/null
- **`echo` (Print Text)**
```bash
echo "Hello, World!"          # Print "Hello, World!" to the terminal
```
- **`cat` (Display or Concatenate Files)**
```bash
cat file.txt            # Show the contents of file.txt
cat file1.txt file2.txt > merged.txt  # Merge two files into one
```
- **`head` (Show First Few Lines of a File)**
```bash
head file.txt          # Show the first 10 lines
head -5 file.txt       # Show the first 5 lines
```
- **`tail` (Show Last Few Lines of a File)**
```bash
tail file.txt          # Show the last 10 lines
tail -5 file.txt       # Show the last 5 lines
tail -f logfile.txt    # Continuously display new lines (useful for logs)
```
- **`>` (Overwrite File Output)**
```bash
echo "Hello" > file.txt  # Overwrites file.txt with "Hello"
```
- **`>>` (Append Output to a File)**
```bash
echo "New line" >> file.txt  # Adds "New line" to the end of file.txt
```
- **`2>&1` (Redirect Standard Error to Standard Output)**
```
**Saves both normal output and errors into `output.txt`.**
ls non_existing_file > output.txt 2>&1
```
- **`/dev/null` (The "Black Hole" of Linux, a special file that discards anything written to it.)**
```
command > /dev/null      # Suppress standard output 
```
## touch, diff
- **`touch` (Create or Update Files)**
```bash
touch newfile.txt       # Create a new empty file
touch file.txt          # Update file’s last modified timestamp
```
- **`diff` (Compare Files Line by Line)**
```bash
diff file1.txt file2.txt  # Compare two files
diff -y file1.txt file2.txt  # Side-by-side comparison
```
## |, wc, grep
- **`grep` (Search for Text in Files)**
```bash
grep "error" logfile.txt      # Search for "error" in logfile.txt
grep -r "keyword" /var/logs   # Recursive search in a directory
grep -r "keyword"             # Recursive search in current directory
ls | grep "keyword"           # Find files containing "keyword" in their name
cat logfile.txt | grep "error" # Find lines containing "error"
```
- **`wc` (Word, Line, Character Count)**
```bash
wc file.txt         # Show line, word, and character count
wc -l file.txt      # Count lines
wc -w file.txt      # Count words
wc -c file.txt      # Count characters
ls | wc -l          # Count the number of files in the current directory
cat file.txt | wc -l # Count lines in a file
```
## vim, i, Esc, w, q, wq, !, shift+g, gg, dd, u, /word, n, N
- **Vim text editor and its Shortcuts**
- **Basic Vim Commands**

| Command | Description |
|---------|------------|
| `vim filename` | Open a file in Vim |
| `i` | Enter **Insert mode** (start typing) |
| `Esc` | Exit Insert mode |
| `w` | Save file (use `:w`) |
| `q` | Quit (use `:q`) |
| `q!` | Quit **without saving** (`:q!`) |
| `wq` | Save and quit (`:wq` or `ZZ`) |

- **Navigation**

| Command | Description |
|---------|------------|
| `Shift+G` | Jump to the **last line** of the file |
| `gg` | Jump to the **first line** |
| `dd` | Delete the current line |
| `u` | Undo last action |
| `/word` | Search for "word" in the file |
| `n` | Jump to the **next** search result |
| `N` | Jump to the **previous** search result |

# 6. memory and storage
## df, du, free
- **`du` (Disk Usage - Show Folder/File Size)**
```bash
du /home/user        # default unit: 512-byte blocks
16	./.git/objects/pack
...

du -h /home/user     # Human-readable (MB, GB instead of bytes).
8.0K	./.git/objects/pack
...

du -s /home/user     # Summary (only show total size).
352 /home/user

du -sh /home/user    
176K /home/user
```
- **`df` (Disk Free - Show Disk Space)**
```bash
df
Filesystem     512-blocks      Used Available Capacity iused     ifree %iused  Mounted on
/dev/disk1s5s1  236568496  45607192  52790936    47%  502161 263954680    0%   /
...

df -h     # Human-readable (MB, GB).
Filesystem       Size   Used  Avail Capacity iused     ifree %iused  Mounted on
/dev/disk1s5s1  113Gi   22Gi   25Gi    47%  502161 263946240    0%   /
...

df -h /home      # Show disk space for a specific partition
```
- **`free` (Show RAM & Swap Memory Usage)**
```bash
free
free -h      # Human-readable (MB, GB).
             total   used   free  shared  buff/cache  available
Mem:          16G    10G    2G     1G        4G          5G
Swap:          2G   512M   1.5G
- **`total`** → Total RAM.
- **`used`** → RAM currently in use.
- **`free`** → Completely unused RAM.
- **`available`** → Usable memory for new applications.

watch free -h   # Show memory usage every 2 seconds
```

# 7. cpu and process
## pgrep, ps, top, htop
```bash
$ ps
  PID TTY          TIME CMD
 1234 pts/0    00:00:00 bash
 5678 pts/0    00:00:00 ps
```
```bash
$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 systemd
    2 ?        00:00:00 kthreadd
   54 ?        00:00:00 kworker/0:1
 1023 ?        00:00:04 Xorg
 2345 ?        00:12:34 gnome-shell
 6789 pts/1    00:00:00 bash
 7890 pts/1    00:00:00 ps
```
```bash
$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1 225568  5124 ?        Ss   10:00   0:01 /sbin/init
root       102  0.1  0.3  85632 15240 ?        Ss   10:00   0:05 /usr/lib/systemd/systemd-journald
user      2345  1.2  2.5 156700 90500 ?        Sl   10:01   5:12 /usr/bin/firefox
user      3456  0.3  1.0  98740 40320 pts/1    S    10:10   0:45 gnome-terminal
user      6789  0.0  0.0   6328  2168 pts/1    Ss   10:20   0:00 bash
user      7890  0.0  0.0   6252  1260 pts/1    R+   10:25   0:00 ps aux
```
- `aux` options explained:
  - `a` → Show processes for all users.
  - `u` → Display user-oriented format (user, memory, and CPU usage).
  - `x` → Include processes **without a terminal (TTY)**.
- Important columns:
  - **USER** → Process owner.
  - **PID** → Process ID.
  - **%CPU** → CPU usage percentage.
  - **%MEM** → Memory usage percentage.
  - **VSZ** → Virtual memory size.
  - **RSS** → Resident memory size.
  - **TTY** → Terminal associated (or `?` for system processes).
  - **STAT** → Process state (`S` = sleeping, `R` = running, etc.).
  - **START** → Start time.
  - **TIME** → Total CPU time.
  - **COMMAND** → Command used to start the process.

| Command  | Shows Own Processes? | Shows System-Wide? | Detailed Info? |
|----------|----------------------|--------------------|----------------|
| `ps`     | ✅ Yes | ❌ No  | ❌ No  |
| `ps -A`  | ✅ Yes | ✅ Yes | ❌ No  |
| `ps aux` | ✅ Yes | ✅ Yes | ✅ Yes |

- top vs. htop
  - <img width="519" alt="圖片" src="https://github.com/user-attachments/assets/2e5c2b78-29f9-4e00-8740-da8dbc345dc6">

- `pgrep` (Process Grep)
```
pgrep firefox
# output
2345
5678
```

## ctrl+z, jobs, bg, fg, screen
- **`Ctrl+Z` (Suspend a Running Process)**
```
nano myfile.txt
# While `nano` is running, press:
Ctrl + Z   # Sends a SIGTSTP (stop signal) to pause a running process.
# Output:
[1]+  Stopped  nano myfile.txt
```

- **`jobs` (List All Suspended and Background Jobs in the current shell)**
```bash
jobs
# Output:
[1]+  Stopped  nano myfile.txt
```
- **`bg` (Resume a Suspended Job in the Background)**
```bash
bg %1
# Output:
[1]+ nano myfile.txt &
```
- **`fg` (Bring a Background Job to the Foreground)**
```bash
fg %1
# Output:
nano myfile.txt
```
- **`screen` (Persistent Terminal Sessions)**
```bash
screen -S mysession # Start a new screen session
Ctrl + A, then D    # Detach from the session (leave it running)
screen -ls          # List active screen sessions
screen -r mysession # Reattach to a session
screen -X -S mysession quit # Kill a session
```
- **Use `Ctrl+Z` and `fg/bg`** for temporary process control.  
- **Use `screen`** for long-running tasks and remote sessions.

## kill, pkill, killall
- **`kill` (Terminate a Process by PID)**
```bash
kill 1234
kill -9 1234  # Force kill
```
- **`pkill` (Kill a Process by Name)**
```bash
pkill firefox
pkill -9 firefox   # Force kill
pkill -u username firefox  # Kill only processes belonging to a specific user
pkill -f "python my_script.py"  # Kill only processes with a matching command pattern
```
- **`killall` (Kill All Instances of a Program)**
```bash
killall firefox  # Terminates **all** `firefox` processes.
killall -9 firefox # Force kill
```
- **Comparison Table**

| Command | Kills by | Scope | Example |
|---------|---------|------|---------|
| `kill` | PID | Single process | `kill 1234` |
| `pkill` | Name | Multiple processes (pattern match) | `pkill firefox` |
| `killall` | Exact name | All matching processes | `killall firefox` |

- **Use `kill`** when you know the exact **PID**.  
- **Use `pkill`** when you want to kill a **process by name**.  
- **Use `killall`** when you want to kill **all processes of a program**.

## lsof
- **`lsof` (List Open Files)**
```
lsof
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
bash      1234 user   cwd    DIR  8,1    4096      12345 /home/user
firefox   2345 user   txt    REG  8,1  1240000    67890 /usr/bin/firefox
python    3456 user   mem    REG  8,1  102400     11223 /usr/lib/libpython3.8.so
```

# 8. kernel and system
## uname, lscpu, /proc/cpuinfo
- **`uname` (System Information)**
```bash
uname # Show basic system information:
Linux
uname -a # Show **detailed system info**
Linux myhostname 5.15.0-79-generic #88-Ubuntu SMP x86_64 GNU/Linux
```
- **`lscpu` (CPU Information)**
```bash
lscpu
# Output (example):
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              8
Thread(s) per core:  2
Core(s) per socket:  4
Vendor ID:           GenuineIntel
Model name:          Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
```
- `/proc/cpuinfo` (Raw CPU Details)**
```bash
cat /proc/cpuinfo
# Shows info about each CPU core:
processor   : 0
vendor_id   : GenuineIntel
model name  : Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
cpu MHz     : 2600.000
cache size  : 12288 KB
```
## /etc/passwd, passwd, useradd
- **`/etc/passwd` (User Accounts Database, lists all system users)
```bash
cat /etc/passwd
# Example output:
root:x:0:0:root:/root:/bin/bash
user:x:1000:1000:User,,,:/home/user:/bin/bash
# Format:
username:x:UID:GID:comment:home_directory:shell
```
- **`passwd` (Change User Password)**
```bash
passwd # Change **your own password**
sudo passwd username  # Change another user's password (**as root**)
```
- **`useradd` (Create a New User)**
```bash
# `-m` → Creates a home directory (`/home/newuser`)
sudo useradd -m newuser
```
## /etc/hosts
- **`/etc/hosts` (Static Hostname Mapping, maps hostnames to IP addresses)**
```bash
cat /etc/hosts
# Example:
127.0.0.1   localhost
192.168.1.10 myserver.local
```
## systemctl
- **`systemctl` (Manage System Services)**
```bash
systemctl status apache2 # Check the status of a service
sudo systemctl start apache2 # Start a service
sudo systemctl stop apache2 # Stop a service
sudo systemctl enable apache2 # Enable a service to start on boot
sudo systemctl disable apache2 # Disable a service
systemctl list-units --type=service --state=running   # View all active services
```
## strace
- **`strace` (System Call Debugging Tool)**
```bash
strace -c ls   # Trace a command with summary
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 50.00    0.000015           3         5           read
 30.00    0.000009           1         9           write
 20.00    0.000006           2         3           openat

strace -p 1234  # Trace a running process (PID 1234)
strace ./my_program # Trace a program
```
## /var/log/syslog
- **`/var/log/syslog` (System Logs)**
```bash
sudo tail -f /var/log/syslog  # View the latest system logs
```

# 9. device and disk
## lsusb, dmesg, /dev/tty*
- **`lsusb` (List USB Devices)**
```bash
lsusb
  Bus 002 Device 003: ID 0781:5583 SanDisk Corp. Ultra Fit
  Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
lsusb -v  # verbose
```
- **`dmesg` (Kernel Message Buffer, Displays system logs and hardware events)**
```bash
dmesg
dmesg | grep -i usb
dmesg -w    # **Watch live logs** as new messages appear.
```
- **`/dev/tty*` (Terminal Devices)**
```bash
ls /dev/tty*
- `/dev/tty` → Current terminal.
- `/dev/ttyUSB0`, `/dev/ttyS0` → **USB serial ports**.
```
## mount, unmount, /etc/fstab
- **`mount` (Attach Storage Devices, makes them accessible)**
```bash
sudo mount /dev/sdb1 /mnt/usb
- `/dev/sdb1` → The partition to mount.
- `/mnt/usb` → The **mount point** (directory).
mount      # View all mounted file systems
sudo mount -o ro /dev/sdb1 /mnt/usb    # Mount with read-only mode
```
- **`umount` (Unmount Storage Devices, Safely ejects a mounted file system)**
```bash
sudo umount /mnt/usb
sudo umount -l /mnt/usb     # Lazy unmount, Force unmount (if busy), detaches but finishes pending processes
```
- **`/etc/fstab` (Persistent Mount Configuration, Stores automount settings for file systems)**
```bash
cat /etc/fstab
  UUID=1234-ABCD  /mnt/usb  vfat  defaults  0  0
  /dev/sda1  /     ext4   defaults  0  1
- **UUID** → Unique disk identifier.
- **File system types:** `ext4`, `vfat`, `ntfs`, etc.
- **Options:** `defaults`, `ro` (read-only), `noexec` (no execution).

sudo mount -a  # Mount all entries in `/etc/fstab
```
## lsblk, fdisk
- **`fdisk` (Partition Management)**
```bash
sudo fdisk -l        # List all disks and partitions
sudo fdisk /dev/sdb  # Edit a disk partition table
```

| Command | Action |
|---------|--------|
| `p` | Print partition table |
| `n` | Create a new partition |
| `d` | Delete a partition |
| `w` | Write changes and exit |
| `q` | Quit without saving |

- **`lsblk` (List Block Devices)**
```bash
lsblk
  NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
  sda      8:0    0  500G  0 disk
  ├─sda1   8:1    0  100G  0 part /
  ├─sda2   8:2    0  400G  0 part /home
  sdb      8:16   1   32G  0 disk
  └─sdb1   8:17   1   32G  0 part /mnt/usb
```

# 10. package management
## apt install remove purge list, dpkg
- **`apt` (Package Management for Debian/Ubuntu)**
```bash
sudo apt install package-name    # Install a package
sudo apt remove package-name     # Remove a package (keep config files)
sudo apt purge package-name      # Completely remove a package and deletes all configuration files
apt list --installed             # List installed packages
sudo apt update                  # Update package lists (but doesn't install anything)
sudo apt upgrade                 # Upgrade all installed packages
```
- **`dpkg` (Low-Level Package Management, works with `.deb` files directly.)**
```bash
sudo dpkg -i package.deb         # Install a `.deb` package
sudo dpkg -r package-name        # Remove a package
dpkg -l                          # List installed packages
```

# 11. permission 
## su, sudo
- **`su` (Switch User)**
```bash
# Requires root's password
su           # **Example: Switch to root user**
su username  # **Example: Switch to another user**
su -         # **Example: Switch to root and start a login shell**
```
- **`sudo` (Run Commands as Root)**
```bash
# Requires **your own password** (not root's password)
sudo command           # **Example: Run a command as root**
sudo -u user2 command  # **Example: Run a command as another user**
```
## chown, chmod
- **`chown` (Change File Owner)**
```bash
sudo chown user1 file.txt            # Makes `user1` the **owner** of `file.txt`.
sudo chown user1:group1 file.txt     # Assigns **`user1` as the owner** and **`group1` as the group**.
sudo chown -R user1:group1 /var/www  # `-R` (Recursive) → Changes ownership for all **subfiles and subdirectories**.
```
- **`chmod` (Change File Permissions)**
```bash
chmod 700 file.txt  # **Example: Give the owner full permissions**
chmod +x script.sh  # **Example: Make a script executable**
```

| Who? | Add | Remove | Set |
|------|-----|--------|-----|
| Owner (`u`) | `chmod u+x file` | `chmod u-w file` | `chmod u=rwx file` |
| Group (`g`) | `chmod g+r file` | `chmod g-x file` | `chmod g=rw file` |
| Others (`o`) | `chmod o+w file` | `chmod o-r file` | `chmod o=r file` |

# 12. history, shell and env var
## history, export, alias, VAR=OOXX, $VAR, .bashrc, .bash_history, bash
- `history` (Command History)
```
history # Lists previously executed commands.
!123    # Runs command number 123 from the history list.
```
- `export` (Set Environment Variables)
```
export MYVAR="Hello"  # Set and Export a Variable
printenv MYVAR        # Check If a Variable is Exported
echo $MYVAR           # Check If a Variable is Exported
echo 'export MYVAR="Hello"' >> ~/.bashrc  # Make a Variable Persistent (Across Reboots)
```
- `alias` (Create Command Shortcuts)
```
alias ll='ls -lah'
```
- Define a Variable
```
MYVAR="Hello"
```
- Access a Variable
```
echo $MYVAR
```
- `.bashrc` (User Shell Configuration), located at: ~/.bashrc
```
source ~/.bashrc     #Apply Changes Without Restarting
```
- `.bash_history` (Command History File), located at: ~/.bash_history
```
tail -10 ~/.bash_history     #View the Last 10 Commands
```
- `bash` (Start a New Shell)
```
bash   # Launch a New Bash Shell
exit   # Exit the Bash Shell
```

# 13. compression
## tar -cvf/-xvf -zcvf/-zxvf
- `tar` (Tape Archive)
```
# Archive .tar (No Compression)
tar -cvf archive.tar file1 file2 directory/
tar -xvf archive.tar

#c → Create an archive
#v → Verbose (show files being archived)
#f → File name
#x → Extract files
```
```
# Compressed .tar.gz Archive
tar -czvf archive.tar.gz file1 file2 directory/
tar -xzvf archive.tar.gz

#z → Compress using gzip
```

## zip/unzip
- `zip` (ZIP Archive, Windows-compatible)
```
# Archive + Compress .zip
zip archive.zip file1 file2 directory/
unzip archive.zip
```

# 14. time
## uptime, date
- `uptime` (Show System Uptime)
```
uptime
10:35:42 up 5 days, 3:12,  2 users,  load average: 0.23, 0.14, 0.09
uptime -p   # human-readable forma
up 5 days, 3 hours, 12 minutes
uptime -s   # Check system startup time
2024-02-01 07:23:12
```
- `date` (Show Current System Date & Time) 
```
date
Mon Feb 7 10:35:42 UTC 2025
date +"%Y-%m-%d"
10:35:42
date +%s  # Current Unix Timestamp # This is the number of seconds since January 1, 1970 (epoch time).
1707316542
```


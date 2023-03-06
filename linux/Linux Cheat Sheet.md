# Linux Cheat Sheet

![Linux Cheat Sheet](https://simplecheatsheet.com/wp-content/uploads/2020/07/Colorful-Pop-Tutorial-Youtube-Thumbnail-10.png)

This **cheat sheet** will help you using Linux**. Linux** is the best-known and most-used open-source operating system. As an operating system, Linux is software that sits underneath all of the other software on a computer, receiving requests from those programs and relaying these requests to the computer’s hardware.

## [Linux: System and Hardware Cheat Sheet](https://simplecheatsheet.com/linux-system-and-hardware/)

\# Display Linux system information

```
uname -a
```

\# Display kernel release information

```
uname -r
```

\# Display the linux kernel name

```
uname -s
```

\# Get the linux kernel version

```
uname -v
```

\# Get network node hostname

```
uname -n
```

\# Get machine hardware architecture (i386, x86_64, etc.)

```
uname --m
```

\# Get processor type

```
uname -p
```

\# Get hardware platform

```
uname -i
```

\# Get operating system information

```
uname -o
```

\# Show which version of redhat installed

```
cat /etc/redhat-release
```

\# Show how long the system has been running + load

```
uptime
```

\# Show system host name

```
hostname
```

\# Display the IP addresses of the host

```
hostname -I
```

\# Show system reboot history

```
last reboot
```

\# Show the current date and time

```
date
```

\# Show this month’s calendar

```
cal
```

\# Display who is online

```
w
```

\# Who you are logged in as

```
whoami
```

\# Get Hardware information

```
sudo lshw
```

\# View the summary of your detailed hardware profile

```
lshw -short
```

\# Print your hardware profile to an HTML file as a superuser

```
sudo lshw -html > [filename.html]
```

\# Get CPU information

```
lscpu
```

\# Get block device information

```
lsblk
```

\# View much more detailed information about all the devices

```
lsblk -a
```

## [Linux: Bash Cheat Sheet](https://simplecheatsheet.com/linux-bash-shortcuts/)

##### # ALT Key

| `ALT+A`  | Go to the beginning of a line.                               |
| -------- | ------------------------------------------------------------ |
| `ALT+B`  | Move one character before the cursor.                        |
| `ALT+C`  | Suspends the running command/process.                        |
| `ALT+D`  | Closes the empty Terminal (I.e it closes the Terminal when there is nothing typed). It also deletes all characters after the cursor. |
| `ALT+F`  | Move forward one character.                                  |
| `ALT+T ` | Swaps the last two words.                                    |
| `ALT+U`  | Capitalize all characters in a word after the cursor.        |
| `ALT+L ` | Uncapitalize all characters in a word after the cursor.      |
| `ALT+R`  | Undo any changes to a command that you have brought from the history if you’ve edited it. |

##### # CTRL Key

| `CTRL+A`  | Quickly move to the beginning of the line.                   |
| --------- | ------------------------------------------------------------ |
| `CTRL+B`  | To move backward one character.                              |
| `CTRL+C`  | Stop the currently running command.                          |
| `CTRL+D`  | Delete one character backward.                               |
| `CTRL+E`  | Move to the end of the line.                                 |
| `CTRL+F ` | Move forward one character.                                  |
| `CTRL+G`  | Leave the history searching mode without running the command. |
| `CTRL+H`  | Delete the characters before the cursor, the same as Backspace. |
| `CTRL+J`  | Same as Enter/ Return key.                                   |
| `CTRL+K`  | Delete all characters after the cursor.                      |
| `CTRL+L`  | Clears the screen and redisplay the line.                    |
| `CTRL+M`  | Same as CTRL+J or RETURN.                                    |
| `CTRL+N`  | Display the next line in the command history.                |
| `CTRL+O`  | Run the command that you found using reverse search i.e CTRL+R. |
| `CTRL+P`  | Displays the previous line in the command history.           |
| `CTRL+R`  | Searches the history backward (Reverse search).              |
| `CTRL+S`  | Searches the history forward.                                |
| `CTRL+T`  | Swaps the last two characters.                               |
| `CTRL+U`  | Delete all characters before the cursor (Kills backward from point to the beginning of the line). |
| `CTRL+V`  | Makes the next character typed verbatim.                     |
| `CTRL+W`  | Delete the words before the cursor.                          |
| `CTRL+X`  | Lists the possible filename completions of the current word. |
| `CTRL+XX` | Move between the start of the command line and the current cursor position (and back again). |
| `CTRL+Y`  | Retrieves the last item that you deleted or cut.             |
| `CTRL+Z`  | Stops the current command.                                   |
| `CTRL+[`  | Equivalent to ESC key.                                       |

##### # Miscellaneous

| `!!`            | Repeat last command                                       |
| --------------- | --------------------------------------------------------- |
| `!name`         | Run the last command starting with ‘name’                 |
| `!name:p`       | Print the last command starting with ‘name’               |
| `!$`            | Last argument of the previous command                     |
| `ALT-.`         | Last argument of the previous command                     |
| `!*`            | All arguments of the previous command                     |
| `^name^another` | Run the previous command, replacing ‘name’ with ‘another’ |

## [Linux: Bash Variables Cheat Sheet](https://simplecheatsheet.com/linux-bash-variables/)

\# Show enviro­nment variables

```
env
```

\# Output value of $NAME variable

```
echo $NAME
```

\# Set $NAME to value

```
export NAME=value
```

\# Executable search path

```
$PATH
```

\# Home directory

```
$HOME
```

\# Current shell

```
$SHELL
```

## [Linux: ls Command Options Cheat Sheet](https://simplecheatsheet.com/linux-ls-command-options/)

\# List all files including hidden file

```
ls -a
```

\# Recursive list

```
ls -R
```

\# Reverse order

```
ls -r
```

\# Colored list [=always/never/auto]

```
ls --color
```

\# List directories – with ‘ */’

```
ls -d
```

\# Add one char of */=>@| to enteries

```
ls -F
```

\# List file’s inode index number

```
ls -i
```

\# Sort by last modified

```
ls -t
```

\# Sort by file size

```
ls -S
```

\# List file size

```
ls -s
```

\# List with long format – show permissions

```
ls -l
```

\# List long format including hidden files

```
ls -la
```

\# List long format with readable file size

```
ls -lh
```

\# List with long format with file size

```
ls -ls
```

\# One file per line

```
ls -1
```

\# Comma-­sep­arated output

```
ls -m
```

\# Quoted output

```
ls -Q
```

\# Sort by extension name

```
ls -X
```

## [Check hardware information on Linux](https://simplecheatsheet.com/check-hardware-information-on-linux/)

\# Display messages in kernel ring buffer

```
dmesg
```

\# Reports information about the cpu and processing units

```
lscpu
```

\# Extracts the information from different /proc files

```
lshw -short
```

\# Report detailed and brief information about multiple different hardware components

```
hwinfo --short
```

\# Lists out all the PCI buses and details about the devices connected to them

```
lspci 
```

\# Display USB devices

```
lsusb 
```

\# Lists out the scsi/sata devices like hard drives and optical drives

```
lsscsi
```

\# Display CPU information

```
cat /proc/cpuinfo
```

\# Display memory information

```
cat /proc/meminfo
```

\# Display DMI/SMBIOS (hardware info) from the BIOS

```
dmidecode
```

\# Show info about disk sda

```
hdparm -i /dev/sda
```

\# Perform a read speed test on disk sda

```
hdparm -tT /dev/sda
```

\# Test for unreadable blocks on disk sda

```
badblocks -s /dev/sda
```

\# List out information all block devices

```
lsblk
```

\# Reports various partitions, their mount points and the used and available space on each

```
df -H
```

\# Mount/unmount and view mounted file systems

```
mount | column -t
```

\# Filter out only those file systems that you want to see

```
mount | column -t | grep ext
```

\# Check the amount of used, free and total amount of RAM on system with the free command.

```
free -m
```

\# Gets information about sata devices like hard disks

```
sudo hdparm -i /dev/sda
```

\# CPU information

```
 cat /proc/cpuinfo
```

\# Memory information

```
cat /proc/meminfo
```

\# Linux/kernel information

```
cat /proc/version
```

## [Linux: Performance Cheat Sheet](https://simplecheatsheet.com/linux-performance/)

\# Display and manage the top processes

```
top
```

\# Display virtual memory statistics

```
vmstat 1
```

\# Display processor related statistics

```
mpstat 1
```

\# Display I/O statistics

```
iostat 1
```

\# List all open files

```
lsof
```

\# List files opened by user

```
lsof -u user
```

\# Capture and display all packets on interface eth0

```
tcpdump -i eth0
```

\# Monitor all traffic on port 80 ( HTTP )

```
tcpdump -i eth0 'port 80'
```

\# Monitoring incoming and outgoing network packets statistics as well as interface statistics

```
netstat -a | more
```

\# Finding the exact process and high used disk read/writes of the processes

```
iotop
```

\# Display free and used memory ( -h for human-readable, -m for MB, -g for GB)

```
free -h
```

\# Execute “df -h”, showing periodic updates

```
watch df -h
```

## [Linux: User Account Infomation Cheat Sheet](https://simplecheatsheet.com/linux-user-account-infomation/)

\# Display the user and group ids of your current user

```
id
```

\# Display the last users who have logged onto the system

```
last
```

\# To show all the users who were present at a specified time

```
last -ap now
```

\# Find the details of a recent login of all users or of a given user as follows

```
lastlog
```

\# Show who is logged into the system

```
who
```

\# Show who is logged in and what they are doing

```
w
```

\# Create a group named “groupname”

```
groupadd groupname
```

\# Create an account named kim, with a comment of “Kim Kardashian” and create the user’s home directory

```
useradd -c "Kim Kardashian" -m kim
```

\# Add the kim account to the sales group

```
usermod -aG sales kim
```

\# Delete the kim account

```
userdel john
```

## [Linux: Networking Cheat Sheet](https://simplecheatsheet.com/linux-networking/)

\# Display all network interfaces and ip address

```
ifconfig -a
```

\# Display eth0 address and details

```
ifconfig eth0
```

\# Query or control network driver and hardware settings

```
ethtool eth0
```

\# Print kernel module info

```
ethtool -i eth0
```

\# Print eth0 traffic statistics

```
ethtool -S eth0
```

\# Print RX, TX and auto-negotiation settings

```
ethtool -a eth0 
```

\# Blink LED

```
ethtool -p eth0 
```

\# Display whois information for domain

```
whois domain
```

\# Send ICMP echo request to host

```
ping host
```

\# Network Connec­tions

```
watch ss -tp
```

\# Display listening tcp and udp ports and corresponding programs

```
netstat -nutlp
```

\# TCP connec­tions

```
netstat -ant
```

\# UDP Connec­tions

```
netstat -anu
```

\# Connec­tions with PIDs

```
netstat -tulpn
```

\# Display DNS information for domain

```
dig domain
```

\# Display DNS ip address for domain

```
host domain
```

\# Display the network address of the host name

```
hostname -i
```

\# Display all local ip addresses

```
hostname -I
```

\# Download file http://domain.com/filename

```
wget http://domain.com/filename
```

## [Linux: Tar Files Cheat Sheet](https://simplecheatsheet.com/linux-tar-files/)

\# Create tar named archive.tar containing directory

```
tar cf archive.tar directory
```

\# Extract the contents from archive.tar

```
tar xf archive.tar
```

\# Create a gzip compressed tar file name archive.tar.gz

```
tar czf archive.tar.gz directory
```

\# Extract a gzip compressed tar file

```
tar xzf archive.tar.gz
```

\# Create a tar file with bzip2 compression

```
tar cjf archive.tar.bz2 directory
```

\# Extract a bzip2 compressed tar file

```
tar xjf archive.tar.bz2
```

\# List content of tar file

```
tar -tvf archive.tar
```

## [Linux: Install Packages Cheat Sheet](https://simplecheatsheet.com/linux-install-packages/)

\# Search for a package by keyword

```
yum search keyword
```

\# Install a Package with YUM

```
yum -y install packetname
```

\# Remove/Uninstall a Package with YUM

```
yum -y remove packetname
```

\# Display description and summary information about package

```
yum info package
```

\# Updating a Package

```
yum update packetname
```

\# List a Package

```
yum list packetname
```

\# Install package from local file named package.rpm

```
rpm -i package.rpm
```

\# List all available packages

```
yum list | less
```

\# List all installed packages

```
yum list installed | less
```



## [Linux: SSH Command Cheat Sheet](https://simplecheatsheet.com/linux-ssh-command/)

\# Connect to host as your local username

```
ssh host
```

\# Connect to host as user

```
ssh user@host
```

\# Connect to host using port

```
ssh -p port user@host
```

\# Generating public-private keys

```
ssh-keygen
```

\# Create a key pair

```
ssh-keygen -t rsa
```

\# Copy Public SSH Key

```
ssh-copy-id hostname_or_IP
```

\# Edit SSH Config File

```
sudo vim /etc/ssh/sshd_config
```

\# Restart SSH service

```
sudo ssh service restart
```

## [Linux: Disk Space Cheat Sheet](https://simplecheatsheet.com/linux-disk-space-command/)

\# Show free and used space on mounted filesystems

```
df -h
```

\# Show free and used inodes on mounted filesystems

```
df -i
```

\# Shows the file system’s complete disk usage even if the Available field is 0

```
df -a
```

\# Display disks partitions sizes and types

```
fdisk -l
```

\# Display disk usage for all files and directories in human readable format

```
du -ah
```

\# Display total disk usage off the current directory

```
du -sh
```

\# Shows the disk usage along with each block’s filesystem type (e.g., xfs, ext2, etc.)

```
df -T
```

## [Linux: Directory Operations Cheat Sheet](https://simplecheatsheet.com/linux-directory-operations/)

\# Go up a directory

```
cd ..
```

\# Go to the $HOME directory

```
cd
```

\# Change to the /etc directory

```
cd /etc
```

\# Show current directory

```
pwd
```

\# Make directory dir

```
mkdir dir
```

\# List files

```
ls
```

## [Linux: Search Cheat Sheet](https://simplecheatsheet.com/linux-search/)

\# Find files and directories by name

```
locate name
```

\# Search for pattern in file

```
grep pattern file
```

\# Search recursively for pattern in directory

```
grep -r pattern directory
```

\# Find files in /home/ that start with “filename”.

```
find /home/owner -name filename*
```

\# Find files owner by “filename” in /home/

```
find /home/ -user filename
```

\# Find files modifed less than “number” minutes ago in home

```
find /home/ -mmin number
```

\# Search files larger than 100MB in /home

```
find /home -size +100M
```

\# Search for pattern in files

```
grep pattern files
```

\# Case insens­itive search

```
grep -i
```

\# Recursive search

```
grep -r
```

\# Inverted search

```
grep -v
```

\# Show matched part of file only

```
grep -o
```

\# Find binary / source / manual for command

```
whereis command
```

## [Linux: Process Management Cheat Sheet](https://simplecheatsheet.com/linux-process-management/)

\# Show your currently running processes

```
ps
```

\# Show all the currently running processes on the system.

```
ps -ef
```

\# Show process information for processname

```
ps -ef | grep processname
```

\# Show real time processes

```
top
```

\# Interactive process viewer (top alternative)

```
htop
```

\# Kill process with id pid

```
kill pid
```

\# Kill all processes named processname

```
killall processname
```

\# Kill process with name processname

```
pkill processname
```

\# Start program in the background

```
program &
```

\# Display stopped or background jobs

```
bg
```

\# Brings the most recent background job to foreground

```
fg
```

\# Brings job n to the foreground

```
fg n
```

## [Linux: File Operations Cheat Sheet](https://simplecheatsheet.com/linux-file-operations/)

\# List all files in a long listing (detailed) format

```
ls -al
```

\# Display the present working directory

```
pwd
```

\# Create a directory

```
mkdir directory
```

\# Create file1

```
touch file1
```

\# Concat­enate files and output

```
cat file1 file2
```

\# View and paginate file1

```
less file1
```

\# Get type of file1

```
file file1
```

\# Remove/ delete file

```
rm file
```

\# Remove the directory and its contents recursively

```
rm -r directory
```

\# Force removal of file without prompting for confirmation

```
rm -f file
```

\# Forcefully remove directory recursively

```
rm -rf directory
```

\# Copy file1 to file2

```
cp file1 file2
```

\# Rename or move file1 to file2

```
mv file1 file2
```

\# Create symbolic link to linkname

```
ln -s /path/to/file linkname
```

\# Create an empty file or update the access and modification times of file1.

```
touch file1
```

\# Show first 10 lines of file1

```
head file1
```

\# Show last 10 lines of file1

```
tail file1
```

\# Output last lines of file1 as it changes

```
tail -F file1
```

## [Linux: File Permis­sions Cheat Sheet](https://simplecheatsheet.com/linux-file-permissions/)

\# Change mode of *file* to 775

```
chmod 775 file
```

\# Recurs­ively chmod *folder* to 600

```
chmod -R 600 folder
```

\# Change *file* owner to *user* and group to *group*

```
chown user:group file
```



## [Linux: File Transfers Cheat Sheet](https://simplecheatsheet.com/linux-file-transfers/)

\# Copy *.html files from server to the local /tmp folder.

```
scp server:/var/www/*.html /tmp
```

\# Secure copy file.txt to the /tmp folder on server

```
scp file.txt server:/tmp
```

\# Copy all files and directories recursively from server to the current system’s /tmp folder.

```
scp -r server:/var/www /tmp
```

\# Synchronize /home to /backups/home

```
rsync -a /home /backups/
```

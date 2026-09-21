# HTB Academy - Linux Fundamentals

Notes and commands from the Hack The Box Linux Fundamentals module.

---

# Section 1 - Linux Structure

## What is Linux?

Linux is an open-source operating system widely used in:

- Servers
- Cloud environments
- Desktop systems
- Embedded devices
- Cybersecurity

Linux comes in many different versions called **distributions (distros)**.

## Linux Architecture

Linux can be understood in layers:

- **Hardware** - CPU, RAM, disks and other physical devices.
- **Kernel** - Core of the operating system. Manages hardware, memory, processes and resources.
- **Shell** - Interface used to interact with the operating system through commands.
- **System Utilities** - Programs that provide additional OS functionality.

## Linux Philosophy

Important Linux principles:

- Everything is treated as a file.
- Programs should perform one task well.
- Small programs can be chained together.
- The shell gives powerful control over the system.
- Configuration is commonly stored in text files.

## Important Linux Components

- **Bootloader** - Starts the operating system.
- **Kernel** - Manages hardware and system resources.
- **Daemons** - Background services.
- **Shell** - Command interpreter.
- **Graphics Server** - Provides graphical functionality.
- **Window Manager / GUI** - Graphical desktop environment.
- **Utilities** - Programs that perform specific tasks.

## Linux Filesystem

Linux uses a tree-like filesystem.

Important directories:

- `/` - Root of the entire filesystem.
- `/bin` - Essential command binaries.
- `/boot` - Bootloader and kernel files.
- `/dev` - Device files.
- `/etc` - System configuration files.
- `/home` - User home directories.
- `/lib` - Shared libraries.
- `/media` - Removable devices.
- `/mnt` - Temporary filesystem mounts.
- `/opt` - Optional or third-party software.
- `/root` - Root user's home directory.
- `/sbin` - System administration binaries.
- `/tmp` - Temporary files.
- `/usr` - Applications, libraries and documentation.
- `/var` - Logs and other variable data.

---

# Section 2 - Linux Distributions

A Linux distribution combines the Linux kernel with different:

- Packages
- Tools
- Configurations
- User interfaces

Common distributions include:

- Ubuntu
- Debian
- Fedora
- CentOS
- Red Hat Enterprise Linux
- Kali Linux
- Parrot OS

## Cybersecurity Distributions

Popular security-oriented distributions include:

- Kali Linux
- Parrot OS
- BlackArch
- BackBox
- Pentoo

## Debian

Debian is known for:

- Stability
- Reliability
- Security
- Long-term support
- Flexibility

Debian uses the `apt` package manager.

Example:

```bash
sudo apt update
```

---

# Section 3 - Introduction to Shell

## Terminal vs Shell

The **terminal** is the interface used to communicate with the shell.

The **shell** interprets commands and communicates with the operating system.

A shell allows us to:

- Navigate directories
- Work with files
- Run programs
- Manage processes
- Gather system information
- Automate tasks with scripts

## Common Shells

- Bash
- Zsh
- Fish
- Ksh
- Tcsh / Csh

Bash stands for:

**Bourne-Again Shell**

and is one of the most commonly used Linux shells.

## Terminal Multiplexers

Tools such as `tmux` allow multiple terminal sessions or panes to run at the same time.

---

# Section 4 - Bash Prompt

A common Bash prompt looks like:

```text
username@hostname:directory$
```

Important symbols:

- `$` - Normal user
- `#` - Root / privileged user
- `~` - User's home directory

Example normal user:

```text
crissv@linux:~$
```

Example root user:

```text
root@linux:/#
```

## PS1

The `PS1` variable controls how the Bash prompt looks.

Useful values:

- `\u` - Username
- `\h` - Hostname
- `\H` - Full hostname
- `\w` - Current working directory
- `\t` - Current time
- `\d` - Date
- `\j` - Number of jobs

Bash prompt configuration is commonly stored in:

```text
~/.bashrc
```

---

# Section 5 - Getting Help

Knowing how to find information is more important than memorizing every option.

## Manual Pages

```bash
man <command>
```

Example:

```bash
man ls
```

Exit a man page with:

```text
q
```

## Command Help

```bash
<command> --help
```

Example:

```bash
ls --help
```

Some commands use:

```bash
<command> -h
```

Example:

```bash
curl -h
```

## Search Manual Descriptions

```bash
apropos <keyword>
```

Example:

```bash
apropos sudo
```

Useful external resource:

```text
https://explainshell.com/
```

---

# Section 6 - System Information

These commands are useful for understanding the Linux system we are currently working on.

## Current User

```bash
whoami
```

Shows the current username.

## User and Group Information

```bash
id
```

Shows:

- User ID
- Group ID
- Group memberships

Security-relevant groups may include:

- `sudo`
- `adm`

Membership in privileged groups can indicate additional permissions.

## Hostname

```bash
hostname
```

Displays the system hostname.

## Kernel and System Information

Basic information:

```bash
uname
```

All available information:

```bash
uname -a
```

Kernel release:

```bash
uname -r
```

The kernel version can be useful when researching known vulnerabilities or compatibility issues.

## Working Directory

```bash
pwd
```

Shows the current directory.

## Networking

```bash
ip
```

Used to inspect or configure:

- Interfaces
- IP addresses
- Routes
- Network devices

Older command:

```bash
ifconfig
```

Network status:

```bash
netstat
```

Sockets and network connections:

```bash
ss
```

## Processes

```bash
ps
```

Shows running processes.

## Logged-In Users

```bash
who
```

Shows users currently logged into the system.

## Environment Variables

```bash
env
```

Displays environment variables.

## Storage Devices

```bash
lsblk
```

Lists block devices such as disks and partitions.

## USB Devices

```bash
lsusb
```

Lists USB devices.

## Open Files

```bash
lsof
```

Lists open files.

## PCI Devices

```bash
lspci
```

Lists PCI hardware.

---

# SSH

SSH allows secure remote command-line access to another system.

Syntax:

```bash
ssh username@IP
```

Example:

```bash
ssh htb-student@10.10.10.10
```

SSH is commonly used to manage Linux servers remotely.

---

# Section 7 - Navigation

## Current Directory

```bash
pwd
```

Example output:

```text
/home/crissv
```

## List Files

```bash
ls
```

Detailed information:

```bash
ls -l
```

Show hidden files:

```bash
ls -la
```

Hidden files normally start with a dot:

```text
.bashrc
.bash_history
```

## List Another Directory

You do not need to enter a directory to inspect it.

```bash
ls -l /var/
```

## Change Directory

```bash
cd <directory>
```

Example:

```bash
cd /dev/shm
```

## Previous Directory

```bash
cd -
```

## Parent Directory

```bash
cd ..
```

## Home Directory

```bash
cd ~
```

or simply:

```bash
cd
```

## Special Directory References

- `.` - Current directory
- `..` - Parent directory
- `~` - Home directory

## Autocomplete

Press:

```text
TAB
```

If multiple possibilities exist, pressing TAB again can display the options.

## Clear Terminal

```bash
clear
```

Shortcut:

```text
Ctrl + L
```

## Command History

Previous / next commands:

```text
↑
↓
```

Search command history:

```text
Ctrl + R
```

## Run Multiple Commands

Commands can be chained.

Example:

```bash
cd /dev/shm && clear
```

`&&` runs the second command only if the first command succeeds.

---

# Section 8 - Working with Files and Directories

## Create an Empty File

```bash
touch <filename>
```

Example:

```bash
touch info.txt
```

## Create a Directory

```bash
mkdir <directory>
```

Example:

```bash
mkdir Storage
```

## Create Nested Directories

```bash
mkdir -p <path>
```

Example:

```bash
mkdir -p Storage/local/user/documents
```

The `-p` option automatically creates missing parent directories.

## View Directory Structure

```bash
tree .
```

## Create a File in Another Directory

```bash
touch ./Storage/local/user/userinfo.txt
```

The `.` means:

**start from the current directory.**

## Rename a File

The `mv` command can rename files.

```bash
mv oldname newname
```

Example:

```bash
mv info.txt information.txt
```

## Move a File

```bash
mv <file> <directory>
```

Example:

```bash
mv information.txt Storage/
```

## Move Multiple Files

```bash
mv file1.txt file2.txt Storage/
```

## Copy a File

```bash
cp <source> <destination>
```

Example:

```bash
cp Storage/readme.txt Storage/local/
```

---

# Quick Command Reference

## Help

```bash
man <command>
<command> --help
<command> -h
apropos <keyword>
```

## System Information

```bash
whoami
id
hostname
uname
uname -a
uname -r
pwd
ip
ifconfig
netstat
ss
ps
who
env
lsblk
lsusb
lsof
lspci
```

## Remote Access

```bash
ssh username@IP
```

## Navigation

```bash
pwd
ls
ls -l
ls -la
cd <directory>
cd ..
cd -
cd ~
clear
```

## Files and Directories

```bash
touch <file>
mkdir <directory>
mkdir -p <path>
tree .
mv <source> <destination>
cp <source> <destination>
```

## Useful Shortcuts

```text
TAB       Autocomplete
Ctrl + L  Clear terminal
Ctrl + R  Search command history
↑ / ↓     Browse command history
```

---

# Cybersecurity Relevance

These Linux fundamentals are important because they help with:

- System enumeration
- Privilege analysis
- Server administration
- Network troubleshooting
- Vulnerability assessment
- Penetration testing
- Incident investigation
- Remote access

Commands such as:

```bash
whoami
id
uname -a
uname -r
ip
ss
ps
lsof
```

are especially useful when trying to understand a Linux system during a security assessment.

---

# Progress

Completed notes:

- Section 1 - Linux Structure
- Section 2 - Linux Distributions
- Section 3 - Introduction to Shell
- Section 4 - Prompt Description
- Section 5 - Getting Help
- Section 6 - System Information
- Section 7 - Navigation
- Section 8 - Working with Files and Directories


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

# Section 9 - Editing Files

Linux files can be edited directly from the terminal using text editors such as Nano and Vim.

---

## Nano

Nano is a simple terminal text editor.

Open or create a file:

```bash
nano notes.txt
```

Useful shortcuts:

```text
Ctrl + W  Search
Ctrl + O  Save
Enter     Confirm filename
Ctrl + X  Exit
```

In Nano, `^` represents the `Ctrl` key.

View the contents of a file:

```bash
cat notes.txt
```

---

## Important Linux Files

### /etc/passwd

Contains information about system users, such as:

- Username
- UID
- GID
- Home directory

Password hashes are normally not stored here.

### /etc/shadow

Contains password hashes and normally has more restrictive permissions.

Misconfigured permissions on sensitive files can expose information and may contribute to privilege escalation.

---

## Vim / Neovim

Vim is a modal text editor.

Different keys perform different actions depending on the current mode.

### Main Modes

- **Normal Mode** - Execute commands.
- **Insert Mode** - Write text.
- **Visual Mode** - Select text.
- **Command Mode** - Execute commands beginning with `:`.
- **Replace Mode** - Replace existing text.

Enter Insert Mode:

```text
i
```

Return to Normal Mode:

```text
Esc
```

---

## Vim Movement

```text
h   Left
j   Down
k   Up
l   Right

0   Beginning of line
gg  Beginning of file
G   End of file
```

Jump to a specific line:

```text
10G
```

Example: `10G` jumps to line 10.

---

## Insert and Append

Insert text:

```text
i
```

Append text at the end of a line:

```text
A
```

Return to Normal Mode:

```text
Esc
```

---

## Delete

Delete current character:

```text
x
```

Delete one word:

```text
dw
```

Delete to the end of the line:

```text
d$
```

Delete one complete line:

```text
dd
```

Delete multiple lines:

```text
2dd
```

---

## Operators, Counts and Motions

Many Vim commands follow:

```text
operator + [count] + motion
```

Examples:

```text
dw    Delete one word
2w    Move two words forward
3e    Move to the end of the third word
d2w   Delete two words
```

This means Vim commands can be combined instead of memorized individually.

---

## Undo and Redo

Undo:

```text
u
```

Redo:

```text
Ctrl + R
```

---

## Put / Paste

Paste after the cursor:

```text
p
```

Paste before the cursor:

```text
P
```

For example:

```text
dd
p
```

can be used to remove a line and place it somewhere else.

---

## Replace

Replace the current character:

```text
r
```

Then type the replacement character.

---

## Change Operator

The `c` operator works similarly to delete, but enters Insert Mode afterward.

Change to the end of a word:

```text
ce
```

Change to the end of a line:

```text
c$
```

General pattern:

```text
c + [count] + motion
```

---

## Search

Search forward:

```vim
/text
```

Next result:

```text
n
```

Previous result:

```text
N
```

Search backward:

```vim
?text
```

---

## Matching Brackets

```text
%
```

Jumps between matching:

```text
( )
[ ]
{ }
```

This can be useful when reading code or scripts.

---

## Text Substitution

Replace one occurrence on the current line:

```vim
:s/old/new/
```

Replace all occurrences on the current line:

```vim
:s/old/new/g
```

---

## Save and Exit Vim

Save and quit:

```vim
:wq
```

Quit without saving:

```vim
:q!
```

During VimTutor in the HTB Pwnbox, `:wq` returned:

```text
E382: Cannot write, 'buftype' option is set
```

because VimTutor was running in a special buffer rather than a normal writable file.

---

## VimTutor

I used VimTutor to practice the commands instead of only reading about them.

I practiced:

- Movement
- Normal Mode
- Insert Mode
- Append
- Delete
- Operators and motions
- Counts
- Undo / redo
- Put
- Replace
- Change
- Search
- Navigation
- Matching brackets
- Basic substitution

The current goal is not to master Vim completely, but to become comfortable enough to use it during Linux administration and cybersecurity labs.

# Section 10 - Find Files and Directories

Finding files and directories is important in Linux administration and cybersecurity.

During a security assessment, it may be necessary to locate:

- Configuration files
- User-created scripts
- Sensitive files
- Installed tools
- Files owned by specific users
- Recently modified files

Linux provides several tools for this purpose.

---

## which

The `which` command shows the path of the executable that would run for a given command.

Syntax:

```bash
which <command>
```

Example:

```bash
which python
```

Example output:

```text
/usr/bin/python
```

This is useful for checking whether tools such as:

- Python
- curl
- wget
- netcat
- gcc

are installed and available.

If the program cannot be found, `which` normally returns no result.

---

## find

The `find` command searches for files and directories and supports many filters.

Basic syntax:

```bash
find <location> <options>
```

Example:

```bash
find / -type f -name "*.conf"
```

This searches from the root directory `/` for files ending in `.conf`.

---

## Useful find Options

### Search only for files

```bash
-type f
```

### Search by name

```bash
-name "*.conf"
```

The `*` wildcard means:

```text
any characters
```

So:

```text
*.conf
```

means any file ending in `.conf`.

### Search by owner

```bash
-user root
```

Searches for files owned by the `root` user.

### Search by size

```bash
-size +20k
```

Searches for files larger than 20 KiB.

### Search by modification date

```bash
-newermt 2020-03-03
```

Shows files modified after the specified date.

---

## Execute Commands on Results

The `-exec` option allows another command to run against each result.

Example:

```bash
-exec ls -al {} \;
```

Important parts:

```text
{}   Placeholder for each file found
\;   Marks the end of the command executed by find
```

Example:

```bash
find / -type f -name "*.conf" -exec ls -al {} \;
```

This searches for `.conf` files and displays detailed information about each one.

---

## Redirect Errors

A large search across the Linux filesystem may produce permission errors.

These can be hidden using:

```bash
2>/dev/null
```

Example:

```bash
find / -type f -name "*.conf" 2>/dev/null
```

`2>` redirects standard error (`STDERR`).

`/dev/null` discards the redirected output.

This means:

```text
2>/dev/null
```

can be used to hide error messages from the terminal.

---

## Complete find Example

```bash
find / -type f -name "*.conf" -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null
```

This command searches:

- From `/`
- Only files
- Files ending in `.conf`
- Owned by root
- Larger than 20 KiB
- Modified after March 3, 2020

Then it runs:

```bash
ls -al
```

against each result and hides permission errors.

---

## locate

The `locate` command searches using a local database instead of scanning the filesystem directly.

Because of this, it can be much faster than `find`.

Update the locate database:

```bash
sudo updatedb
```

Search for `.conf` files:

```bash
locate "*.conf"
```

---

## find vs locate

### find

Advantages:

- Searches the filesystem directly
- Supports many filters
- Can search by:
  - Name
  - Type
  - Owner
  - Size
  - Date
- Can execute commands against results

Disadvantage:

- Can be slower

### locate

Advantages:

- Very fast
- Simple to use

Disadvantages:

- Uses a database
- Database may need to be updated
- Has fewer filtering capabilities

---

## Cybersecurity Relevance

Searching the filesystem is useful for:

- Enumeration
- Finding configuration files
- Finding scripts
- Discovering installed tools
- Looking for sensitive files
- Privilege escalation research
- Locating files owned by privileged users

Important commands from this section:

```bash
which <command>
find <location> <options>
locate <pattern>
sudo updatedb
```

Useful `find` filters:

```bash
-type f
-name
-user
-size
-newermt
-exec
```

Useful error redirection:

```bash
2>/dev/null
```


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
- Section 9 - Editing Files
- Section 10 - Find Files and Directories
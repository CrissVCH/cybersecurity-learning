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

# Section 11 - File Descriptors and Redirections

Linux uses file descriptors to manage input, normal output, and errors.

The three standard file descriptors are:

```text
0 = STDIN
1 = STDOUT
2 = STDERR
```

---

## STDIN, STDOUT and STDERR

### STDIN - File Descriptor 0

Standard input received by a program.

Input can come from:

- Keyboard
- File
- Another command

### STDOUT - File Descriptor 1

Normal output produced by a command.

### STDERR - File Descriptor 2

Error output produced by a command.

STDOUT and STDERR are separate streams and can be redirected independently.

---

## Redirecting STDOUT

Redirect normal output to a file:

```bash
command > file.txt
```

This is equivalent to:

```bash
command 1> file.txt
```

Important:

```text
>  overwrites the file
>> appends to the file
```

Example:

```bash
echo hello > notes.txt
echo world >> notes.txt
```

---

## Redirecting STDERR

Redirect errors:

```bash
command 2> errors.txt
```

Example:

```bash
find / -name "*.log" 2> errors.txt
```

---

## /dev/null

`/dev/null` discards anything written to it.

It is useful for hiding errors:

```bash
2>/dev/null
```

Example:

```bash
find / -type f -name "*.log" 2>/dev/null
```

The command can still produce permission errors, but they are not displayed.

---

## Redirect STDOUT and STDERR Separately

```bash
command 1> stdout.txt 2> stderr.txt
```

This sends:

```text
normal output → stdout.txt
errors        → stderr.txt
```

---

## Redirecting STDIN

Use a file as input:

```bash
command < file.txt
```

Example:

```bash
cat < file.txt
```

---

## Here Documents

A here document provides multi-line input to a command.

Example:

```bash
cat << EOF
Hello
Linux
HTB
EOF
```

The shell continues accepting input until the closing delimiter is reached.

It can also be redirected to a file:

```bash
cat << EOF > stream.txt
Hello
Linux
HTB
EOF
```

Quick reference:

```text
<       Input from a file
<< EOF  Multi-line input

>       Write output and overwrite
>>      Append output
```

---

## Pipes

A pipe sends the STDOUT of one command into the STDIN of another.

```bash
command1 | command2
```

Example:

```bash
find /etc -name "*.conf" 2>/dev/null | grep systemd
```

Conceptually:

```text
command
   ↓
 STDOUT
   ↓
   |
   ↓
 STDIN
   ↓
next command
```

This is one of the most important Linux concepts because small tools can be chained together.

---

## grep

`grep` filters text using a pattern.

```bash
command | grep pattern
```

Case-insensitive search:

```bash
grep -i "linux"
```

This can match:

```text
linux
Linux
LINUX
```

---

## Basic Regex - ^

The regex symbol:

```text
^
```

means:

```text
beginning of the line
```

Example:

```bash
grep '^ii'
```

keeps only lines beginning with `ii`.

---

## wc -l

Count lines:

```bash
wc -l
```

Example:

```bash
command | wc -l
```

This is useful when each result is displayed on one line.

---

## Building Pipelines

Commands can be chained together:

```bash
command | grep pattern | wc -l
```

The logic is:

```text
Generate data
      ↓
Filter data
      ↓
Count results
```

A good habit is to build pipelines step by step instead of writing everything at once.

---

## Practical Example - Finding .log Files

A search can be built based on several questions:

```text
Where?
→ /

What type?
→ regular file

What filename?
→ *.log

Hide errors?
→ 2>/dev/null

Need a count?
→ wc -l
```

Example structure:

```bash
find / -type f -name "*.log" 2>/dev/null | wc -l
```

Important:

```bash
-name "*.log"
```

means any filename ending in `.log`.

This:

```bash
-name ".log"
```

would search for a file literally named `.log`.

---

## dpkg -l

`dpkg -l` lists package information:

```bash
dpkg -l
```

Before filtering output, it is useful to inspect it:

```bash
dpkg -l | head
```

This helps understand the output format before building a pipeline.

---

## Installed Package State

Installed package entries begin with:

```text
ii
```

The two characters represent package states:

```text
i = Install
i = Installed
```

Installed packages can therefore be filtered with:

```bash
grep '^ii'
```

Example structure:

```bash
dpkg -l | grep '^ii' | wc -l
```

The important concept is the pipeline:

```text
dpkg
 ↓
generate package information

grep
 ↓
keep installed packages

wc -l
 ↓
count results
```

---

## dpkg -l vs dpkg -L

Linux options are case-sensitive.

```bash
dpkg -l
```

Lowercase `l`:

```text
List package information
```

```bash
dpkg -L <package>
```

Uppercase `L`:

```text
List files installed by a package
```

Therefore:

```text
-l != -L
```

---

## Problem-Solving Workflow

When building Linux commands:

```text
1. Run the base command
2. Inspect the output
3. Add a filter
4. Check the filtered output
5. Add counting or redirection
```

Example:

```bash
dpkg -l
```

then:

```bash
dpkg -l | grep '^ii'
```

then:

```bash
dpkg -l | grep '^ii' | wc -l
```

This makes commands easier to understand and debug.

---

## Important Commands

```bash
command > file.txt
command >> file.txt
command 2> errors.txt
command 2>/dev/null
command < file.txt

command1 | command2

grep pattern
grep -i pattern
grep '^pattern'

wc -l
head

dpkg -l
dpkg -L <package>
```

---

## Key Takeaways

```text
0 = STDIN
1 = STDOUT
2 = STDERR

>   overwrite STDOUT
>>  append STDOUT
2>  redirect STDERR
<   redirect STDIN
|   pipe output to another command
```

The main skill developed in this section was learning to build data-processing pipelines:

```text
Generate data
     ↓
Redirect unwanted output
     ↓
Pipe useful output
     ↓
Filter it
     ↓
Count or save the final result
```

# Section 12 - Filter Contents

This section focused on reading, filtering, transforming, organizing, and counting text directly from the Linux terminal.

The main idea is to progressively process command output using small tools connected through pipes.

```text
command
   ↓
filter
   ↓
transform
   ↓
final result
```

---

## more and less

`more` and `less` are pagers used to read large files without opening them in a text editor.

```bash
cat /etc/passwd | more
```

```bash
less /etc/passwd
```

Exit either pager with:

```text
q
```

`less` generally provides more functionality than `more`.

---

## head

Displays the beginning of a file or command output.

```bash
head /etc/passwd
```

By default, it shows the first 10 lines.

---

## tail

Displays the end of a file or command output.

```bash
tail /etc/passwd
```

By default, it shows the last 10 lines.

---

## sort

Sorts text output.

```bash
cat /etc/passwd | sort
```

By default, results are sorted alphabetically.

---

## grep

Filters lines that match a pattern.

```bash
grep "pattern"
```

Example:

```bash
cat /etc/passwd | grep "/bin/bash"
```

### Exclude matches

```bash
grep -v "pattern"
```

Example:

```bash
grep -v "false\|nologin"
```

This excludes lines containing either `false` or `nologin`.

### Case-insensitive search

```bash
grep -i "pattern"
```

---

## cut

`cut` extracts fields from structured text.

The `/etc/passwd` file uses `:` as a delimiter.

Example:

```bash
cut -d":" -f1
```

Meaning:

```text
-d":"  → delimiter is :
-f1    → return field 1
```

Multiple fields can be selected:

```bash
cut -d":" -f1,3,7
```

Important `/etc/passwd` fields:

```text
1 = Username
3 = UID
6 = Home directory
7 = Shell
```

---

## UID

UID means:

```text
User ID
```

It is the numeric identifier Linux uses internally for a user.

---

## tr

`tr` replaces characters.

Example:

```bash
tr ":" ","
```

This changes colon-separated output into comma-separated output.

---

## column

`column -t` formats text into aligned columns.

```bash
command | column -t
```

Its main purpose is readability.

---

## awk

`awk` can process specific columns in text.

Example:

```bash
awk '{print $1, $NF}'
```

Meaning:

```text
$1  = first field
$NF = last field
```

Unlike `grep`, which normally searches the entire line, `awk` can target specific columns.

Example:

```bash
ss -ltn4 | awk '$4 ~ /^0\.0\.0\.0:/'
```

This filters based specifically on column 4.

Important lesson:

```text
Do not blindly memorize column numbers.
Always inspect the output first.
```

---

## sed

`sed` is a stream editor commonly used for text substitution.

Syntax:

```bash
sed 's/old/new/g'
```

Example:

```bash
sed 's/bin/HTB/g'
```

Meaning:

```text
s = substitute
g = replace all matches
```

---

## wc -l

Counts lines.

```bash
wc -l
```

Example:

```bash
command | wc -l
```

Useful when each line represents one result.

---

# Working with /etc/passwd

This section used `/etc/passwd` to practice filtering.

Example pipeline:

```bash
cat /etc/passwd | cut -d":" -f1,3,7 | tr ":" ","
```

This can display:

```text
username,UID,shell
```

Filtering unwanted accounts can be added:

```bash
grep -v "false\|nologin"
```

The important concept is that every stage changes the data passed to the next stage.

---

# Network Filtering with ss

`ss` can inspect network sockets.

Useful options:

```text
-l = listening
-t = TCP
-n = numeric addresses and ports
-4 = IPv4
-u = UDP
```

Example:

```bash
ss -ltn4
```

Important addresses:

```text
0.0.0.0   = listening on all IPv4 interfaces
127.0.0.1 = localhost only
```

A simple `grep "0.0.0.0"` can sometimes produce incorrect results because it searches the entire line.

Using `awk` can filter the specific Local Address column instead.

---

# Process Filtering with ps

Processes are associated with users.

Example:

```bash
ps aux | grep -i ProFTPd
```

The first column of `ps aux` is:

```text
USER
```

Process states such as:

```text
S+
Ss
```

belong to the `STAT` column and are not usernames.

`ps` output can also be customized:

```bash
ps -Ao pid,tt,user
```

Where:

```text
-A   all processes
-o   choose output columns
pid  process ID
tt   terminal
user process owner
```

---

# curl

`curl` can retrieve web content from the terminal.

```bash
curl "https://example.com"
```

Silent mode:

```bash
curl -s "https://example.com"
```

This returns the page's HTML without the transfer progress information.

---

## href and Web Paths

In HTML:

```html
<a href="/contact/">Contact</a>
```

`href` contains the destination of a hyperlink.

For:

```text
https://example.com/contact/
```

the components are:

```text
https://      → protocol
example.com   → domain
/contact/     → path
```

---

## sort -u

Sort results and remove duplicates:

```bash
sort -u
```

Useful when counting unique results.

---

# Advanced Regex

During the HTB exercises, a more advanced command was used to extract paths from HTML.

The important concept was not memorizing the entire regex, but understanding the pipeline:

```text
curl
  ↓
retrieve HTML

grep
  ↓
extract matching data

sort -u
  ↓
remove duplicates

wc -l
  ↓
count results
```

Complex regex can be learned gradually later.

---

# Problem-Solving Workflow

A good way to build complex Linux commands is:

```text
1. Run the original command
2. Inspect the output
3. Add one filter
4. Inspect again
5. Add another transformation
6. Verify the result
7. Only then count or save it
```

This helps avoid getting an answer that looks correct but is actually counting the wrong information.

---

# Important Commands

```bash
more
less
head
tail
sort

grep
grep -v
grep -i

cut -d":" -f1
tr ":" ","
column -t

awk '{print $1, $NF}'
sed 's/old/new/g'

wc -l

ss -ltn4
ps aux
ps -Ao pid,tt,user

curl
curl -s

sort -u
```

---

# Key Takeaway

The most important skill from this section was learning how to progressively reduce large amounts of data into exactly the information needed:

```text
Raw data
   ↓
Inspect
   ↓
Filter
   ↓
Transform
   ↓
Inspect again
   ↓
Count / save result
```

# Section 13 - Regular Expressions

Regular Expressions (RegEx) are patterns used to search, filter, and manipulate text with more precision.

RegEx can be used with tools such as:

- `grep`
- `sed`
- Programming languages
- Other text-processing tools

Instead of searching only for exact text, RegEx allows us to describe the structure of what we want to find.

---

## Extended Regular Expressions

With `grep`, the option:

```bash
-E
```

enables Extended Regular Expressions.

Example:

```bash
grep -E "(my|false)" /etc/passwd
```

This searches for lines containing either:

```text
my
OR
false
```

---

# Important RegEx Symbols

## Parentheses `()`

Used to group expressions.

Example:

```text
(my|false)
```

This groups the two patterns together.

---

## Square Brackets `[]`

Used to define a character class.

Example:

```text
[a-z]
```

means:

```text
any lowercase letter from a to z
```

---

## Curly Brackets `{}`

Used as quantifiers.

Example:

```text
{1,10}
```

means that the previous pattern can repeat between 1 and 10 times.

---

## OR Operator `|`

The pipe inside RegEx represents:

```text
OR
```

Example:

```bash
grep -E "(my|false)" /etc/passwd
```

means:

```text
find my OR false
```

---

# The `.*` Pattern

Two important symbols are:

```text
. = any character

* = zero or more repetitions of the previous pattern
```

Together:

```text
.*
```

means approximately:

```text
zero or more of any character
```

Example:

```bash
grep -E "my.*false" /etc/passwd
```

Conceptually:

```text
find "my"
    ↓
allow anything between
    ↓
later find "false"
```

HTB uses this as an AND-like pattern where both expressions must appear in the specified order.

A similar idea can also be created using pipelines:

```bash
grep -E "my" /etc/passwd | grep -E "false"
```

---

# Line Anchors

## `^` - Beginning of Line

```text
^Password
```

means:

```text
the line must begin with Password
```

Example:

```bash
grep -E "^Password" file
```

This can match:

```text
PasswordAuthentication yes
```

but not:

```text
# PasswordAuthentication yes
```

because that line begins with `#`.

---

## `$` - End of Line

```text
yes$
```

means:

```text
the line must end with yes
```

Example:

```bash
grep -E "yes$" file
```

---

# Word Boundaries

Line boundaries and word boundaries are different.

## `\<` - Beginning of Word

```text
\<Permit
```

means:

```text
find a word that starts with Permit
```

Examples:

```text
PermitRootLogin
PermitEmptyPasswords
PermitUserEnvironment
```

---

## `\>` - End of Word

```text
Authentication\>
```

means:

```text
find a word that ends with Authentication
```

Examples:

```text
PasswordAuthentication
PubkeyAuthentication
HostbasedAuthentication
```

---

# Line vs Word Anchors

Important distinction:

```text
^Permit
→ the LINE begins with Permit

\<Permit
→ a WORD begins with Permit
```

And:

```text
yes$
→ the LINE ends with yes

Authentication\>
→ a WORD ends with Authentication
```

---

# grep -w

The option:

```bash
-w
```

matches a complete word.

Example:

```bash
grep -w "Permit"
```

searches for the complete word:

```text
Permit
```

This is different from:

```text
\<Permit
```

because:

```text
PermitRootLogin
```

starts with `Permit`, but is not exactly the word `Permit`.

---

# grep -v

The `-v` option inverts a match.

Normal:

```bash
grep "#"
```

means:

```text
show lines containing #
```

But:

```bash
grep -v "#"
```

means:

```text
show lines NOT containing #
```

---

# Practice File

The exercises used:

```text
/etc/ssh/sshd_config
```

This is the SSH server configuration file.

It provided a real configuration file for practicing pattern matching.

---

# Practice Patterns

## Lines Without `#`

The idea was to invert the search:

```bash
grep -v "#" /etc/ssh/sshd_config
```

Key concept:

```text
-v = exclude matching lines
```

---

## Words Starting with `Permit`

Important difference:

```text
^Permit
→ line starts with Permit

\<Permit
→ word starts with Permit
```

Pattern:

```text
\<Permit
```

---

## Words Ending with `Authentication`

Pattern:

```text
Authentication\>
```

This can match values such as:

```text
PubkeyAuthentication
PasswordAuthentication
HostbasedAuthentication
```

---

## Lines Containing `Key`

Not every search requires complicated RegEx.

Searching for:

```text
Key
```

can already match values such as:

```text
HostKey
AuthorizedKeysFile
AuthorizedKeysCommand
GSSAPIKeyExchange
```

Important lesson:

```text
Use the simplest pattern that solves the problem.
```

---

## Lines Beginning with `Password` and Containing `yes`

Pattern:

```text
^Password.*yes
```

Breakdown:

```text
^
→ beginning of line

Password
→ line must begin with this text

.
→ any character

*
→ zero or more repetitions

.*
→ any number of any characters

yes
→ must appear later
```

Conceptually:

```text
Beginning of line
      ↓
Password
      ↓
anything can appear here
      ↓
yes
```

---

## Lines Ending with `yes`

Pattern:

```text
yes$
```

Remember:

```text
$
→ end of line
```

Difference:

```text
yes\>
→ WORD ends with yes

yes$
→ LINE ends with yes
```

---

# Important Mistake - `?`

The:

```text
?
```

symbol does NOT mean end of line.

In Extended RegEx, it means:

```text
the previous pattern appears 0 or 1 times
```

Example:

```text
yes?
```

can match:

```text
ye
yes
```

because the `s` is optional.

The correct end-of-line symbol is:

```text
$
```

---

# Important Mistake - `,*` vs `.*`

These expressions are very different:

```text
,*
```

means:

```text
zero or more commas
```

while:

```text
.*
```

means:

```text
zero or more of any character
```

For a pattern such as:

```text
^Password.*yes
```

the correct expression is:

```text
.*
```

---

# Using man grep

I do not need to memorize every RegEx expression immediately.

Useful command:

```bash
man grep
```

Inside the manual, search using:

```text
/word
```

For example:

```text
/beginning
```

Useful features discovered through the manual include:

```text
\<
\>
-w
```

A better learning workflow is:

```text
Understand what I need
        ↓
Check man / --help
        ↓
Find the relevant syntax
        ↓
Test the pattern
        ↓
Inspect the output
```

---

# RegEx Quick Reference

```text
^
→ beginning of line

$
→ end of line

\<
→ beginning of word

\>
→ end of word

.
→ any character

*
→ zero or more repetitions

.*
→ zero or more of any character

|
→ OR

()
→ group expressions

[]
→ character class

{}
→ quantifier / repetition

?
→ previous pattern appears 0 or 1 times
```

---

# grep Options Reinforced

```text
-E
→ Extended Regular Expressions

-v
→ invert match

-w
→ complete word

-i
→ case-insensitive search
```

---

# Example Pattern Breakdown

```bash
grep -E "^Password.*yes" /etc/ssh/sshd_config
```

Can be read as:

```text
^Password
→ start the line with Password

.*
→ allow any number of characters

yes
→ later contain yes
```

Thinking about RegEx this way makes complex expressions easier to understand.

---

# Key Takeaway

The main lesson from this section was learning the difference between searching for literal text and describing a pattern.

Instead of only thinking:

```text
find this word
```

RegEx allows searches such as:

```text
find a line that starts with X

find a line that ends with Y

find a word that starts with X

find a word that ends with Y

find either A or B

find A followed later by B
```

The goal is not to memorize every RegEx symbol immediately.

The more important skill is:

```text
What condition am I trying to express?
                ↓
Find the appropriate RegEx syntax
                ↓
Test it
                ↓
Inspect the result
```

Useful references:

```bash
man grep
grep --help
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
- Section 11 - File Descriptors and Redirections
- Section 12 - Filter Contents
- Section 13 - Regular Expressions
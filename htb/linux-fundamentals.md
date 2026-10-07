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

# Section 14 - Permission Management

Linux permissions control who can access, modify, or execute files and directories.

Every file and directory has:

- An owner
- A group
- Permissions for the owner
- Permissions for the group
- Permissions for others

---

## Permission Types

Linux uses three basic permissions:

```text
r = read
w = write
x = execute
```

Their octal values are:

```text
r = 4
w = 2
x = 1
```

Permissions are divided into:

```text
owner | group | others
```

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
- | rwx | r-x | r--
    owner group others
```

Which becomes:

```text
owner  = rwx = 7
group  = r-x = 5
others = r-- = 4
```

Therefore:

```text
754
```

---

# File Types

The first character in `ls -l` shows the object type.

```text
- = regular file
d = directory
l = symbolic link
```

Examples:

```text
-rw-r--r--
→ regular file
```

```text
drwxr-xr-x
→ directory
```

---

# Common Octal Values

```text
7 = rwx
6 = rw-
5 = r-x
4 = r--
3 = -wx
2 = -w-
1 = --x
0 = ---
```

The values are added together.

Example:

```text
rwx
4 + 2 + 1
= 7
```

```text
r-x
4 + 1
= 5
```

---

# chmod

`chmod` changes permissions.

There are two common methods:

```text
Octal
Symbolic
```

---

## Octal chmod

Example:

```bash
chmod 754 file
```

Means:

```text
owner  = rwx
group  = r-x
others = r--
```

Another common example:

```bash
chmod 644 file
```

Means:

```text
owner  = rw-
group  = r--
others = r--
```

---

## Symbolic chmod

Permission targets:

```text
u = user / owner
g = group
o = others
a = all
```

Operators:

```text
+ = add permission
- = remove permission
```

Examples:

```bash
chmod g+w file
```

Adds write permission to the group.

```bash
chmod o-r file
```

Removes read permission from others.

```bash
chmod a+x file
```

Adds execute permission to everyone.

---

# File vs Directory Permissions

The meaning of `x` depends on the object.

For a file:

```text
x
→ execute the file
```

For a directory:

```text
x
→ traverse / access the directory
```

Without execute permission on a directory:

```bash
cd directory
```

may return:

```text
Permission denied
```

For directories:

```text
r
→ list directory entries

w
→ create, delete, or rename items

x
→ enter / traverse the directory
```

This is an important distinction.

---

# Reading ls -l

Example:

```text
-rw-r--r-- 1 user group 0 Oct 6 02:04 test.txt
```

Important fields:

```text
-rw-r--r--
→ file type and permissions

1
→ number of hard links

user
→ owner

group
→ group

0
→ file size

Oct 6 02:04
→ modification date/time

test.txt
→ filename
```

---

# chown

`chown` changes the owner and/or group of a file or directory.

Syntax:

```bash
chown user:group file
```

Example:

```bash
chown root:root shell
```

Changes:

```text
owner → root
group → root
```

---

# SUID

SUID means:

```text
Set User ID
```

Normally:

```text
user executes program
        ↓
program runs as that user
```

With SUID:

```text
user executes program
        ↓
program runs with the file owner's privileges
```

Example:

```text
-rwsr-xr-x
```

The:

```text
s
```

in the owner execute position indicates SUID.

This can become dangerous if the owner is `root` and the program can launch commands or shells.

This is important later for privilege escalation.

---

# SGID

SGID means:

```text
Set Group ID
```

It works similarly to SUID, but uses the privileges of the file's group.

Example:

```text
-rwxr-sr-x
```

The:

```text
s
```

in the group execute position indicates SGID.

Quick comparison:

```text
SUID
→ use file owner's privileges

SGID
→ use file group's privileges
```

---

# Sticky Bit

The sticky bit is mainly used on shared directories.

It prevents users from deleting or renaming files they do not own.

Normally, only:

```text
file owner
directory owner
root
```

can delete or rename files inside a sticky-bit directory.

Representation:

```text
t
```

means:

```text
sticky bit enabled
+
execute permission exists for others
```

```text
T
```

means:

```text
sticky bit enabled
+
execute permission for others is NOT set
```

---

# Permission Quick Reference

```text
r = read    = 4
w = write   = 2
x = execute = 1
```

```text
u = owner
g = group
o = others
a = all
```

```text
chmod
→ change permissions

chown
→ change owner/group
```

---

# Important Commands

```bash
ls -l

chmod 754 file
chmod 644 file

chmod g+w file
chmod o-r file
chmod a+x file

chown user:group file
```

---

# Key Takeaway

The most important practical skill from this section is being able to look at:

```text
-rwxr-xr--
```

and understand:

```text
owner  = rwx = 7
group  = r-x = 5
others = r-- = 4
```

Therefore:

```text
754
```

Also remember:

```text
x on file
→ execute

x on directory
→ traverse
```

And from a cybersecurity perspective:

```text
SUID / SGID
→ may run with elevated owner/group privileges
→ important later in privilege escalation

Sticky Bit
→ protects files in shared directories
```

# Section 15 - User Management

This section focused on managing Linux users and groups and understanding how identity, ownership, and permissions work together.

Main concepts:

- Creating and deleting users
- Managing passwords
- Switching users
- Creating and managing groups
- Running commands with elevated privileges
- Understanding primary and supplementary groups
- Connecting users/groups with file permissions

---

## /etc/passwd

General Linux user account information is stored in:

```text
/etc/passwd
```

Example:

```text
alexlab:x:1003:1004::/home/alexlab:/bin/bash
```

Structure:

```text
username : password : UID : GID : comment : home : shell
```

Important fields:

```text
1 = username
3 = UID
4 = primary GID
6 = home directory
7 = login shell
```

Example using `cut`:

```bash
cut -d":" -f1,3,7 /etc/passwd
```

This extracts:

```text
username : UID : shell
```

---

## /etc/shadow

Sensitive password-related information is stored in:

```text
/etc/shadow
```

Normal users usually cannot read it.

```bash
cat /etc/shadow
```

may return:

```text
Permission denied
```

With appropriate privileges:

```bash
sudo cat /etc/shadow
```

---

# sudo

`sudo` executes a command with elevated or different-user privileges.

Example:

```bash
sudo cat /etc/shadow
```

Conceptually:

```text
normal user
    ↓
sudo
    ↓
elevated command
```

Not every user automatically has permission to use `sudo`.

---

# su

`su` switches to another user.

```bash
su - alexlab
```

The `-` creates a login-style environment for that user.

```text
su alexlab
→ switch user

su - alexlab
→ switch user
→ load user's HOME
→ load login environment
→ use user's login shell
```

Useful commands after switching:

```bash
whoami
pwd
id
```

---

# useradd

Creates a user account.

Example:

```bash
sudo useradd -m -s /bin/bash alexlab
```

Meaning:

```text
-m
→ create home directory

-s /bin/bash
→ set login shell

alexlab
→ username
```

This creates:

```text
/home/alexlab
```

---

# Verifying Users

Display user and group information:

```bash
id alexlab
```

Example:

```text
uid=1003(alexlab)
gid=1004(alexlab)
groups=1004(alexlab)
```

Search `/etc/passwd`:

```bash
grep "alexlab" /etc/passwd
```

Retrieve the account through system databases:

```bash
getent passwd alexlab
```

---

# passwd

Set or change a user's password:

```bash
sudo passwd alexlab
```

The password is not displayed while typing.

---

# Groups

Linux users can have:

```text
one primary group
+
zero or more supplementary groups
```

Create a group:

```bash
sudo addgroup labteam
```

Verify it:

```bash
getent group labteam
```

Example:

```text
labteam:x:1003:
```

---

# getent

`getent` retrieves entries from system databases.

Useful examples:

```bash
getent passwd USER
getent group GROUP
```

Mental model:

```text
getent
→ get entry
```

---

# usermod

Modify an existing user.

Example:

```bash
sudo usermod -aG labteam alexlab
```

Meaning:

```text
-a
→ append

-G
→ supplementary groups

labteam
→ group

alexlab
→ user
```

This adds `alexlab` to `labteam` without removing existing supplementary groups.

Important:

```text
-G without -a
```

can replace the user's current supplementary group list.

---

# Primary vs Supplementary Groups

Example:

```text
gid=1004(alexlab)
```

means:

```text
primary group = alexlab
```

While:

```text
groups=1004(alexlab),1003(labteam)
```

means:

```text
alexlab
→ primary group

labteam
→ supplementary group
```

---

# Home Directory ~

The symbol:

```text
~
```

represents the current user's home directory.

For `alexlab`:

```text
~
=
/home/alexlab
```

Example:

```bash
touch ~/alex-file.txt
```

is equivalent to:

```bash
touch /home/alexlab/alex-file.txt
```

---

# ls -ld

To inspect a directory itself:

```bash
ls -ld /home/alexlab
```

Without `-d`:

```bash
ls -l /home/alexlab
```

tries to list its contents.

Example:

```text
drwx------ ... alexlab alexlab ... /home/alexlab
```

means:

```text
owner = alexlab
group = alexlab

owner  = rwx
group  = ---
others = ---
```

---

# Running a Command as Another User

Instead of switching the whole shell:

```bash
sudo -u alexlab whoami
```

runs only that command as `alexlab`.

Another example:

```bash
sudo -u alexlab touch /home/alexlab/from-sudo.txt
```

Conceptually:

```text
sudo -u USER COMMAND
→ execute one command as USER
```

---

# Shared Group Directory

A useful lab combined users, groups, ownership, and permissions.

```bash
sudo mkdir /tmp/labshared
sudo chown root:labteam /tmp/labshared
sudo chmod 770 /tmp/labshared
```

Result:

```text
drwxrwx--- root labteam /tmp/labshared
```

Meaning:

```text
owner = root
→ rwx

group = labteam
→ rwx

others
→ ---
```

Because `alexlab` belongs to `labteam`, the user can access the directory using group permissions.

This demonstrates:

```text
USER
 ↓
belongs to GROUPS
 ↓
files/directories have OWNER + GROUP
 ↓
rwx permissions determine access
```

---

# userdel

Delete a user:

```bash
sudo userdel alexlab
```

Delete the user and also remove their home directory and related files:

```bash
sudo userdel -r alexlab
```

Important:

```text
-r
```

here belongs specifically to `userdel`.

---

# Command Options Are Command-Specific

Options do not always mean the same thing.

Example:

```text
rm -r
→ recursive

userdel -r
→ remove user home and related files
```

Always check options using:

```bash
COMMAND --help
```

or:

```bash
man COMMAND
```

---

# Important Commands

```bash
sudo COMMAND

su - USER

useradd
userdel
usermod
passwd

addgroup
delgroup

id USER
groups USER
whoami

getent passwd USER
getent group GROUP

ls -ld DIRECTORY

sudo -u USER COMMAND
```

---

# Key Takeaway

Linux access control depends on several pieces working together:

```text
user identity
+
group membership
+
file/directory ownership
+
rwx permissions
```

A user does not need to own a resource directly if one of their groups has the required permissions.

This section connected:

```text
User Management
+
Group Management
+
Ownership
+
Permission Management
```

into one complete access-control model.

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
- Section 14 - Permission Management
- Section 15 - User Management
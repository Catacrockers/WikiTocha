# Terminology

* **/**: Slash.
* **~**: Home path
* **.**: Current directory.
* **..**: Parent directory.
* **|**: Pipe.
* **'**: Single quote.
* **>**: Symbol to redirect the output of a command.
* **>>**: Symbol to appends standard output to a file.
* **<**: Symbol to redirect the input of a command.
* **FHS**: Filesystem Hierarchy Standard.
* **PID**: Process ID.
* **terminal**: Device used for entering data into, and displaying data from, a computer.
* **sudo**: It is a program for Unix-like computer operating systems that allows users to run programs with the security privileges of another user, by default the superuser.
* **pipeline**: It is a sequence of processes chained together by their standard streams, so that the output of each process (stdout) feeds directly as input (stdin) to the next one.
* **root**: The top of the file system hierarchy standard. Called */*.
* **working directory**: It is a directory of a hierarchical file system, if any, dynamically associated with each process.
* **Hardware**: Computer hardware refers to the physical parts of a computer and related devices.
* **Software**: Computer software is a general term that describes computer programs. Related terms such as software programs, applications, scripts, and instruction sets all fall under the category of computer software.

# Files and directories

UNIX use binary files and folder. Folders group 0 or more folders and files and are organized following Filesystem Hierarchy Standard (FHS):

| Directory | Description |
|-----------|-------------|
| / | Primary hierarchy root and root directory of the entire file system hierarchy |
| /bin | Essential command binaries that need to be available in single user mode; for all users, e.g., cat, ls, cp |
| /boot | Boot loader files, e.g., kernels, initrd |
| /dev | Essential device files, e.g., /dev/null |
| /etc | Host-specific system-wide configuration files |
| /etc/opt | Configuration files for add-on packages that are stored in /opt/ |
| /etc/sgml | Configuration files, such as catalogs, for software that processes SGML |
| /etc/X11 | Configuration files for the X Window System, version 11 |
| /etc/xml | Configuration files, such as catalogs, for software that processes XML |
| /home | Users' home directories, containing saved files, personal settings, etc |
| /lib | Libraries essential for the binaries in /bin/ and /sbin/ |
| /lib<qual> | Alternate format essential libraries. Such directories are optional, but if they exist, they have some requirements |
| /media | Mount points for removable media such as CD-ROMs (appeared in FHS-2.3) |
| /mnt | Temporarily mounted filesystems |
| /opt | Optional application software packages |
| /proc | Virtual filesystem providing process and kernel information as files. In Linux, corresponds to a procfs mount |
| /root | Home directory for the root user |
| /run | Run-time variable data: Information about the running system since last boot, e.g., currently logged-in users and running daemons |
| /sbin | Essential system binaries, e.g., fsck, init, route |
| /srv | Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems |
| /sys | Contains information about the devices connected to the computer |
| /tmp | Temporary files (see also /var/tmp). Often not preserved between system reboots, and may be severely size restricted |
| /usr | Secondary hierarchy for read-only user data; contains the majority of (multi-)user utilities and applications |
| /usr/bin | Non-essential command binaries (not needed in single user mode); for all users |
| /usr/include | Standard include files |
| /usr/lib | Libraries for the binaries in /usr/bin/ and /usr/sbin/ |
| /usr/lib<qual> | Alternate format libraries (optional) |
| /usr/local | Tertiary hierarchy for local data, specific to this host. Typically has further subdirectories, e.g., bin/, lib/, share/ |
| /usr/sbin | Non-essential system binaries, e.g., daemons for various network-services |
| /usr/share | Architecture-independent (shared) data |
| /usr/src | Source code, e.g., the kernel source code with its header files |
| /usr/X11R6 | X Window System, Version 11, Release 6 (up to FHS-2.3, optional) |
| /var | Variable files—files whose content is expected to continually change during normal operation of the system—such as logs, spool files, and temporary e-mail files |
| /var/cache | Application cache data. Such data are locally generated as a result of time-consuming I/O or calculation. The application must be able to regenerate or restore the data. The cached files can be deleted without loss of data |
| /var/lib | State information. Persistent data modified by programs as they run, e.g., databases, packaging system metadata, etc |
| /var/lock | Lock files. Files keeping track of resources currently in use |
| /var/log | Log files. Various logs |
| /var/mail | Mailbox files. In some distributions, these files may be located in the deprecated /var/spool/mail |
| /var/opt | Variable data from add-on packages that are stored in /opt/ |
| /var/run | Run-time variable data. This directory contains system information data describing the system since it was booted |

In FHS 3.0, /var/run is replaced by /run; a system should either continue to provide a /var/run directory, or provide a symbolic link from /var/run to /run, for backwards compatibility.

| Directory | Description |
|-----------|-------------|
| /var/spool | Spool for tasks waiting to be processed, e.g., print queues and outgoing mail queue |
| /var/spool/mail | Deprecated location for users' mailboxes |
| /var/tmp | Temporary files to be preserved between reboots |

Using ```ls -l``` in a path, you can get a output like this:

```
drwxr-xr-x 2 root root     0 Jan  1  1970 home
```

What is the meaning for `drwxr-xr-x`:
* First word:
  * First character: d = Is a directory. If is a file will appear -.
  * The followint 3 character sequences are permissions for user owner, group of user owners and rest of users: r = read, x = execution, w = write. No permission appear -.
* Second word is `2`: Number of files/folders inside including it.
* Third word is the Owner, in this case `root`.
* Forth word is the User, in this case `root`.
* Fifth word is Size of the file, is a folder so it is zero. In this case is `0`
* Next third words are the date, in this case: `Jan  1  1970`.
* And the last one is the file/folder name: `home`

# Shorcuts

In order to manage the terminal, you need to know some shortcuts to make your life easy and send signals.

| Command   | Meaning |
|:----------:|:-------------|
| Control + z | Suspend the process running in the foreground = send SIGSTOP signal |
| Control + c | Kill the process running in the foreground = send SIGINT signal |
| Control + shift + C | Copy selected terminal text |
| Control + shift + V | Paste previous copy/cut text into terminal |

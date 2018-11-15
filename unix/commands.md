# Unix Commands

This section cover all commands you shall need.

## Basics

A command is a specific instruction given to a computer application to perform some kind of task or function. Here, basic commands to manage an UNIX O.S through terminal.

| Command   | Meaning | Userful options |
|:----------:|:-------------|-------------|
| whoami | Print your user name | None |
| whatis $(command) | Print basic command info without options | None |
| man $(command) | An interface to the on-line reference manuals for any command | None |
| apropos $(command) | It returns the commands with keyword in their manual page header.  | None |
| ls $(directory_path) | Lists the contents of your current working directory. If no dir_path variable, print current | a: Show hidden, l: Print as list |
| cd $(directory_path) | Change to dir_path directory. dir_path can be any, including / ~ .. . |  None |
| mkdir $(subdir_name)| Make a subdirectory | p: Create any missing intermediate pathname components. |
| pwd | Print current working directory | None. |
| cp $(origin_file) $(destination_file) | Make a copy of $(origin_file) called $(destination_file). It can use relative path. | None |
| mv $(origin_file) $(destination_file) | Move file $(origin_file) to $(destination_file)  | None |
| rm $(file) | Remove a file. Can delete all files and folders using fr options | Use with precaution! f: force r: recursively |
| rmdir $(directory) | Delete a directory if is empty. | None |
| clear | Clear all text and leave you with the % prompt at the top of the window.  | None |
| cat $(file) | It can be used to display the contents of a file on the screen | n: Number all output lines |
| less | It writes the contents of a file onto the screen a page at a time. Pressing space bar. | None |
| head | It writes the first ten lines of a file to the screen.  | None |
| tail | It writes the last ten lines of a file to the screen.  | None |
| grep $(patterns) | It search files for specified words or patterns. To search phrases use single quotes | c: Count lines, i: Ignore upper/lower case distinctions |
| wc $(file) | Count words in a file. | l: print the newline counts, w: print the word counts |
| sort $(file) | Write sorted concatenation of all FILE(s) to standard output | None |
| chmod $(parameters) $(file/folder) | Change owner for a file or folder | 777 = full access for all users (Use with caution) |
| ps $(options) | Show information about your processes. | aux: All user processes in a list |
| sleep $(time_in_seconds) | Wait given number of seconds before continuing | None |
| $(command) & | Character ¬ run the process in background | None |
| jobs | list out the background jobs |
| bg | | |
| fg %$(i)|  bring a background job to the foreground | %i: Bring job number i in jobs list |
| kill | Kill | |
| killall $(name) | | |
| df . | The df command reports on the space left on the file system | human-readable: Print beautiful info |
| du -s $(file_name) | List the number of kilobyes used by each file | $(file_name) = * all list in your current path |
| file $(file_name) | It classifies the named files according to the type of data they contain | $(file_name) = * all list in your current path |
| diff $(file_name_1) $(file_name_2) | Compares the contents of two files and displays the differences. Lines beginning with a < denotes file1, while lines beginning with a > denotes file2 | None |
| find . -iname "$(sub_name_to_search)" | This searches through the directories for files and directories with a given name, date, size, or any other attribute you care to specify | -size +$(size_min): check for files with larger than size |
| grep | das | None |
| history | Ordered list of all the commands that you have entered | None |

# Info

| Command   | Meaning | Userful options |
|:----------:|:-------------|-------------|
| uname $(options) | Print system information | a: Print all info |
| lsb_release $(options) | Print certain LSB (Linux Standard Base) and Distribution information | a: Print all info |
| lscpu | Print CPU info | None |
| lsblk | Print information about block devices | None |
| lspci $(options) | Print PCI Hardware | v: verbose info |
| lsusb $(options) | Print USB Hardware | html: print in HTML format, short: Less info details |
| lshw | Print a lot of hardware info. Require installation and sudo. | None |
| fdisk $(options) | Print file system information. Require sudo. | l: List the partition tables for the specified devices |
| dmidecode $(options) | Print dumping a computer's DMI table contents in a human-readable format. Require sudo. | t: Choose a type or resource |

# Redirecting pipes

A pipeline is a sequence of processes chained together by their standard streams, so that the output of each process (stdout) feeds directly as input (stdin) to the next one.

## Redirect to files

Then, it is possible to redirect the output of a process (stdout) to a new file (overriding its content):

```
$ command > outputfile.txt  
```

It is possible to append stdout to a file at the bottom:

```
$ command >> outputfile.txt
```

If you want redirect the error messages of a process (stderr) as well use this:

```
$ command &> outputfile.txt   
```

To append it just:

```
$ command &>> outputfile.txt   
```

If you want to have both stderr and output displayed on the console and in a file use 'tee' command and pipe the output to it:

```
$ command | tee outputfile.txt
```

A slight modification will catch stderr as well:

```
$ command 2>&1 | tee outputfile.txt
```

or slightly shorter and less complicated:

```
$ command |& tee outputfile.txt
```

To summarize:

```
          || visible in terminal ||   visible in file   || existing
  Syntax  ||  StdOut  |  StdErr  ||  StdOut  |  StdErr  ||   file   
==========++==========+==========++==========+==========++===========
    >     ||    no    |   yes    ||   yes    |    no    || overwrite
    >>    ||    no    |   yes    ||   yes    |    no    ||  append
----------||----------|----------||----------|----------||----------
   2>     ||   yes    |    no    ||    no    |   yes    || overwrite
   2>>    ||   yes    |    no    ||    no    |   yes    ||  append
----------||----------|----------||----------|----------||----------
   &>     ||    no    |    no    ||   yes    |   yes    || overwrite
   &>>    ||    no    |    no    ||   yes    |   yes    ||  append
----------||----------|----------||----------|----------||----------
 | tee    ||   yes    |   yes    ||   yes    |    no    || overwrite
 | tee -a ||   yes    |   yes    ||   yes    |    no    ||  append
----------||----------|----------||----------|----------||----------
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    || overwrite
 n.e. (*) ||   yes    |   yes    ||    no    |   yes    ||  append
----------||----------|----------||----------|----------||----------
|& tee    ||   yes    |   yes    ||   yes    |   yes    || overwrite
|& tee -a ||   yes    |   yes    ||   yes    |   yes    ||  append
----------||----------|----------||----------|----------||----------
```

* Please note that the n.e. in the syntax column means "not existing".
** There is a way, but it's too complicated to fit into the column. You can find a helpful link in the List section about it.

# Connections

To connect to a server though terminal you need to:

```
ssh $(user_name)@$(server_address)
```

# Key management

## SSH

To create a SSH key:

```
ssh-keygen -t rsa -C "your_email@example.com"
```

This command will place a ssh key (public and private) at ```~/.ssh``` folder. Never share private key, and use public key to set up connections to remote terminals. In this folder you will have the following files:

* authorized_keys: Holds a list of authorized public keys for servers. When the client connects to a server, the server authenticates the client by checking its signed public key stored within this file.
* id_rsa: Contains your PRIVATE key. Never share!
* id_rsa.pub: Contains your PUBLIC key. You can share it.
* known_hosts: Contains DSA host keys of SSH servers accessed by the user. This file is very important for ensuring that the SSH client is connecting the correct SSH server.

## Passwords

Never share your passwords. Never reuse your passwords if is possible. Using a Password manager is a good strategy to improve your security.

### pass

pass is a utility to manage your passwords across several devices. It is the standard unix password manager. It require to create a gpg key. It can be managed though several computers using git directly though the command.

To generate a new key:

```
pass generate $(key_name) $(number_of_character)
```

* Note: key name support ```/```, so you can store in a folder system several keys. In example: ```$(key_group)/$(my_key)``` is a valid ```$(key_name)```
* Note II: Use ```[--no-symbols,-n]``` to avoid symbols and ```[-c]``` option to avoid printing and store it in the clipboard.

To get a key stored:

```
pass $(key_name)
```

* Note: Use ```[-c]``` option to avoid printing and store it in the clipboard.

To save key created:

```
pass git push
```

To get new keys:

```
pass git pull
```

# Concepts

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

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

# DAY-20 | LINUX For DevOps ENgineers

Linux is an open-source operating system kernel that serves as the foundation for various Linux-based operating systems (distributions).
Linux is known for its stability, security, and flexibility. It is based on the Unix operating system and follows the Unix philosophy of small, modular, and reusable components. Linux is highly customizable and can be tailored to suit various needs, ranging from desktop computers and servers to embedded systems and supercomputers.

Linux distributions, such as Ubuntu, Fedora, Debian, CentOS, and many others, take the Linux kernel and combine it with additional software packages, utilities, and graphical interfaces to create complete operating systems that are ready to be used by end-users.

Linux offers a command-line interface (CLI) that allows users to interact with the system through text commands, as well as graphical user interfaces (GUIs) that provide a more user-friendly experience. It supports a wide range of applications, software development tools, and server services, making it suitable for various purposes, including general computing, web servers, cloud infrastructure, networking, and more.

## Linux Folder Structure

The folder structure in Ubuntu Linux follows the Filesystem Hierarchy Standard (FHS), which is a standard for organizing the files and directories on a Unix-like operating system. Here is an overview of the main directories you will typically find in Ubuntu:

- **/bin**: Contains essential command-line executable files (binaries) that are available to all users.

- **/boot**: Contains files related to the boot process, including the Linux kernel, initial ramdisk (initrd), and bootloader configuration.

- **/dev**: Contains device files that represent and allow access to various hardware devices on the system.

- **/etc**: Contains system-wide configuration files for various applications and services.

- **/home**: The home directories for individual users. Each user typically has a subdirectory here to store their personal files and settings.

- **/lib** and **/lib64**: These directories contain shared libraries needed by the system and applications. The "lib64" directory is present on 64-bit systems.

- **/media**: Mount point for removable media devices such as USB drives or optical discs.

- **/mnt**: A general-purpose mount point for temporarily mounting filesystems.

- **/opt**: Contains optional software packages installed on the system. Applications installed here are often self-contained in their own directories.

- **/proc**: A virtual filesystem that provides information about processes and system status. It is used by many system utilities to obtain runtime information.

- **/root**: The home directory for the root user, the administrative superuser.

- **/run**: A temporary filesystem that contains runtime data for various system services. It is cleared on each reboot.

- **/sbin**: Contains system binaries (executable files) that are primarily used by the root user for system administration tasks.

- **/srv**: Contains data for services provided by the system.

- **/sys**: A virtual filesystem that exposes kernel-related information and configuration.

- **/tmp**: A directory for temporary files created by applications and users. Its contents are typically cleared on each reboot.

- **/usr**: Contains user-related programs, libraries, documentation, and shared resources. It has subdirectories such as /usr/bin for user binaries, /usr/lib for libraries, and /usr/share for shared data.

- **/var**: Contains variable data that changes during the system's operation, such as logs, databases, and spool files.

This is a high-level overview of the Ubuntu Linux folder structure. Each directory serves a specific purpose in organizing the system's files and resources.

## Important Linux Commands for DevOps Engineers

This repository provides a list of important Linux commands that are frequently used by DevOps engineers. Each command is explained with a brief description and examples of usage.

### 1. `ls`

- Description: Lists files and directories in the current directory.
- Usage:
  - `ls`: Lists files and directories in the current directory.
  - `ls -l`: Lists files and directories in long format.
  - `ls -a`: Lists all files and directories, including hidden ones.

### 2. `cd`

- Description: Changes the current directory.
- Usage:
  - `cd /path/to/directory`: Changes the current directory to the specified path.
  - `cd ..`: Moves up to the parent directory.
  - `cd ~`: Moves to the home directory.

### 3. `mkdir`

- Description: Creates a new directory.
- Usage:
  - `mkdir directory_name`: Creates a new directory with the specified name.
  - `mkdir -p path/to/directory`: Creates nested directories if they don't exist.

### 4. `rm`

- Description: Removes files and directories.
- Usage:
  - `rm file_name`: Removes the specified file.
  - `rm -r directory_name`: Removes the specified directory and its contents recursively.
  - `rm -f file_name`: Forces removal of the specified file without prompting.

### 5. `cp`

- Description: Copies files and directories.
- Usage:
  - `cp source_file destination_file`: Copies the source file to the destination.
  - `cp -r source_directory destination_directory`: Copies the source directory to the destination recursively.

### 6. `mv`

- Description: Moves or renames files and directories.
- Usage:
  - `mv source_file destination_file`: Moves the source file to the destination or renames it.
  - `mv source_directory destination_directory`: Moves the source directory to the destination or renames it.

### 7. `grep`

- Description: Searches for a specific pattern in files or output.
- Usage:
  - `grep pattern file_name`: Searches for the specified pattern in the given file.
  - `grep -r pattern directory`: Searches for the pattern recursively in the specified directory.
  - `command | grep pattern`: Filters the output of a command and searches for the pattern.

### 8. `ps`

- Description: Lists running processes.
- Usage:
  - `ps`: Lists the running processes for the current user.
  - `ps -ef`: Lists all running processes.
  - `ps -eaf`: Lists all running processes with full details.

### 9. `top`

- Description: Displays real-time system information and the list of processes.
- Usage:
  - `top`: Displays real-time system information, CPU usage, memory usage, and the list of processes.
  - Press `q` to exit the `top` command.

### 10. `tail`

- Description: Outputs the last part of a file.
- Usage:
  - `tail file_name`: Displays the last 10 lines of the specified file.
  - `tail -n N file_name`: Displays the last N lines of the specified file.
  - `tail -f file_name`: Continuously outputs new lines appended to the file.

## Here are the top 20 networking commands in Linux:

1. `ifconfig` - Displays or configures network interfaces.
2. `ip` - Shows or manipulates routing, devices, policy routing, and tunnels.
3. `ping` - Sends ICMP Echo Request packets to a specified network host.
4. `traceroute` - Traces the route packets take to reach a network host.
5. `netstat` - Displays active network connections, routing tables, and network statistics.
6. `ss` - Provides information about sockets (network connections) on a Linux system.
7. `nslookup` - Performs DNS queries to retrieve domain name or IP address information.
8. `dig` - A versatile DNS lookup utility for querying DNS servers.
9. `host` - Performs DNS lookups and displays detailed information about DNS records.
10. `route` - Shows or manipulates the IP routing table.
11. `arp` - Manipulates or displays the kernel's ARP cache and network interface settings.
12. `iwconfig` - Displays or configures wireless network interfaces.
13. `iw` - Provides information and control over wireless devices and their configuration.
14. `ssh` - Connects to a remote server using the Secure Shell protocol.
15. `scp` - Copies files securely between a local and remote host over SSH.
16. `ftp` - Transfers files to and from a remote server using the FTP protocol.
17. `wget` - Downloads files from the web using HTTP, HTTPS, or FTP protocols.
18. `curl` - A versatile command-line tool for making HTTP, HTTPS, and FTP requests.
19. `nmap` - Scans network hosts for open ports, services, and other information.
20. `tcpdump` - Captures network packets and displays them in real-time or saves them to a file for analysis.

These commands provide essential functionality for network configuration, troubleshooting, and analysis in Linux. You can refer to the respective man pages or online documentation for each command to learn more about their options and usage.

In Linux, you can change permissions and ownership of files and directories using the `chmod`, `chown`, and `chgrp` commands. Here's how you can use these commands:

## Changing Permissions

### `chmod`

The `chmod` command is used to change permissions of files and directories. It supports two modes of operation: symbolic mode and octal mode.

1. Symbolic Mode:
   - Syntax: `chmod [options] [permissions] file(s)`

   - Examples:
     - Grant read and write permissions to the owner: `chmod u+rw file.txt`
     - Revoke execute permission from the group: `chmod g-x script.sh`
     - Add read and execute permissions to others: `chmod o+rx program`
     - Combined permissions: `chmod u=rw,go=r file.txt`

2. Octal Mode:
   - Syntax: `chmod [options] [mode] file(s)`

   - Examples:
     - Set read, write, and execute permissions for owner, group, and others: `chmod 755 script.sh`
     - Restrict permissions to the owner only: `chmod 700 private.txt`
     - Grant full permissions to everyone: `chmod 777 public_dir`

## Changing Ownership

### `chown`

The `chown` command is used to change the ownership of files and directories.

- Syntax: `chown [options] owner:group file(s)`

- Examples:
  - Change the owner and group of a file: `chown john:users file.txt`
  - Recursively change ownership for a directory and its contents: `chown -R alice:staff project_dir`

### `chgrp`

The `chgrp` command is used to change the group ownership of files and directories.

- Syntax: `chgrp [options] group file(s)`

- Examples:
  - Change the group of a file: `chgrp developers script.sh`
  - Recursively change group ownership for a directory and its contents: `chgrp -R team project_dir`

In Linux, you can change permissions using the `chmod` command. The permissions determine who can read, write, or execute a file. Here's how you can use `chmod` to change permissions:

Syntax:
```
chmod [options] permissions file(s)
```

Options:
- `-R` or `--recursive`: Change permissions recursively for directories and their contents.

Permissions:
- `u` (user/owner): The owner of the file.
- `g` (group): The group associated with the file.
- `o` (others): Users who are neither the owner nor part of the group.
- `a` (all/everyone): All users, including the owner, group, and others.

Each permission has three possible settings:
- `r` (read): Permission to read the file or view directory contents.
- `w` (write): Permission to modify or delete the file or add/remove files in a directory.
- `x` (execute): Permission to execute a file or access a directory.

Examples:

1. Grant read and write permissions to the owner:
```
chmod u+rw file.txt
```

2. Revoke execute permission from the group:
```
chmod g-x script.sh
```

3. Add read and execute permissions to others:
```
chmod o+rx program
```

4. Set read and write permissions for the owner, and read-only permissions for the group and others:
```
chmod u=rw,g=r,o=r file.txt
```

5. Change permissions recursively for a directory and its contents:
```
chmod -R u+w project/
```


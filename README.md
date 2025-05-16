# Виконала самостійно Слобожан Софія РПЗ-23А
# Topic: System Service Data Storage and Network Configuration

## Objective

- To gain practical skills in working with the Bash command-line interface.  
- To become familiar with basic structures for storing system data such as processes, memory, log files, and kernel status messages.  
- To get introduced to the Filesystem Hierarchy Standard (FHS).  
- To understand the basic procedures for network configuration.
---

## Glossary of terms

1. **Pseudo Filesystems** - special file systems that do not store data on disk, but provide access to information about the system and its processes.
2. **/proc** - a directory containing information about processes and other system parameters.
3. **/var/log** - a directory containing log files that record system and program events.
4. **free** command - a utility for displaying information about memory usage in the system.
5. **Log Files** - files containing records of events that occur in the system or programs.
6. **FHS (Filesystem Hierarchy Standard)** - a standard that defines the directory structure in Unix-like systems.
7. **Network configuration commands** - commands such as ifconfig, ip, ping, netstat, which are used to configure and monitor the network.

---

## Answers to questions

### 1. Explain the concept of a “pseudo file system”, why does the system need it?

Pseudo file systems are special file systems that do not store data on physical media, but provide access to information about the state of the system, processes, hardware and other parameters. They are necessary to provide convenient access to system information, which allows administrators and users to receive data about the system in real time.

### 2. Why do users not often access the /proc directory directly, how can information be obtained from it?

Users do not access the /proc directory directly, because the information in it is presented in the form of files that may not be completely understandable without additional knowledge. Usually, commands such as cat, grep, or specialized utilities are used to obtain information from /proc, which process data from these files and present them in a convenient form.

### 3. What is the purpose of the files /proc/cmdline, /proc/meminfo and /proc/modules?

- **/proc/cmdline** - contains the command line parameters with which the system was started. This is useful for diagnostics and boot configuration.
- **/proc/meminfo** - provides information about memory usage in the system, including total, free and used memory.
- **/proc/modules** - contains information about loaded kernel modules, allowing you to check which modules are currently active.

### 4. What is the purpose of the free command?

The free command is used to display information about the use of RAM in the system. It shows total, used, free memory, as well as memory used by the cache.

### 5. What are log files for, give examples of their use?

Log files are needed to record events that occur in the system or programs. They are used for monitoring, diagnosing problems, security analysis, and tracking system changes.
Examples of use:
- Analyzing errors in web servers (for example, access.log and error.log).
- Tracking system events in the /var/log/syslog file.

### 6. What is the purpose of the /var/log/dmesg file?

The /var/log/dmesg file contains a buffer of kernel messages that are generated during system boot and kernel operation. This is important for diagnosing hardware problems and tracking kernel events.

### 7. What is the FHS for?

The FHS (Filesystem Hierarchy Standard) is a standard that defines the directory structure in Unix-like systems to unify the location of files and directories. This simplifies administration, software development, and system support.

### 8. What are the main commands in Linux for viewing and configuring the network?

Main commands:
- ifconfig – viewing and configuring network interfaces (older command).
- ip – modern utility for network management (replacement of ifconfig).
- ping – check the availability of network nodes.
- netstat – display active network connections.
- ss – modern utility for viewing sockets and network statistics.
- route – view and configure the routing table.

---
Table for describing commands:
| Command        | Purpose and Functionality                                                                                  |
|----------------|------------------------------------------------------------------------------------------------------------|
| `su`           | Switch the current user to root (superuser)                                                               |
| `ls /proc`     | List contents of the `/proc` directory (requires root access)                                              |
| `cat /proc/cmdline` | Display kernel boot parameters                                                                          |
| `cat /proc/meminfo` | Show detailed information about system memory                                                          |
| `cat /proc/modules` | Show currently loaded kernel modules                                                                    |
| `free`         | Display the amount of free and used memory in the system                                                   |
| `dmesg`        | Show kernel ring buffer messages (system boot and hardware logs)                                          |
| `ifconfig`     | Display and configure network interfaces (older tool, often replaced by `ip`)                             |
| `ip addr`      | Display IP addresses and network interfaces (modern replacement for `ifconfig`)                           |
| `ping <host>`  | Send ICMP echo requests to test connectivity to a host                                                    |
| `netstat`      | Show network connections, routing tables, interface statistics                                            |
| `ss`           | Display socket statistics and network connections (modern alternative to `netstat`)                       |
| `route`        | Show or manipulate the IP routing table                                                                   |
| `journalctl`   | Query and display logs from the systemd journal (system logs)                                             |
| `grep`         | Search for patterns in files or output streams                                                             |
| `cat`          | Display the content of files                                                                                |
# Using `cat`, `dig`, and `netstat` Commands

## Exploring the Capabilities of the `cat` Command

The `cat` command (short for "concatenate") is used to:
- display the contents of files;
- create new files;
- merge multiple files into one;
- redirect output to another file.

### Main Tasks and Examples

| Task                                           | Command                                                | Description                                                |
|------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------|
| Create a new file                              | `cat > file1.txt`                                       | Enter text manually. End with `Ctrl+D`                     |
| View file contents                             | `cat file1.txt`                                         | Displays the content of the file in the terminal           |
| Redirect content to another file               | `cat file1.txt > file2.txt`                             | Copies content from `file1.txt` into `file2.txt`           |
| Concatenate multiple files into one            | `cat file1.txt file2.txt > combined.txt`                | Merges both files into a new file                          |
| Number the lines                               | `cat -n file1.txt`                                      | Adds line numbers to each line                             |
| Show non-printable characters                  | `cat -v file1.txt`                                      | Displays special characters like ^M, ^I                    |
| Suppress repeated empty lines                  | `cat -s file1.txt`                                      | Removes consecutive blank lines                            |

---

## The `dig` Command (Domain Information Groper)

The `dig` command is used to query DNS servers for domain-related information.

### Key Features and Examples

| Command Example                | Description                                               |
|-------------------------------|-----------------------------------------------------------|
| `dig google.com`              | Retrieves A records (IP addresses) for the domain         |
| `dig +short google.com`       | Short format output (only IP addresses)                   |
| `dig google.com MX`           | Retrieves mail servers (MX records) of the domain         |
| `dig google.com ANY`          | Fetches all available DNS records                         |
| `dig @8.8.8.8 google.com`     | Uses a specific DNS server for the query (Google DNS)     |

---

## The `netstat` Command

The `netstat` command shows network statistics, active connections, routing tables, listening ports, etc.

### Key Features and Examples

| Command Example          | Description                                                         |
|--------------------------|----------------------------------------------------------------------|
| `netstat -a`             | Displays all active connections and listening ports                 |
| `netstat -tuln`          | Lists all TCP/UDP connections without resolving hostnames           |
| `netstat -p`             | Shows which process is using each connection                        |
| `netstat -r`             | Displays the system routing table                                   |
| `netstat -s`             | Shows protocol statistics (TCP, UDP, etc.)                          |

---
## Screenshots for tasks
![image](https://github.com/user-attachments/assets/fefb8132-0fc4-4d62-9e14-847d3f1c67f8)
![image](https://github.com/user-attachments/assets/bf0109cf-27de-49f5-985a-d94111bac5e6)
![image](https://github.com/user-attachments/assets/5d13455d-3d35-40fe-ada0-a33980c2be56)
![image](https://github.com/user-attachments/assets/9b825b1b-c461-4202-b47f-068b06d792ff)
![image](https://github.com/user-attachments/assets/195db2b6-f45b-418d-bd46-6f2e9f6bd762)
![image](https://github.com/user-attachments/assets/00664730-bb7d-4d99-b4d3-51900d0b5337)
![image](https://github.com/user-attachments/assets/621e4983-6442-48e2-ab6e-8f870fcfbb55)
![image](https://github.com/user-attachments/assets/9cf1a35c-2289-4132-acc8-e5733bb0e47f)
![image](https://github.com/user-attachments/assets/fba9d323-fc7a-4716-ba97-d59fffaed65b)

## Summary

As a result of this lab work, the basic functionalities of the cat, dig, and netstat commands were explored and practiced. The cat command is useful for working with text files — viewing, creating, and merging them. The dig command is used for querying DNS and analyzing domain information, while netstat provides insight into network connections and open ports. The knowledge gained forms a solid foundation for further learning in system and network administration.

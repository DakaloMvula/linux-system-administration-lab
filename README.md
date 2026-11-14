# Linux System Administration Lab

## Project Overview

This project demonstrates practical Linux system administration skills using Ubuntu Linux in an Oracle VirtualBox virtual machine.

The project was completed as part of the **Linux-Based Operating Systems (ITLSA)** module at Eduvos, within the Bachelor of Science in Information Technology programme.

The practical work focuses on essential Linux administration tasks, including file system management, Bash scripting, user and group administration, file permissions, network troubleshooting, system monitoring, and package management.

The project uses a simulated IT environment for **TechNet Solutions**, where an IT administrator is responsible for maintaining Linux workstations and servers, automating administrative tasks, managing user access, and troubleshooting system performance.

## Project Objectives

The main objectives of this project were to:

- Develop practical Linux command-line skills.
- Understand the Linux directory structure and file system.
- Perform file and directory management operations.
- Automate repetitive administrative tasks using Bash scripts.
- Configure Linux users, groups, and file permissions.
- Troubleshoot network connectivity and DNS resolution.
- Monitor system resources and running processes.
- Manage software packages using the APT package manager.
- Gain practical experience administering Linux systems in a virtualised environment.

## Technologies and Tools Used

| Technology | Purpose |
|---|---|
| Ubuntu Linux | Operating system used for practical administration |
| Oracle VirtualBox | Virtualisation platform for the Linux environment |
| Bash | Shell scripting and command-line automation |
| Linux Terminal | Executing administrative commands |
| GNU Nano | Creating and editing text files and scripts |
| APT Package Manager | Installing and removing software packages |
| Linux Networking Utilities | Network connectivity and DNS troubleshooting |

---

## Lab 1: Linux File System and Directory Management

### Objective

The objective of this lab was to understand the Linux directory structure and demonstrate practical file and directory management using terminal commands.

### Understanding the Linux Directory Structure

The following Linux directories were examined:

| Directory | Description |
|---|---|
| `/home` | Stores user home directories and personal files |
| `/etc` | Contains system-wide configuration files |
| `/var` | Stores variable data such as logs and temporary application data |
| `/bin` | Provides essential executable commands |
| `/usr` | Contains applications, utilities, libraries, and shared resources |

### Practical Implementation

**1. Navigating the Linux file system**

The `/etc` directory was accessed to inspect system configuration files.

```bash
cd /etc
ls
```

**2. Creating a workspace directory**

A directory named `intern_workspace` was created inside the user's home directory.

```bash
mkdir ~/intern_workspace
```

**3. Creating and editing a text file**

A file named `report.txt` was created containing the text `Linux Audit Report`.

```bash
echo "Linux Audit Report" > ~/intern_workspace/report.txt
```

**4. Displaying file contents**

The `cat` command was used to display the contents of the text file.

```bash
cat ~/intern_workspace/report.txt
```

**5. Moving a file**

The report file was moved into the `/tmp` directory.

```bash
mv ~/intern_workspace/report.txt /tmp/
```

**6. Deleting a file**

The file was removed from the temporary directory.

```bash
rm /tmp/report.txt
```

**7. Displaying the current working directory**

```bash
pwd
```

### Skills Demonstrated

- Linux file system navigation
- Directory creation
- File creation and editing
- File relocation and deletion
- Command-line file inspection
- Understanding Linux directory structures

---

## Lab 2: Bash Scripting and Backup Automation

### Objective

The objective of this lab was to demonstrate how Bash scripting can automate repetitive Linux administration tasks.

The scenario involved backing up configuration files from the `/etc` directory to reduce manual administrative work.

### Bash Script Implementation

A Bash script named `backup.sh` was developed to:

1. Create a backup directory in the user's home directory.
2. Copy configuration files with the `.conf` extension from `/etc`.
3. Display a confirmation message after the backup operation.

### Example Backup Script

The following is an illustrative version of the backup workflow. It is not a verified copy of the original submitted script.

```bash
#!/bin/bash

# Create a backup directory
mkdir -p "$HOME/backup"

# Copy configuration files into the backup directory
cp /etc/*.conf "$HOME/backup/"

# Display confirmation message
echo "Backup completed successfully!"
```

### Making the Script Executable

```bash
chmod +x backup.sh
```

### Executing the Script

```bash
./backup.sh
```

### Verifying Backup Files

```bash
ls ~/backup
```

### Benefits of Bash Scripting

**Automation:** Bash scripts allow administrators to perform repetitive tasks without manually entering the same commands multiple times.

**Efficiency:** Automated administrative operations reduce the time required to perform routine system maintenance.

**Consistency:** Scripts help ensure that the same administrative procedures are followed during repeated operations.

### Skills Demonstrated

- Bash scripting
- Task automation
- Configuration file management
- Script execution permissions
- Basic backup administration

**Note:** This lab demonstrates local configuration-file copying. It does not implement scheduled backups, cloud uploads, or a complete disaster recovery solution.

---

## Lab 3: Linux User and Group Administration

### Objective

The objective of this lab was to demonstrate Linux user account management, group administration, file ownership, and access permissions.

The scenario involved onboarding a new developer and configuring access to Linux resources.

### Practical Implementation

**1. Creating a Linux user**

The `adduser` command was used to create a new user account.

```bash
sudo adduser new_user
```

**2. Creating a group**

A group named `staff` was created.

```bash
sudo groupadd staff
```

**3. Adding a user to a group**

```bash
sudo usermod -aG staff new_user
```

**4. Creating a welcome file**

```bash
sudo touch /home/new_user/welcome.txt
```

**5. Configuring file ownership**

The ownership of the file was assigned to the user and the `staff` group.

```bash
sudo chown new_user:staff /home/new_user/welcome.txt
```

**6. Configuring file permissions**

File permissions were modified so that only the owner could read and write to the file.

```bash
sudo chmod 600 /home/new_user/welcome.txt
```

### Understanding Linux Permissions

Linux uses file permissions to control access to files and directories.

The three main permission categories are:

- **Read (r):** Permission to read file contents.
- **Write (w):** Permission to modify file contents.
- **Execute (x):** Permission to execute a file or access a directory.

### Important Linux Administration Commands

| Command | Purpose |
|---|---|
| `adduser` | Creates a user account |
| `groupadd` | Creates a group |
| `usermod` | Modifies user account properties |
| `chmod` | Modifies file permissions |
| `chown` | Changes file ownership |
| `chgrp` | Changes group ownership |

### Skills Demonstrated

- Linux account administration
- User and group management
- File ownership configuration
- Linux permission management
- Basic access control principles

---

## Lab 4: Linux Network Troubleshooting and System Performance Monitoring

### Objective

The objective of this lab was to diagnose network connectivity issues and inspect system resource utilisation on an Ubuntu Linux workstation.

### Part A: Network Troubleshooting

**1. Verifying network connectivity**

The `ping` command was used to test connectivity to an external destination.

```bash
ping -c 4 google.com
```

This command sends four ICMP echo requests to test connectivity.

**2. Displaying network interface information**

```bash
ip address show
```

This command displays information about the system's network interfaces, including configured IP addresses.

**3. Viewing listening ports and network sockets**

```bash
ss -tulnp
```

This command displays TCP and UDP sockets, including listening ports and available process information.

**4. Tracing the network route**

```bash
traceroute google.com
```

The `traceroute` command helps identify the network path taken by packets towards a destination.

**5. Testing DNS resolution**

```bash
nslookup google.com
```

This command queries DNS to resolve a domain name to its associated IP addresses.

### Part B: System Performance Monitoring

**1. Checking available disk space**

```bash
df -h
```

The command displays file system disk usage in a human-readable format.

**2. Monitoring memory-intensive processes**

```bash
top
```

The `top` utility was used to inspect running processes and system resource consumption.

Processes were sorted by memory utilisation to identify applications consuming significant system resources.

**3. Installing software packages**

The APT package manager was used to install Python 3.

```bash
sudo apt install python3
```

**4. Removing installed software**

```bash
sudo apt remove python3
```

This demonstrated package removal in a controlled lab environment.

**Note:** Removing Python 3 from a working Ubuntu installation can affect applications that depend on it. This operation should only be performed after reviewing package dependencies.

### Skills Demonstrated

- Network connectivity troubleshooting
- Network interface inspection
- DNS troubleshooting
- Network route analysis
- Socket and port inspection
- Disk utilisation monitoring
- Process monitoring
- Linux package management

---

## Practical Skills Gained

Through this project, I developed practical experience in the following areas:

### Linux Administration

- Working with the Linux command-line interface.
- Navigating and managing the Linux file system.
- Creating and managing files and directories.
- Configuring file ownership and permissions.

### Scripting and Automation

- Writing basic Bash scripts.
- Automating repetitive administrative operations.
- Executing scripts and managing execution permissions.
- Performing local configuration-file backups.

### User and Access Management

- Creating Linux user accounts.
- Creating and managing user groups.
- Assigning group membership.
- Configuring file access restrictions.

### Networking

- Testing network connectivity.
- Inspecting network interface configurations.
- Investigating network routes.
- Performing DNS queries.
- Inspecting listening ports and network sockets.

### System Monitoring

- Checking disk utilisation.
- Monitoring running processes.
- Identifying memory-intensive applications.
- Installing and removing Linux software packages.

---

## Project Environment

The practical activities were performed using Ubuntu Linux installed inside an Oracle VirtualBox virtual machine.

This virtualised environment provided a controlled setting for executing Linux commands, configuring user accounts, creating scripts, and testing administrative operations.

Virtualisation made it possible to practise system administration without modifying the host operating system.

---

## Project Outcomes

The project provided practical exposure to Linux system administration and reinforced the importance of command-line proficiency in IT operations.

Key learning outcomes included:

- Understanding the structure and organisation of Linux operating systems.
- Managing files and directories through terminal commands.
- Using Bash scripting to automate administrative tasks.
- Applying file ownership and permissions to control access.
- Diagnosing common network connectivity problems.
- Monitoring Linux system resources.
- Managing software packages through the command line.

These skills provide a foundation for further learning in Linux server administration, network engineering, cybersecurity, and IT infrastructure management.

---

## Future Improvements

Potential improvements to this project include:

- Implementing scheduled backups using Cron.
- Adding backup verification and error handling.
- Implementing automated system health monitoring.
- Configuring SSH for secure remote administration.
- Introducing centralised logging and log analysis.
- Exploring Linux firewall configuration using UFW.
- Expanding Bash scripts to support additional administrative tasks.

These improvements are proposed future enhancements and were not part of the documented implementation.

---

## Author

**Bradley Dakalo Mvula**

**Areas of Interest:**
- Cybersecurity
- Network Engineering
- Linux System Administration
- IT Infrastructure
- Network Security

---

## Disclaimer

This repository documents practical Linux administration activities completed in an educational lab environment.

Commands and scripts are provided for learning and demonstration purposes. Administrative operations should be tested and reviewed before being applied to production systems.

The project is intended to demonstrate foundational Linux administration skills and practical technical experience.

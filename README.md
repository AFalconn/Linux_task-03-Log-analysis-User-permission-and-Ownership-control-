# Linux User Management, Permissions & Log Analysis Lab

## Project Overview

This project demonstrates practical Linux system administration and foundational cybersecurity skills through user account management, file permissions, ownership control, and system log analysis.

The exercise focuses on managing user access, generating and filtering mock system event logs, controlling access to confidential files, and performing basic user administration using Linux command-line utilities.

The lab simulates common responsibilities encountered in cybersecurity operations, Linux administration, and Security Operations Center (SOC) environments.

## Objectives

The objectives of this lab were to:

- Create and configure Linux user accounts.
- Manage user privileges using the `sudo` group.
- Create directories and generate mock system event logs.
- Search, filter, and inspect logs using Linux text-processing commands.
- Redirect command output into report files.
- Apply file permissions using `chmod`.
- Change file ownership using `chown`.
- Observe how file ownership and permissions affect access.
- Create, modify, and delete user accounts using Linux user management commands.

## Tools and Technologies

| Tool / Command | Purpose |
|---|---|
| Linux Terminal | Executing administrative commands |
| `useradd` | Creating user accounts |
| `passwd` | Setting user passwords |
| `usermod` | Modifying user account properties and group membership |
| `userdel` | Deleting user accounts |
| `sudo` | Executing authorized administrative commands |
| `grep` | Searching logs for specific keywords |
| `less` | Viewing command output interactively |
| `head` and `tail` | Displaying the beginning and end of log files |
| `cat` and `echo` | Creating and viewing text files |
| `chmod` | Changing file permissions |
| `chown` | Changing file ownership |
| `>` and `\|` | Redirecting and piping command output |

## Lab Environment

- Operating System: Linux
- User account: `Sugar`
- Additional accounts: `guest1` and `guest2`
- Working directory: `/home/forensic01/logs/`
- Log file: `sys_events.log`
- Report file: `error_report.txt`
- Restricted file: `confidential.txt`

Administrative commands were performed using `sudo` where required.

## Part 1: New User Setup and Access Control

### Tasks Performed

1. Created a Linux user named `Sugar` with a home directory and Bash shell.
2. Added the user to the `sudo` group.
3. Set a password for the account.
4. Switched to the newly created user.
5. Created a dedicated directory for log analysis.
6. Generated a mock system event log containing timestamps and entries with `ERROR`, `WARNING`, `INFO`, `user01`, and `root`.

### Commands Practised

```bash
sudo useradd -m -s /bin/bash Sugar
sudo usermod -aG sudo Sugar
sudo passwd Sugar
su - Sugar
mkdir -p /home/Sugar/logs
cd /home/Sugar/logs
```

The mock log file was created using `cat` and `echo` to simulate system events for investigation and filtering practice.

## Part 2: Log Filtering and Analysis

### Tasks Performed

The `sys_events.log` file was examined to identify error messages, locate entries mentioning specific users, and inspect log activity.

**Search for error messages**

```bash
grep "ERROR" sys_events.log
```

This command displays all lines containing the `ERROR` keyword.

**Search for root or user01**

```bash
grep -E "root|user01" sys_events.log
```

This command uses an extended regular expression to find lines containing either `root` or `user01`.

**Pipe results into less**

```bash
grep "ERROR" sys_events.log | less
```

Piping the search results into `less` allows the output to be reviewed interactively.

**Save the error report**

```bash
grep "ERROR" sys_events.log > error_report.txt
```

The matching error entries are redirected into `error_report.txt` for documentation and further review.

**Display the first five lines**

```bash
head -n 5 sys_events.log
```

**Display the last five lines**

```bash
tail -n 5 sys_events.log
```

**Display the complete log file**

```bash
cat sys_events.log
```

### Security Relevance

Log filtering is a foundational skill in cybersecurity investigations. Searching for error messages, account names, and privileged users can help analysts identify events that require further investigation.

The exercise also demonstrates how command output can be preserved in a report file for documentation and review.

## Part 3: File Permissions and Ownership Control

### Tasks Performed

1. Created `confidential.txt` in the logs directory.
2. Restricted file access so that only the owner had read and write permissions.
3. Changed the file owner to `root` using `sudo`.
4. Attempted to read or edit the file as `Sugar`.
5. Observed how ownership and permissions affected access.

### Commands Practised

**Create the confidential file**

```bash
touch confidential.txt
```

**Set owner-only read and write permissions**

```bash
chmod 600 confidential.txt
```

The permission mode `600` grants read and write access to the owner while denying permissions to the group and others.

**Change ownership to root**

```bash
sudo chown root:root confidential.txt
```

**Inspect file ownership and permissions**

```bash
ls -l confidential.txt
```

### Key Learning

Linux uses ownership and permission rules to control access to files and directories.

After ownership was changed to `root`, the `Sugar` account no longer had owner-level access to the file. Because the permissions were set to `600`, ordinary access by `Sugar` was denied unless the account had an applicable privilege or another access mechanism.

This demonstrated why correct ownership and permissions are essential for protecting sensitive information.

## Part 4: User Management Commands

### Tasks Performed

- Created two temporary users named `guest1` and `guest2`.
- Added `guest1` to the `sudo` group.
- Deleted `guest2` and removed its home directory.

### Commands Practised

**Create temporary users**

```bash
sudo useradd -m guest1
sudo useradd -m guest2
```

**Add guest1 to the sudo group**

```bash
sudo usermod -aG sudo guest1
```

**Verify group membership**

```bash
groups guest1
```

**Delete guest2 and its home directory**

```bash
sudo userdel -r guest2
```

These operations demonstrate the importance of maintaining user accounts and applying administrative privileges only where required.

## Skills Demonstrated

- Linux command-line navigation and file management
- User account creation and administration
- Privilege and group management
- Log filtering and basic event investigation
- Output redirection and command piping
- File permission configuration
- File ownership management
- Access control verification
- Basic security documentation and reporting

## Repository Structure

```text
linux-user-management-log-analysis/
├── README.md
├── logs/
│   ├── sys_events.log
│   ├── error_report.txt
│   └── confidential.txt
├── screenshots/
│   ├── user-creation.png
│   ├── log-analysis.png
│   ├── file-permissions.png
│   └── user-management.png
└── docs/
    └── lab-notes.md
```



## Conclusion

This lab strengthened my understanding of Linux user administration, access control, file ownership, and log analysis. It provided practical experience with essential command-line tools used to manage accounts, investigate events, and protect sensitive files.

These skills form part of my ongoing cybersecurity development, particularly in Linux security, system administration, and foundational SOC operations.

## Author

**Amarachi Faith**

Cybersecurity Professional

- GitHub: [https://github.con/AFalconn]
- LinkedIn: [https://www.linkedin.com/in/amarachi-faith]


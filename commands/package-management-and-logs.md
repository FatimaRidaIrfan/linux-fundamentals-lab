# Package Management and Logs 

## 1. Package Management

Package management helps install, update, upgrade, and remove software on Linux.

On Debian-based distributions such as Debian and Ubuntu, apt is commonly used to manage packages.

Common APT Commands

| Command | Purpose | 
| --- | --- | 
| `sudo apt update` | Checks for the available updates. | 
| `sudo apt upgrade` | Install those updates. | 
| `sudo apt install PACKAGE` | Installs a package. | 
| `sudo apt remove PACKAGE` | Removes a package but generally leaves its configuration files. | 
| `apt search KEYWORD` | Searches for packages. | 
| `apt show PACKAGE` | Displays package information. | 

Important: `apt` update refreshes package lists; it does not itself upgrade installed software.

## 2. Checking Services. 

Linux services commonly run in the background. On systems using `systemd`, `systemctl` manages and inspects services.

| Command | Purpose | 
| --- | --- | 
| `systemctl status SERVICE` | Displays service's status. | 
| `systemctl is-active SERVICE` | Checks whether a service is active. | 
| `systemctl is-enabled SERVICE` | Checks whether a service is configured to start automatically. |

Example : 
- `systemctl status ssh` 

The service name may differ across distributions. Some systems use `sshd` instead of `ssh`.

## 3. Viewing System Logs

Logs record system events, application activity, errors, and other informations. 

On systems using `systemd`, `journalctl` is commonly used to read the system journal.

| Command | Purpose | 
| --- | --- | 
| `journalctl` | Displays journal entries. | 
| `journalctl -u SERVICE` | Displays logs for a specific service. | 
| `journalctl --since today` | Displays entries since the start of the current day. | 
| `journalctl -f` | Follows new log entries as they appear. | 

Example : 
`journalctl -u ssh --since today` - This displays today's journal entries for the SSH service, if available.

## 4. Troubleshooting

When a service or application fails we may troubleshoot the problem by the following steps.

- 1.Check the service status using `systemctl status`.
- 2.Review relevant logs using `journalctl`.
- 3.Identify error messages and investigate their causes.
- 4.Check whether the system has sufficient disk space using `df -h`.
- 5.Check for available package updates when appropriate.
- 6.Apply a fix and verify that the issue is resolved.

## Summary :

- `apt update` refreshes package information.
- `apt upgrade` upgrades installed packages.
- Repositories provide packages and metadata.
- `systemctl` status helps inspect services.
- `journalctl` helps investigate system and service events.
- Logs support troubleshooting and security monitoring.
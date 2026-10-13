 # Linux Users and Groups 

## 1. Introduction to Linux Users and Groups
Linux users and groups help administrators control who can access files, use resources, and perform administrative tasks. For example, a company server may have developers, system administrators, and applications running under different accounts. Each account should receive only the access it needs.

Users and groups are important because they help protect sensitive information, prevent unauthorized access, and improve system security.

## 2. Understanding Users 

Linux uses user identities to determine what actions a process is allowed to perform.
There are two common categories of user accounts -
- Regular users: Accounts generally used by people for everyday activities. They usually have limited privileges.

- System users: Accounts commonly created for services and applications. For example, a web server may use its own account rather than running as root.

Every user has a unique UID (User ID), which Linux uses to identify the account.

To display your current username, use:
`whoami`

To display your user ID and group information, use:
`id`
Example output:
```text 
uid=1000(rida) gid=1000(rida) groups=1000(rida),27(sudo)
```
This is an example of the output produced by the `id` command.

In this example : 

`uid=1000(rida)` identifies the user `rida`, whose UID is `1000`.
`gid=1000(rida)` identifies the user's primary group.
`groups=1000(rida)`,`27(sudo)` lists the groups the user belongs to.

## 3. Understanding Groups

A group is a collection of user accounts. Groups make it easier to manage permissions for multiple users without configuring each user separately. For example, a company may create a group named developers for employees working on the same project. A directory can be assigned to that group, and its permissions can be configured to provide the required access to group members.

Every group has a GID (Group ID), which identifies the group.

To display which groups you belongs to, run :
`groups` 

To look up a particular group, such as sudo, run:
`getent group sudo`

The main difference is:

- UID: Identifies a user.
- GID: Identifies a group.

## 4. Important Commands for Managing and Inspecting Users and Groups

Linux provides commands to inspect account information and group memberships.

| Command | Purpose |
|---|---|
| `whoami` | Displays the effective username. |
| `id` | Displays the user's UID, primary GID, and group memberships. |
| `groups` | Displays the groups associated with a user. |
| `getent passwd` | Displays user account entries from configured account databases. |
| `getent group` | Displays group entries from configured account databases. |
| `who` | Shows logged-in users when their login sessions are recorded. |

Examples :
- `whoami`
- `id`
- `groups`
- `getent passwd`
- `getent group`
- `who`

These commands help administrators know which accounts exist, what groups they belong to, and who is currently logged in.

## 5. Understanding the Root User

The root user is the main administrative account on a Linux system. Its UID is 0, and it normally has most privileges over the operating system.

The root account can perform tasks such as:
- Installing or removing system-wide software.
- Modifying protected system configuration files.
- Managing user accounts and groups.
- Changing file ownership and permissions.
- Managing system services.

A safer approach is to use a regular account for everyday activities and use elevated privileges only when necessary.

## 6. Understanding sudo

The `sudo` command allows an authorized user to execute a command with elevated privileges according to the system's security policy.

Example : 
`sudo apt update` - This runs the package-list update with administrative privileges.

Not every user can automatically use the `sudo` command . The system's configuration determines which users are allowed to use it and which commands they can run.

You can know your user and group information using:
`id` 
If your output includes the sudo group, than you may have administrative access on a typical Debian installation. However, actual authorization depends on the system's configuration.

For security purposes it is better to grant administrative access only to users who need it. 

## 7. Important Linux User and Group Files 

Linux stores local user and group account information in several important files.

| File | Purpose |
|---|---|
| `/etc/passwd` | Stores local account information such as usernames, UIDs, home directories, and login shells. |
| `/etc/shadow` | Stores protected password hashes and password-aging information for local accounts. |
| `/etc/group` | Stores local group information and supplementary group membership listings. |
| `/etc/gshadow` | Stores protected group administration information. |

To view local user account entries, use:
`cat /etc/passwd`

To view local group entries, use:
`cat /etc/group`

The `/etc/passwd` file does not normally contain users' actual passwords. Modern Linux systems generally store password hashes in `/etc/shadow`, which is more restricted.

## 8. User and Group Management Commands

Linux provides administrative commands for creating, modifying, and removing accounts and groups.

| Command | Purpose |
|---|---|
| `useradd` | Creates a user account. |
| `usermod` | Modifies an existing user account. |
| `userdel` | Deletes a user account. |
| `groupadd` | Creates a group. |
| `groupmod` | Modifies a group. |
| `groupdel` | Deletes a group. |

## 9. The Principle of Least Privilege

The principle of least privilege means giving users and services only the permissions they need to perform their tasks.

For example:

- A regular user should not receive administrator privileges without a valid reason.
- A web server should use an appropriately restricted service account when possible.
- Members of a development team should receive access to the project files they need.
- Sensitive system files should not be writable by ordinary users.

## 10. Why Users and Groups Matter for Linux Security

Incorrect user and group configuration can create security problems. For example, granting administrative privileges to unnecessary accounts increases risk. Giving a group access to sensitive files may expose information to people who do not need it.

Proper user and group management helps administrators:
- Restrict access to sensitive resources.
- Separate regular work from administrative tasks.
- Manage shared resources efficiently.
- Reduce unnecessary privileges.
- Improve accountability and system security.

Users, groups, and file permissions work together to control access on Linux systems.

## 11. Key Points to Take Away 

- Linux is a multi-user operating system.
- A user represents a person or service account.
- A group allows permissions to be managed for multiple users.
- UID identifies a user, while GID identifies a group.
- whoami, id, and groups help inspect account information.
- root is the main administrative account, normally identified by UID 0.
- sudo allows authorized users to execute commands with elevated privileges.
- /etc/passwd, /etc/shadow, /etc/group, and /etc/gshadow serve different purposes.
- Least privilege helps reduce security risks.
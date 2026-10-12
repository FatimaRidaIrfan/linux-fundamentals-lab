# Linux File Permissions. 

## 1. Introduction to Linux File Permissions.

Linux file permissions control who can access files and directories and what actions they can perform. They help in protecting private information, prevent unauthorized modifications, and reduce security risks.

For example, a regular user should not automatically be allowed to access important system configuration files. Permissions help restrict access to authorized users.

Linux permissions are based on three categories: owner, group, and others. Each category can have (`r`) read, (`w`) write, and (`x`) execute permissions.

## 2. Understanding `r`, `w`, and `x` 

`r` - (Read Permission) Allows a user to view a file's contents. For a directory, it allows the user to list its entries, subject to other permissions.

`w` - (Write Permission) Allows a user to modify a file's contents. For a directory, it allows creating, deleting, or renaming entries when the required directory permissions are present.

`x` - (Execute Permission) Allows a user to execute a program or script when other requirements are met. For a directory, it allows traversing it and accessing entries by name, subject to permissions.

A permission can be present or absent for each category. For example, a file may allow its owner only to read and write while allowing other users just to read it.

## 3. Owner, Group and Others 

A file is associated with an owner and a group

**Owner**: The user who owns the file.
**Group** : The group which is associated with the file. Group members may receive the permissions assigned to that category.
**Others** : Users who are neither the owner nor members of the file's group. 

This separation is useful when multiple people use the same Linux system. For example, a team may share read access to a project file without allowing write permission.

## 4. Checking permissions with `ls -l`

`ls -l` : This command displays a detailed listing of files and directories, including their permissions, ownership, size, and modification time.

Example output
-rwxr-xr-- 1 rida developers 1200 Oct 10 10:30 script.sh

The permission string for this file is -rwxr-xr--

`-` indicates a regular file whereas a d indicates a directory.
`rwx` represent the owner's permissions. Which are read, write and execute.
`r-x` represent the group's permissions. Which are to read and execute.
`r--` represent the permissions for others. Which is only to read.

Therefore the owner can read, write, and execute the file. The group can read and execute it, while others can only read it.

## 5. Changing permissions with chmod.
`chmod` command changes file or directory permissions. It uses symbolic notation and numeric notation.

Symbolic notation - Uses letters to identify the permission category and the action.
`u` means owner (user)
`g` means group 
`o` means others 
`a` means all catogories
`+` adds persmissions, `-` removes them, `=` sets the specified permissions for the selected categories. 

Examples 

```bash
chmod u+x script.sh
chmod g-w notes.txt
chmod o=r notes.txt
```

The first command adds execute permission for the owner. The second removes write permission from the group. The third sets others permissions to read only.

Numeric notation - Use three digits: owner, group, and others. Each digit is calculated by adding the values of the permissions.

Permission	Value
Read (`r`)	4
Write (`w`)	2
Execute (`x`)	1

`rwx` = 4 + 2 + 1 = 7
`rw`- = 4 + 2 = 6
`r-x` = 4 + 1 = 5

Read plus write equals (4+2=6). Read plus execute equals (4+1=5). Read, write, and execute together equal (4+2+1=7)

Example mode - `chmod 700` :(4+2+1 = 7) where owner has the permission to read write and execute, whereas group and others have no permissions.

## 6. Changing ownership with chown
The `chown` command changes file ownership. Its general syntax is - 

```bash
chown USER:GROUP FILE
```

Example 

```bash
sudo chown rida:developers notes.txt
```
This sets `rida` as the owner and `developers` as the group of notes.txt

## 7. Why permissions matter for Linux security. 

Incorrect permissions can expose important information, allow unauthorized changes, or let users execute files they should not be able to run. It is safer to practise permission changes on test files and directories rather than changing important system files without understanding the consequences.

## 8. Key points to take away.

Linux permissions regulate access to files and directories.
`r`, `w`, and `x` represent read, write, and execute.
Permissions are assigned to owner, group, and others.
`ls -l` helps inspect permissions and ownership.
`chmod` changes permissions; chown changes ownership.

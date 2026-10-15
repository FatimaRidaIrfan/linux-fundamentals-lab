# Linux Filesystem and Storage

## 1. Linux Filesystem Hierarchy

Linux organizes files and directories in a hierarchical structure that starts at the root directory `/`.

| Directory | Purpose | 
| --- | --- |
| `/` |Root of the entire filesystem. |
| `/home` | Personal directories of regular users. |
| `/etc` | System-wide configuration files. |
| `/var` | Variable data, including logs and caches. |
| `/tmp` | Temporary files. |
| `/dev` | Device files representing hardware and virtual devices. |
| `/boot` | Files needed to start the system. |
| `/usr` | Many user-space programs, libraries, and shared data. |
| `/opt` | Optional application software. |
| `/mnt` | Common temporary mount point for filesystems. |
| `/media` | Common mount point for removable media. |

## 2. Disk, Partition, and Filesystem

These three concepts are related but different.

- Disk : A storage device, such as an SSD or virtual disk.

- Partition: A logical section of a disk.

- Filesystem: A structure that organizes and stores files and directories within a storage area.

## 3. Common Linux Filesystems

| Filesystem | Common use |
| --- | --- | 
| `ext4` | Common Linux filesystem. | 
| `FAT32` | Broad compatibility with devices; individual files are limited to 4 GiB. |
| `exFAT` | Commonly used for removable storage and large files. |

The appropriate filesystem depends on the operating system, workload, compatibility requirements, and storage needs.

## 4. Useful Storage Commands

- `lsblk` - Displays devices and their relationships.
- `lsblk -f` - Displays filesystem information, labels, UUIDs, and mount points when available.

- `df -h` - Displays filesystem space usage in human-readable units.

- `du -sh` - Shows the total space used by a directory.
- `du -sh ~` - Checks directory size. 

- `findmnt` - Displays mounted filesystems and their mount points.

- `mount and umount` - These commands are used to mount and unmount filesystems.

## 5. Swap Space 

Swap space provides the system with additional virtual-memory capacity. Linux can use swap when memory pressure increases. Swap can be implemented using a dedicated partition or a swap file.

Commands 

`free -h` - Displays memory and swap usage.

`swapon --show` - Lists active swap areas.

## Summary : 

- `/` is the root of the Linux filesystem hierarchy.
- A disk is a storage device, a partition is a section of a disk, and a filesystem organizes files.
- `lsblk` displays block devices.
- `df -h` reports filesystem space usage.
- `du -sh` reports directory space usage.
- `findmnt` displays mounted filesystems.
- `free -h` and swapon --show help inspect memory and swap.
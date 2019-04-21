# Setting up Permissions to a File or Directory

## Introduction

In Unix file systems, permissions are divided into 2 parts:

* **Ownership**: with 3 levels (user `u`, group `g` and other `o` - all `a`)
* **Access Type**: with 3 access types (read `r`, write `w` and execute `x`).

Each level of ownership can be granted any or all of the access types. 

## Permissions for a particular ownership level

Use the `chmod` command:

```bash
$ chmod [ownership][+/-][access type] [file path]
```

Examples:

```bash
# Allow write access to everyone
$ chmod +w sample.txt

# Remove read access for the user
$ chmod u-r sample.txt

# Add execute access for everyone (a = all)
$ chmod a+x sample.txt
```

## Permissions for all ownership levels

To set the permissions for the user, group and other all at once, you can do so with 3 numbers ranging from 0 to 7 (2^3 = 8 permission levels per ownership).

| Number | Permission                  |
| ------ | --------------------------- |
| 0      | No permission granted       |
| 1      | Can execute                 |
| 2      | Can write                   |
| 3      | Can  write and execute      |
| 4      | Can read                    |
| 5      | Can read and execute        |
| 6      | Can read and write          |
| 7      | Can read, write and execute |

To set permissions, you combine the 3 numbers in one (owner > group > other):

```bash
# Grant the owner full access, the group read and execute and the other read access
$ chmod 754 test.sh
$ ls -l test.sh
-rwxr-xr-- 1 bob admin 0B Jul 15 15:24 test.sh
```

To change the permission of a file or directory, you must be its owner, or be root, or use sudo.

---
TIL #1 - 21/04/2019

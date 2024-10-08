# Ninth Dojo: Perceiving Permissions

## 1. Understanding File Ownership
- Each file in Linux is owned by a user and a group.
- Ownership can be changed using `chown` (for both user and group) or `chgrp` (only for group).
- **Examples**:
  ```bash
  chown user:group filename
  chgrp groupname filename

## 2. File Permissions Breakdown
- Permissions are represented by three sets of `rwx` (read, write, execute) for the user, group, and others.
- **Example**: 
  - `rwxr-xr--`: User can read, write, and execute; group can read and execute; others can only read.
- **Permission Characters**:
  - `r` – read
  - `w` – write
  - `x` – execute
  - `-` – no permission

## 3. Changing Permissions with `chmod`
- `chmod` (change mode) allows users to change file permissions.
- Basic usage: `chmod [OPTIONS] MODE FILE`
- Modes can be specified to add or remove permissions:
  - `u+r`: Adds read access for the user.
  - `g+wx`: Adds write and execute access for the group.
  - `o-w`: Removes write access for others.
  - `a-rwx`: Removes all permissions for user, group, and others.
- Permissions can also be set entirely with `=`:
  - `u=rw`: Sets user permissions to read and write.
  - `o=x`: Sets only execute permissions for others.
  - Chaining modes is possible:
    - `chmod u=rw,g=r /challenge/pwn`: Sets user to read and write, group to read-only.
    - `chmod u=rw,g=r,o=- /challenge/pwn`: Sets user to read and write, group to read-only, and others to no permissions.

## 4. Set User ID (SUID) Permissions
- The "Set User ID" (SUID) permission allows a user to run a program as the owner of that program's file.
- A file with SUID has an "s" in place of the executable bit:
  - Example: `-rwsr-xr-x`: The "s" indicates that the file can be executed with SUID.
- When executed, the program runs as the owner (e.g., root), regardless of who runs it.
- To set the SUID bit on a program, use:
  - `chmod u+s [program]`
- Caution: Giving SUID to a program owned by root can create security vulnerabilities.

## 5. Changing Permissions with `chmod`
- The `chmod` command modifies file permissions.
- You can set permissions using:
  - `u`: user
  - `g`: group
  - `o`: others
- Permissions can be modified as follows:
  - `+`: add permission
  - `-`: remove permission
  - `=`: set permission explicitly, overwriting existing permissions
- Examples:
  - `chmod u+r file`: adds read permission for the user.
  - `chmod g-w file`: removes write permission for the group.
  - `chmod o=x file`: sets execute permission for others, removing read and write.
  - `chmod u=rw,g=r file`: sets user permissions to read and write, and group permissions to read only.

## 6. Special Permissions: Set User ID (SUID)
- The Set User ID (SUID) permission allows a user to execute a program with the permissions of the program's owner.
- When the SUID bit is set, it appears as an `s` in the user execute position of the permissions.
- Example:
  - `-rwsr-xr-x`: The `s` indicates the SUID is set, allowing the program to run with the owner's permissions (e.g., root).
- To set the SUID bit, use:
  - `chmod u+s [program]`
- **Caution:** Adding SUID to programs owned by root can create security risks and potential attack vectors.

## 7. Chaining Permissions with `chmod`
- Permissions can be modified using `chmod` by chaining multiple modes.
- You can set permissions for user, group, and others simultaneously.
- Examples:
  - `chmod u=rw,g=r /challenge/pwn`: Sets user permissions to read and write, and group permissions to read-only.
  - `chmod a=r,u=rw /challenge/pwn`: Sets user permissions to read and write, and group and world permissions to read-only.
  - `chmod u=rw,g=r,o=- /challenge/pwn`: Sets user permissions to read and write, group permissions to read-only, and no permissions for others.
- Use `=` to set permissions and `-` to remove permissions, differentiating them from the context of who the permissions apply to.

## 8. Set User ID (SUID) Permissions
- The Set User ID (SUID) bit allows a user to run a program as the owner of that program's file.
- This is used to give non-root users elevated access for specific tasks without needing root credentials.
- A file with the SUID bit set will display an `s` in place of the execute permission:
  - Example: `-rwsr-xr-x` indicates the SUID bit is set for the executable.
- To set the SUID bit on a program, use the command:
  - `chmod u+s [program]`
- **Caution**: Adding the SUID bit to executables owned by root can create security vulnerabilities, so it should be done carefully.
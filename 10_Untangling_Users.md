# Summary: "Untangling Users"

- **Users in Linux**: There are many users on a Linux system beyond just “hacker” and “root”. The list of users is stored in the `/etc/passwd` file.
  
- **Format of `/etc/passwd` file**: Each line in this file contains:
  1. Username
  2. `x` (placeholder for password)
  3. Numerical user ID
  4. Numerical default group ID
  5. User details (optional)
  6. Home directory
  7. Default shell
  
- **Examples**: The file lists users such as `root`, `daemon`, `bin`, `games`, and `nobody`.

- **Types of Users**:
  - **Service accounts**: Support software operations (e.g., `systemd-timesync`, `mysql`).
  - **Utility accounts**: For minimal privileges (e.g., `nobody`).
  
- **Purpose**: The module focuses on understanding users, switching between them for system administration, and exploring user-related tasks.

## Becoming root with su

- **Goal**: In the previous challenge, `/challenge/getroot` was used to become root, but typical Linux systems use `su` or `sudo` for this purpose.
  
- **Focus**: This challenge introduces the older utility, `su`, for switching users.

- **su Utility**:
  - **Setuid Binary**: `su` has the SUID bit set, meaning it runs with root privileges (`-rwsr-xr-x`).
  - **Purpose**: It can start a root shell if the correct password is provided.

- **Limitations of su**:
  - Requires the root password for authentication.

- **Modern Use**: Rarely used today, as root passwords are less common, and other methods (like `sudo`) are preferred for administrative access.

## Other users with su

- **Default Behavior**: Running `su` without arguments starts a root shell after authenticating with the root password.

- **Switching to Other Users**: You can specify a username as an argument to switch to that user instead of root.

- **Example**:
  - `su some-user` switches to `some-user` after entering the password.

This allows switching between users, not just to root, using the `su` command.

## Cracking Password

- **Password Storage**:
  - Historically stored in `/etc/passwd`, but now moved to `/etc/shadow` for security.
  - The second field in `/etc/shadow` holds the hashed password.
  - `*` or `!` means password login is disabled.
  - A blank field means no password (a misconfiguration that allows password-less `su`).

- **Password Hashing**:
  - When a password is entered into `su`, it is one-way encrypted (hashed) and compared to the stored hash. If they match, access is granted.

- **Cracking Passwords**:
  - If a hacker obtains the `/etc/shadow` file (e.g., via unencrypted backups), they can attempt to crack the hashed passwords using tools like John the Ripper.
  - **Example command**: `john ./my-leaked-shadow-file`, which cracks and displays the password if successful.

This highlights the importance of securing `/etc/shadow` and preventing leaks.

## Using sudo

1. **Old Linux Administration**:
   - Administrators used to switch to root using the `su` command after entering the root password.

2. **Challenges with Root Passwords**:
   - Root passwords are hard to maintain.
   - They can leak.
   - Not suitable for large-scale environments (e.g., multiple servers).

3. **Shift to sudo**:
   - The world has transitioned to using `sudo` for administrative tasks.
   - `sudo` runs commands as root, instead of launching a root shell like `su`.

4. **sudo Command**:
   - **Example**:
     ```bash
     hacker@dojo:~$ sudo whoami
     root
     ```
   - It allows users to run commands as root without knowing the root password.

5. **Policy-Based Access Control**:
   - `sudo` uses policies defined in `/etc/sudoers` to determine if a user can execute commands as root, rather than asking for the root’s password.

6. **pwn.college Practice Mode**:
   - After this level, Practice Mode will give full `sudo` access to allow introspection and debugging, but with a placeholder flag.
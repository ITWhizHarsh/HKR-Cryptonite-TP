# Second Dojo - Pondering Paths 

## Overview
Learned **absolute** and **relative paths**, special directory entries (`.` and `..`), and the difference between running programs using naked paths and explicit relative paths.

---

### Key Concepts Learned

- **Absolute Path**: A path that starts from the root `/`. It is complete and can be used from anywhere in the system, e.g., `/challenge/run`.
  
- **Relative Path**: A path that depends on the current working directory. It can start without `/` and is resolved based on the current location, e.g., `challenge/run`, `./run`, or `../run` depending on your current directory.

- **Special Entries in Directories**:
  - `.`: Refers to the current directory.
  - `..`: Refers to the parent directory.

- **Naked Paths**: When you try to run a program by just typing its name, e.g., `run`. If this program is not in a directory listed in your `PATH` environment variable, it won’t be found. By default, Linux does not search the current directory for security reasons.

- **Explicit Relative Paths**: To run a program from the current directory, you need to use `./` to explicitly tell Linux to look in the current directory, e.g., `./run`.

- **Home Directory**:
  - Your home directory is `/home/hacker`, which is typically where you store personal files.
  - `~` is shorthand for your home directory.
  - You can use `cd ~` or just `cd` to go to your home directory.

---

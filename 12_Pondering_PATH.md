# Pondering PATH

## Command Invocation Methods
- **Absolute Path**: Refers to the full path of the command (e.g., `/challenge/run`).
- **Relative Path**: Refers to a path relative to the current working directory (e.g., `./run`).
- **Bare Command Name**: Executes commands without a path, like `ls`.

## The PATH Variable
- **Explanation**: PATH is a shell variable that stores directories where the shell searches for commands.
- **Example**:
    - `echo $PATH`
        - Displays the current directories in the PATH.
    - `PATH=""`
        - Clears the PATH, making commands like `ls` unusable.
    - `ls`
        - Lists directory contents, but fails if PATH is cleared.

## Setting PATH
- **Example**:
    - `PATH=/home/hacker/scripts`
        - Sets the PATH to only the `/home/hacker/scripts` directory, allowing commands in that directory to be used by name (e.g., `goodscript`).

## Adding Commands to PATH
- **Command**:
    - `export PATH=/home/hacker/scripts:$PATH`
        - Adds `/home/hacker/scripts` to the existing PATH, retaining access to system commands like `cat`.
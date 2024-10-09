# Dojo: Chaining Commands

## Chaining with Semicolons
- **Piping Module Recap**: Previously, you learned to use pipes to connect commands for more complex tasks.
- **Purpose**: This module explores chaining commands without pipes, allowing multiple commands to run in quick succession.
- **Chaining with Semicolons**:
  - **Usage**: Commands can be separated with a semicolon (`;`), allowing them to be executed one after the other without the need for a new prompt.
  - **Example**:
    ```bash
    echo COLLEGE > pwn; cat pwn
    ```
    This writes “COLLEGE” to a file named `pwn` and then displays its content.
- **Goal**: Use `;` to chain the execution of `/challenge/pwn` and `/challenge/college`.

---

## Your First Shell Script
- **Purpose of Shell Scripts**: When commands become complex, using shell scripts allows you to store commands in a file and execute them easily.
- **Example of Command Chaining**:
  - The following commands can be combined into a shell script:
    ```bash
    echo COLLEGE > pwn
    cat pwn
    ```
- **Creating and Running a Shell Script**:
  - **File Creation**: Save the above commands in a file named `pwn.sh`.
  - **Execution**: Run the script using:
    ```bash
    bash pwn.sh
    ```
  - This will execute both commands in the script, creating and displaying the content of the file `pwn`.
- **Task**: Create a shell script named `x.sh` that runs `/challenge/pwn` and `/challenge/college`, then execute it using `bash`.
- **Note**: You can use the Text Editor application or the default editor in the VSCode Workspace to create the shell script.

---

## Redirecting Script Output
- **Concept Overview**:
  - You can redirect output from your scripts similar to commands in the Piping module.
  - The script acts as a command, allowing redirection of its input and output.
- **Example of Output Redirection**:
  - Create a script (`script.sh`) with the following content:
    ```bash
    echo PWN
    echo COLLEGE
    ```
  - Run the script and redirect the output to a file:
    ```bash
    bash script.sh > output
    ```
  - Check the output file:
    ```bash
    cat output
    ```
  - Output will display:
    ```
    PWN
    COLLEGE
    ```
- **Redirection Methods**:
  - `>` for stdout
  - `2>` for stderr
  - `<` for stdin
  - `>>` and `2>>` for append-mode redirection
  - `>&` for redirecting to other file descriptors
  - `|` for piping to another command
- **Challenge**: Create a script that calls `/challenge/pwn` and `/challenge/college`, and pipe the output into a single invocation of `/challenge/solve`.

---

## Executable Shell Scripts
- **Introduction**:
  - Calling a shell script using `bash script.sh` can be cumbersome.
  - This command launches bash with `script.sh` as an argument, executing the script.
- **Avoiding Manual Invocation**:
  - You can execute a shell script directly if it is marked as executable.
  - Invocation can be done using:
    - **Absolute Path**: `/home/hacker/script.sh`
    - **Relative Path**: `~/script.sh`
    - **Current Directory**: `./script.sh` (if in the script’s directory)
- **Task**:
  - Create a shell script that invokes `/challenge/solve`.
  - Make the script executable.
  - Run the script without explicitly using the `bash` command.
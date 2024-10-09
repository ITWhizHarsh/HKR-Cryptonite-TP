# Dojo: Chaining Commands

## Chaining with Semicolons
- **Purpose**: Explore chaining commands without pipes, using semicolons (`;`) to run commands in sequence.
- **Example**:
    ```bash
    echo COLLEGE > pwn; cat pwn
    ```
    This writes "COLLEGE" to a file named `pwn` and then displays its content.

- **Use Case**: Chain the execution of `/challenge/pwn` and `/challenge/college` using a semicolon.

---

## Your First Shell Script
- **Purpose**: Shell scripts store complex command sequences for easy execution.
- **Example**: 
    - Combine commands in a script:
    ```bash
    echo COLLEGE > pwn
    cat pwn
    ```
    - **Creating the Script**:
        1. Use `nano` to create a script:
           ```bash
           nano pwn.sh
           ```
           Add the commands above and save.
        2. Run the script:
           ```bash
           bash pwn.sh
           ```

- **Task**: Create a script `x.sh` that runs `/challenge/pwn` and `/challenge/college`, and execute it using `bash`.

---

## Redirecting Script Output
- **Purpose**: Redirect script output like commands.
- **Example**: 
    - Create `script.sh`:
    ```bash
    echo PWN
    echo COLLEGE
    ```
    - Redirect output:
    ```bash
    bash script.sh > output
    cat output
    ```
    - Output will display:
    ```
    PWN
    COLLEGE
    ```

- **Redirection Methods**:
    - `>`: Redirect stdout.
    - `2>`: Redirect stderr.
    - `>>`: Append stdout.
    - `|`: Pipe output to another command.

---

## Executable Shell Scripts
- **Purpose**: Make scripts executable to avoid manual invocation with `bash`.
- **Steps**:
    1. Create the script:
    ```bash
    nano solve.sh
    ```
    Add commands to invoke `/challenge/solve`.
    2. Make it executable:
    ```bash
    chmod +x solve.sh
    ```
    3. Run it without `bash`:
    ```bash
    ./solve.sh
    ```

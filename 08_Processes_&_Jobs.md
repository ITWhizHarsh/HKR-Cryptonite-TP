# Eight Dojo: Processes and Jobs

## 1. Listing Processes
- **Command to List Processes:**
  - `ps`: Lists processes running in the terminal.
  
- **Understanding ps Output:**
  - **PID:** Process Identifier (unique number for each process).
  - **TTY:** Terminal associated with the process.
  - **TIME:** Total CPU time used by the process.

- **Usage of Arguments with ps:**
  - **Standard Syntax:**
    - `-e`: List every process.
    - `-f`: Full format output (includes arguments).
    - **Combined:** `ps -ef`.
  - **BSD Syntax:**
    - `a`: List processes for all users.
    - `x`: List processes not running in a terminal.
    - `u`: User-readable output.
    - **Combined:** `ps aux`.

- **Examples of Commands:**
  - `ps -ef`: Shows a detailed list of all processes.
  - `ps aux`: Provides a user-readable list of all processes with memory and CPU usage.

- **Common Output Columns:**
  - **Both ps -ef and ps aux display:**
    - User (USER column)
    - PID
    - TTY
    - Start time (STIME/START)
    - Total CPU time (TIME)
    - Command (CMD/COMMAND)
  - **Additional Columns:**
    - `ps -ef`: Parent Process ID (PPID).
    - `ps aux`: %CPU and %MEM used.

- **Note on Output Truncation:**
  - Both commands truncate the command listing to fit the terminal width; resizing the terminal or redirecting output may be necessary to view complete command paths.

---

## 2. Terminating Processes
- **Command to Terminate Processes:**
  - `kill`: Terminates a process using its PID.
  
- **Example Commands:**
  - Launch a process:
    ```bash
    sleep 1337
    ```
  - List processes and find PID:
    ```bash
    ps -e | grep sleep
    ```
  - Terminate the process:
    ```bash
    kill <PID>
    ```

---

## 3. Interrupting Processes
- **Hotkey to Interrupt Processes:**
  - **Ctrl-C**: Sends an "interrupt" signal to the running application, causing it to exit cleanly.

---

## 4. Suspending and Resuming Processes
- **Hotkey to Suspend Processes:**
  - **Ctrl-Z**: Suspends the process and puts it in the background.

- **Command to Resume Processes in the Foreground:**
  - `fg`: Resumes a suspended process in the foreground.

- **Command to Resume Processes in the Background:**
  - `bg`: Resumes a suspended process in the background.

- **Example Workflow:**
  - Launch a process, suspend it with Ctrl-Z, and resume it using:
    ```bash
    bg
    ```
  - Launch another copy while the first is running.

---

## 5. Backgrounding Processes
- **Command to Start a Process in the Background:**
  - Append `&` to the command:
    ```bash
    sleep 1337 &
    ```

---

## 6. Exit Codes
- **Exit Codes:**
  - Every shell command exits with an exit code indicating success or failure.
  
- **Accessing Exit Codes:**
  - Use the special variable `$?` to retrieve the exit code of the most recently terminated command.
  
- **General Rule:**
  - **Exit Code `0`:** Command succeeded.
  - **Non-zero Exit Code:** Command failed (commonly `1` for general errors, with specific codes for other failure modes).

- **Example Commands:**
  - Successful Command:
    ```bash
    touch test-file
    echo $?
    ```
    - **Output:** `0`
  - Failed Command:
    ```bash
    touch /test-file
    echo $?
    ```
    - **Output:** `1`
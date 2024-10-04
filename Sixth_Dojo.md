# Sixth Dojo - Practicing Piping

## Redirection Operators
- `>`: Redirects stdout to a file.
- `>>`: Appends stdout to a file.
- `2>`: Redirects stderr to a file.
- `2>>`: Appends stderr to a file.
- `&>`: Redirects both stdout and stderr to a file.
- `2>&1`: Redirects stderr to the same place as stdout.

## Piping
- `|`: Pipes stdout from one command to stdin of another.

## Process Substitution
- `>(command)`: Sends output to a command through a named pipe.

## Combining Redirection and Piping
- `command > >(stdout_command) 2> >(stderr_command)`.

## Command Examples
- `echo HACK | tee FILE`: Duplicates output to a file and stdout.
- `command | tee >(command1) | command2`: Pipes to multiple commands.
- `command 2> error_log`: Redirects stderr to a file.
- `command &> output_log`: Redirects both stdout and stderr to a file.

## Multiple Outputs
- `command | tee >(command1) | >(command2)`: Duplicates command output to two different commands.

## Redirecting to Multiple Commands
- `command | tee >(command1) | >(command2)`: Directly pipes output to two different commands.
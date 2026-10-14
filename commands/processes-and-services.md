# Linux Processes and Services

## 1. Introduction to Processes

A process is a running instance of a program. Whenever a program is executed, the operating system manages its execution as a process. Linux assigns each process a unique Process ID (PID) while that process exists. The PID allows administrators to identify and manage individual processes.

Important terms:
- Program: A set of instructions stored in a file.
- Process: A program that is running.
- `PID` (Process ID): The identifier assigned to a process.
- `PPID` (Parent Process ID): The PID of the process that created another process.

A process also has information such as its owner, current state, and resource usage.

## 2. Parent and Child Processes

Linux processes can create other processes.

- Parent process: A process that creates another process.
- Child process: A process created by another process.

The relationship between a parent and child process is recorded through the `PPID`.

For example, when you run a command from a shell, the shell may create a child process to execute that command.

To view process relationships, use:

`ps -ef` 
This displays a process list that includes PID and PPID information.

## 3. Commands for Viewing Processes

Linux provides several commands for inspecting running processes.

| Command | Purpose |
| --- | --- |
| `ps` | Displays a snapshot of processes associated with the current terminal. |
| `ps aux` | Displays a broad list of running processes. |
| `ps -ef` | Displays processes in a full-format listing, including PID and PPID. |
| `top` | Shows processes and resource usage in a continuously updating display. |

Difference between `ps` and `top`
- `ps` displays a snapshot of processes at the time the command runs.
- `top` continuously updates the display, helping you monitor process activity and resource usage.

## 4. Understanding Process States and Resource Usage

A process can be in different states during its lifetime.

Common process states include:
- `Running or runnable`: The process is executing or ready to execute.
- `Sleeping`: The process is waiting for an event or resource.
- `Stopped`: The process has been paused.
- `Zombie`: The process has finished, but its parent has not yet collected its exit status.

You can inspect the state of the process by running 
`ps aux` 

The STAT column shows process-state information.

Processes also consume system resources:
- CPU: Performs processing and calculations.
- Memory (RAM): Stores data and instructions used while programs run.

The `top` command helps you monitor CPU and memory usage.

## 5. Managing Processes with Signals

Linux uses signals to communicate with processes.

The `kill` command sends a signal to a process identified by its `PID`.

| Command | Purpose | 
| --- | --- | 
| `kill PID` | Sends the default SIGTERM signal. | 
| `kill -TERM PID` | Requests graceful termination. | 
| `kill -KILL PID` | Sends SIGKILL to force termination. |

Replace `PID` with the actual process `ID`. 

For example : 
`kill 1234` 
Here, `1234` is only an example `PID`.

Important points:
- `SIGTERM` requests that a process terminate and allows it to perform cleanup.
- `SIGKILL` cannot be caught or ignored by the target process.
- Try graceful termination before using `SIGKILL`.
- You generally need appropriate permissions to send signals to a process.

Never terminate an unfamiliar process without first understanding what it does.

## 6. Services and Daemons 

A service is a system function or application that provides a particular capability, such as remote access, scheduled tasks, or web hosting.

A daemon is a program that runs in the background to provide a service or perform a system function.

Examples include:
- SSH service: Provides remote login and administration.
- Web server service: Serves web content to clients.

A service can involve one or more processes. A process can also run without being a system service.

| Process | Service | 
| --- | --- | 
| A running instance of a program | A managed system function or application. |
| Identified by a `PID` | Managed through a service manager such as `systemd`. |
| Managed with commands such as `ps` and `top`. | Managed with commands such as `systemctl`. |

## 7. Understanding systemd 

`systemd` is a system and service manager used by Debian and many other Linux distributions.

It manages system startup and can start, stop, and monitor services.

Services managed by systemd are commonly represented by unit files. A service unit describes how a service should be managed.

The `systemctl` command is used to interact with systemd.

Example : 
`systemctl status ssh` 

This displays status information for the `SSH` service, if that service exists on the system.

## 8. Managing Services with systemctl

These commands shows common service-management operations.

| Command | Purpose | 
| --- | --- | 
| `systemctl status ssh` | Checks the status of the SSH service. |
| `sudo systemctl start ssh` | Starts the service now. |
| `sudo systemctl stop ssh` | Stops the service now. | 
| `sudo systemctl restart ssh` | Restarts the service. |
| `sudo systemctl enable ssh` | Configures the service to start automatically at boot. | 
| `sudo systemctl disable ssh` | Removes its normal automatic startup enablement. | 
| `systemctl list-units --type=service` | Lists loaded service units. |

The exact service name may differ between systems. For example, Debian commonly uses `ssh` for the `OpenSSH` server service.

Important distinction
- start and stop change a service's current runtime state.
- restart stops and starts the service again.
- enable and disable change its normal startup configuration.
- Enabling a service does not necessarily start it immediately.
- Disabling a service does not necessarily stop it if it is already running.

## 9. Viewing Service Logs with journalctl

Linux logs record information about system activity. Logs are useful for understanding errors and troubleshooting problems.

`journalctl` is a command used to view logs.

| Command | Purpose | 
| --- | --- | 
| `journalctl` | Displays available journal entries. | 
| `journalctl -u ssh` | Displays journal entries associated with the SSH service. | 
| `journalctl -u ssh -n 20` | Displays the latest 20 matching entries. | 
| `journalctl -u ssh -f` | Follows new matching log entries as they arrive. | 

Press `Ctrl + C` to stop following live entries.

## 10. Key Points

- A process is a running instance of a program.
- `PID` identifies a process, while `PPID` identifies its parent process.
- `ps` provides a snapshot, while `top` updates continuously.
- `kill` sends signals to processes.
- `SIGTERM` requests termination; `SIGKILL` forces it.
- A service provides a system function and may involve multiple processes.
- `systemd` manages system startup and services on Debian.
- `systemctl` controls services and their startup configuration.
- `journalctl` displays system journal logs.
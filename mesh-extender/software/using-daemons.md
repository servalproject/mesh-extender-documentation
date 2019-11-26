# Using Daemons
Daemons are handled by the `start-stop-daemon` program included in the Mesh Extender firmware. It can daemonise any program, running it in the background until the program stops or it is told to kill it.

Below is the usage for `start-stop-daemon`:
```
Usage: start-stop-daemon [OPTIONS] [-S|-K] ... [-- ARGS...]

Search for matching processes, and then
-K: stop all matching processes.
-S: start a process unless a matching process is found.

Process matching:
	-u USERNAME|UID	Match only this user's processes
	-n NAME		Match processes with NAME
			in comm field in /proc/PID/stat
	-x EXECUTABLE	Match processes with this command
			command in /proc/PID/cmdline
	-p FILE		Match a process with PID from the file
	All specified conditions must match
-S only:
	-x EXECUTABLE	Program to run
	-a NAME		Zeroth argument
	-b		Background
	-c USER[:[GRP]]	Change to user/group
	-m		Write PID to the pidfile specified by -p
-K only:
	-s SIG		Signal to send
	-t		Match only, exit with 0 if a process is found
Other:
	-q		Quiet
```

## Starting a daemon
To start a program as a daemon, use: `start-stop-daemon -Sbx <program> [args...]`
where `<program>` is the program name and `[args...]` is a list of arguments that you would normally provide the program.

The program will start running in the background.

## Stopping a daemon
To stop a running daemon started with the `start-stop-daemon` program, use: `start-stop-daemon -K <program>`  
where `<program>` is the program name.

Note that **this will kill the program**. If you need to stop it gracefully (i.e. with a `SIGHUP` or `SIGINT`), then add `-s <signal>` to the options.

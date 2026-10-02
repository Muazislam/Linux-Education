PROCESS CHAIN:
systemd(1) → systemd(1390) → konsole(19069) → bash(19077) → pstree(19593)

PID 1:
PID 1 is systemd.
It is important because it tells that the systemd is running.

INTERMEDIATE PROCESS:
PID 5156 was not found because that process is not runnning.
PID 1390 is systemd.
PID 19069 is konsole.

SHELL:
My shell is Bash.
Its PID is 19077.
Its parent PID is 19069.

COMMAND PROCESS:
The `pstree` command had PID 19593 because it is a command that runs in the system under the bash to gather information. 

EXPLANATION:
The process tree shows that the a process is running. And it traces the whole tree from the programs that are running above it and in which it is running step by step. But i think that maybe it just searches from the start of the process and then it goes to the bottom to the process.
A PID tells me that a process is running and it is consuming ram but it does not tell me that a process is downloaded. The same PID number can go to any process, that number is just to tell that a process is running
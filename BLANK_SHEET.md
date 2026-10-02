PID 1:
PID 1 is _______
PID 1 is the first userspace process started by the kernel. It is important because it initializes and manages system services, adopts orphaned processes, and participates in shutdown and reboot.

COMMAND PROCESS:
pstree is an external program. Bash starts it as a child process, so it recieves it's own PID. It reads process relationship and displays them as a tree.

A PID identifies a process currently known to the kernel. It doesn't tell me how much RAM the process uses. Memory usage must be measured seperately.

A PID is not related to whether software is downloaded or installed. The same PID number may be reused later for a different process, but two active processes cannot normally use the same PID at the same time.


This is the answer that chatgpt codex generated on my previous answers. So, i want to mention that i am re writing them. But I would mention that, i understand them but articulating them into proper words is a little difficult for me. I hope that with firther sessions and tasks, i become good at articulating.
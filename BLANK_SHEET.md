
The output is this

```

    ps -p 5156 -o pid,ppid,comm,args
        PID    PPID COMMAND         COMMAND

My raw observation here is that the 5156 process doesn't even exist. Because it doesn't has a PID number. If a process has a PID number, it exists in the system whether it is running in the ram or not. 5156 doesn't exist. Maybe it doesn't exist here or it is not downloaded.
    
    ps -p "$$"  -o pid,ppid,comm,args
        PID    PPID COMMAND         COMMAND
    19077   19069 bash            /bin/bash
I can see it that this is bash running and it is showing a PID. And it is actually taking space in my RAM too.
    pstree -p -s "$$"
    systemd(1)───systemd(1390)───konsole(19069)───bash(19077)───pstree(19593)

This shows that first the systemd with PID 1 runs. And then 1398 runs, then konsole runs. Then in that the bash runs and then the pstre runs in the bash. I think that this is showing that the processes are runing in eachother like a node tree.

This is my first basic observation. Now, what to do


```

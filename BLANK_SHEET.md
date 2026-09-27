I am thinking of running this commands on the file that is useless.



What is PID 1, and why is it important?

``PID 1 is the first process that runs in my system. It is my linux device itself that the device starts this is why is it systemd. This is why it is important`

```


What relationship exists between your shell and PID 1?

```
The PID1 is the system itself that the system is running. And the shell is a process that is running within that system. We can assume that this is like a heirerichal tree that

PID1 running
    |
    shell
```

Why are /proc, /sys, /dev, and /run different from an ordinary directory such as /home?

```
These directories are different because /proc gprovides (process and kernel info). It is a virtual system created in the computers memory by the kernel. And it contains information about active programs(processes) and system hardware like CPU.

The /sys (system and device attributes). It is a structural virtual file system called sysfs. It contains information about device trees, and kernel settings. User can even read and change system settings here, like changing screen brightness or CPU sppeed.

The /dev (device files) is a directory holding special files for hardware devices. It contains interfaces for hard drives(/sda), webcams(/video0) or the mouse so programs can use them.

The /run (runtime variable data). is a temporary file system (usually stored in RAM as a tmpfs.) It is short-term data for processes that started up since the last boot, such as active service IDs (PIDs) or login socket files.


I honestly searched these things definition online because i have never studied them before. THis is my first time learning about them
```

Which observations come from the kernel, and which come from userspace tools?

```
The kernel owns and maintains the underlying system state. Userspace commands such as uname, ps and ls request or read that state and present to me

```

```
    ~ 
    ❯ ps -p 1 -o pid,ppid,comm,args
        PID    PPID COMMAND         COMMAND
        1       0 systemd         /usr/lib/systemd/systemd --switched-root --system --deserialize=59


    ~ 
    ❯ ps -p "$$" -o pid,ppid,comm,args
        PID    PPID COMMAND         COMMAND
    5171    5156 bash            /bin/bash

```
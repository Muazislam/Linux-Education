I am thinking of running this commands on the file that is useless.

Then answer in your own words:
Which command gives evidence about the kernel?

```
uname -a gives wvidence about kernel.
It says 7.2.4-arch1-2 #1. I think it is the kernel. Instead of x86_64 GNU/Linux.
```

What is PID 1, and why is it important?

```
i DON't know what this is. But this is relevant to systemd. I think systemd is maybe my own laptop endavouros, 7.2.4 arch1 -2. And the command section in PID is refering to the folders in my system. but the --switched-root and --system --deserialize=58 is about the commands that can be run, i think this is because this is how i see commands running. So, tell me if i am right or wrong.
```

Is your shell a process? What evidence proves it?

```
My shell is a process because it has a PID, if something has a PID, it means that that process is running and consuming ram.
```

What relationship exists between your shell and PID 1?

```
The PID1 is maybe showing that the system is running (my endavouros) and the shell is the system itself, i can do anychanges in my operating system using shell. So, this might be the relationship.
```

Why are /proc, /sys, /dev, and /run different from an ordinary directory such as /home?

```
They are different because they contain system files and working data. ABout all the instructions that the system has and apps installed in the system. And the /home etc files are the directories where i can place my user data.
```

Which observations come from the kernel, and which come from userspace tools?

```
The kernel is about showing the kernel number, the last update system had. The architecture and the linux installed in the device. The device name too.
as for the userspace tool

i guess you mean  ls -ld /proc /sys /dev /run /home
this command.. SO, it is showing the files and it shows the permissions it has in each and the dates and numbers.
```

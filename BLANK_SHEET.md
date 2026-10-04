## Task 3: Compare persistent, virtual, and runtime filesystems

**Target:** HOST  
**Risk:** Read-only. Do not use `sudo`, write to `/sys`, or modify any files.

### Objective

Understand why `/home` behaves differently from `/proc`, `/sys`, `/dev`, and `/run`.

Run:

```bash
findmnt -T /home -o TARGET,SOURCE,FSTYPE,OPTIONS
findmnt -T /proc -o TARGET,SOURCE,FSTYPE,OPTIONS
findmnt -T /sys -o TARGET,SOURCE,FSTYPE,OPTIONS
findmnt -T /dev -o TARGET,SOURCE,FSTYPE,OPTIONS
findmnt -T /run -o TARGET,SOURCE,FSTYPE,OPTIONS
```

Then inspect examples:

```bash
ls -ld /home /proc /sys /dev /run
ls -ld /proc/$$
ls -l /dev/null
```

Use local documentation:

```bash
man findmnt
man 5 proc
man 5 sysfs
man 4 null
```

Search inside the manuals for:

```text
/filesystem
/mounted
/virtual
/device
```

### Think through these questions

1. What filesystem type is `/home` using?   
    ```
    /home is using btrfs filesystem type. I concluded that from the third column FSTYPE. Although I don't know the specifics of btrfs.
    I also have a question that what is filesystem type?

    ```
2. What filesystem types are `/proc`, `/sys`, `/dev`, and `/run` using?
    ```
    /home filesystem type is btrfs
    /proc filesystem type is proc
    /sys filesystem type is sysfs
    /dev filesystem type is devtmp
    /run filesystem type is tmpfs


    ```
3. Which directory primarily stores persistent user data?
    ```
    The process of me searching for answer:
        ```
        🚀  muazislambabar ~   10:32  ❯ man -k /run
        dracut-shutdown.service (8) - unpack the initramfs to /run/initramfs

        bUT this is not the right answer either. I think i should tell the man page to give me documentation about /run or just run in the filesystem. And the way to access filesystem is findmnt I guess.

        I did this but tstill no use
          in 45s491ms ❯ man -k findmnt,run
            findmnt,run: nothing appropriate.

            🚀  muazislambabar ~   10:35  ❯ man -k findmnt
            findmnt (8)          - find a filesystem

            🚀  muazislambabar ~   10:36  ❯ man findmnt

            🚀  muazislambabar ~   10:36   in 19s176ms ❯ 

            Damn I am thinking of what to do here. But the answer is not comming to me. Might be beause i do not know which command to through on the man. Or how to search this. I can easily get answer from the internet though.

            But from my knowledge. THe /proc is for process. It contains all the files for the things that are running and it gives them all a PID.
            And /run i don't remember much about it. Maybe it contains the persistent data. But i thought that persistent data would be stored in a catch folder.
            /dev is for devices. it contains all the files for the hardware of the system
            /sys is for containing files of the things that are happening over the kernel. It also gives moniter informatrion.#
            
            I can say this because of previous task and that i remember many things from the videos on file system in linux.

        ```
    ```
4. Which directories are generated or populated by the kernel or boot process?
    ```
    I would say /run /sys /dev /proc are generated or populated by the kernel or boot process. Because they are contained in the RAM. It is only /home that lives in ROM.
    ```
5. Why does `/proc/$$` correspond to your current shell?
    ```
    /proc/$$ corresponds to current shell. I don't know how. But $$ looks familiar. And I would say that $$ maybe gives to root or shell level something.I read this in phase 0. So, i hardly remember it.

    I will try typing man $$. And see what happens.

     in 19s176ms ❯ man $$
    No manual entry for 68555

    🚀  muazislambabar ~   10:50  ❯ man -k $$
    68555: nothing appropriate.

    🚀  muazislambabar ~   10:51  ❯ 


    You asked me why slash proc slash dollar corresponds to my current shell. Um, as I remember, when uh, we write dollar dollar, maybe it means something that is relevant to the home directory or the shell. Although I used it in the past in the phase zero, so I do not remember much about it. But from the output that I can see, it is a directory and it is not a root directory, but it is, uh, I think, near from the home directory. And uh, you say dollar dollar, it shows 61701. So um, maybe dollar dollar uh, here brings the PID number, maybe, and uh, maybe it shows that. When the command was run, it had a specific PID number, and at the end of the directory, um, it is also showing slash proc slash the PID number 61701. Uh, maybe this uh, is showing that the current process that I typed, the command that I typed ls negative ld slash proc slash dollar dollar executed, and it had. Uh, PID in the process um, slash proc directory because the slash proc directory contains all the processes that are uh, happening on the kernel. So maybe it uh, the pro this process happened in an instant and it recorded it.
    ```
6. Why is `/dev/null` a device interface rather than an ordinary text file?
    ```
    Now I do not know why slash dev slash null is uh, something like uh, I do not know why slash dev slash null is uh, a device interface rather than an ordinary text but from the command that I typed I can see that uh, The output does not start with D, it starts with C. And uh, if it, the output starts with D, it is usually a directory, but uh, it is starting with C. So it is not a directory, I will say. And you say slash dev slash null. Normally, when we say slash dev, we write slash SDA1, SDA2, but here we uh, typed null. So um, I think that. This is the directory that does not exist. It is a null directory. Therefore, we have C in the starting. And uh, normally, uh, not normally, but uh, I would get uh, but I see that it exists in the root. And uh, it also gives time and month and afterwards it just types slash dev slash null yeah. 
    ```
7. Which contents would you expect to disappear or change after reboot?

I would say that the content that would disappear when we reboot um, would be everything that exists in the RAM. So most of the root directories such as slash dev slash sys slash um, swap slash sys are persistent uh, memory directories which um, are formed in the RAM when the kernel starts or when the Linux uh, kernel starts and the all the files that are generated are saved in the RAM they are not saved in the ROM it is the slash home directory that contains all the things that are saved in the ROM 


Use this report:

```text
OBJECTIVE:
COMMANDS USED:

FILESYSTEM COMPARISON:
- /home:
- /proc:
- /sys:
- /dev:
- /run:

IMPORTANT OUTPUT:

INTERPRETATION:

WHAT I EXPECTED:

WHAT SURPRISED ME:

UNRESOLVED QUESTIONS:


```

Do not search for definitions first. Start with the command output, then use the manuals to explain what you observed.
# 2. Other filesystem types

Mostly correct:
/home → btrfs
/proc → proc
/sys → sysfs
/dev → devtmp
/run → tmpfs

I maade a mistake to write /dev file system type to be devtmpfs instead of devtmp. THis mistake happened because in my konsole, the devtmp and fs were joined together.

```
❯ findmnt -T /dev -o TARGET,SOURCE,FSTYPE,OPTIONS
TARGET SOURCE FSTYPE OPTIONS
/dev   devtmpfs
              devtmp rw,nosuid,size=7985760k,nr_inodes=1996440,mode=755,inode64,hug

```

# 3. Persistent user data

Your investigation became stuck because man -k searches manual descriptions; it does not search directory meanings very effectively.

Try:
man 7 file-hierarchy
Inside the manual:
/home
/run

If that manual does not exist:
man hier
Use this reasoning:
/home is backed by /dev/sda2[/@home].
/run is backed by tmpfs.
One source refers to storage on a device.
The other refers to a temporary filesystem.
Ask yourself: which one would normally survive a reboot?

```
    I tried man 7 file-hierarchy and i choosed a link of html to the website on file system. There was information about /home and /run but it just contained purpose and requirement information. the /home had one more explanation paragragh although that i do not remember.
    And then i tried man hier. And it showed me all about /tmp and /dev and further various / files and one line information about them. But I didn't find anything about fs regarding tmpfs.
    but I would say that I was also reading about slash sys uh, I was also reading about slash sys in the, the in the man hire h-i-e-r so I saw that the slash sys explanation was that this is a mount point for the sysfs file system which provides information about the kernel like slash proc but better structured following the form formalizing of K object infrastructure although I do not understand much about it and I don't think that this is important information for me right now but what I understood this is a hypothesis that I could conclude that uh, the sysfs means sys uh, the the uh, sysfs was the mount point of slash sys and yet Uh, it has FS with it. Maybe it means file system. Because if I remember about slash sys, it contains all the proc uh, information about the kernel, like slash proc. The first hypothesis that I conclude is that um, maybe a mount point also contains FS because it may contain files that are being taken from another root directory. like slash sys is taking files information like slash proc or maybe and there is also hypothesis that slash sys also displays the system information um, when we are prompted just like the taskbar manager of Windows so maybe the FS means that those files can be displayed like that Although this is just a mount point and mount point doesn't deal with displaying mount point deals with um, connecting the storage or directories with the kernel of Linux. So I would say that maybe ..
    in case if we are talking about rebooting then um, the, uh, the slash home directory is mounted with the um, slash dev slash sta2 and uh, the slash root is mounted at tempfs so I do not think that the tempfs sorry uh, so uh, I would uh, I think it is clearly understandable that the slash home directory is going to persist even after the reboot but slash root directory is not going to persist because it contains temporary files and they vanish away when the device reboots

```

4. Kernel or boot-generated directories
   Your conclusion is broadly correct, but the explanation needs correction.
   Do not group them together simply because they are “in RAM.” Their producers differ:
   /proc: kernel process and system information.
   /sys: kernel device and object information.
   /dev: device interfaces created and managed through the device system.
   /run: temporary runtime state created during boot and service startup.
   Also, /home does not live in ROM. It is stored on writable persistent storage, such as an SSD or hard drive.

```

okay i understand that my wording had been a little off compared to what is needed for a proffessional linux dev. And i willtry to make this correction from now on

```

# 5th mistake correction.

The ($$) expands to process ID of shell. In a subshell, it expands to the process ID of the parent shell, not the subshell.

The $$ gives the current shell pid. And when we combine it with /proc, it gives the directory in the /proc where the current shell pid exists.

```
ls -ld /proc/$$
dr-xr-xr-x 9 muazislambabar muazislambabar 0 اکتوبر  4 15:08 /proc/115580

```

6. /dev/null
   Your observation about the leading c is correct.
   From:
   crw-rw-rw-
   the first character means:
   d: directory;
   -: regular file;
   c: character device.
   /dev/null exists. It is not a nonexistent directory.
   Read its documentation:
   man 4 null

   Then answer:
   What happens when data is written to /dev/null?
   ```
    The data written to /dev/null and /dev/zero special files is discarded.
   ```
   What happens when a program reads from /dev/null?
    ```
    Reads from /dev/null always return end of file. (i.e., read(2) return (0))
    ```
   Why would programs need such an interface?
    ```
    If these devices are not written and readable for all users, many programs will act strangely.
    Since linux reads from /dev/zero are interruptible by signals. This change helps with bad latencies for large reads from /dev/zero.

    ```

    7. Reboot behavior
Your general direction is reasonable, but avoid using “ROM.” Use:
persistent storage;
temporary runtime storage;
virtual kernel filesystem.
Build this table from your findmnt evidence:
PATH    FSTYPE     SOURCE             PERSISTENT AFTER REBOOT?
/home   btrfs      /dev/sda2[/@home]   Yes
/proc   proc        proc                No
/sys    sysfs       sysfs               No
/dev    devtmp      devtmpfs            No
/run    tmpfs       tmpfs               No

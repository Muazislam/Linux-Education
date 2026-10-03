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
    /home is using /"home
    ```
2. What filesystem types are `/proc`, `/sys`, `/dev`, and `/run` using?
3. Which directory primarily stores persistent user data?
4. Which directories are generated or populated by the kernel or boot process?
5. Why does `/proc/$$` correspond to your current shell?
6. Why is `/dev/null` a device interface rather than an ordinary text file?
7. Which contents would you expect to disappear or change after reboot?

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
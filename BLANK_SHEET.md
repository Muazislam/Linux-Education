Correction 1: /sys vs /proc are not the same kind of information

/proc contains information about processes and general kernel state, things like running process IDs, CPU info, memory stats, system uptime.
/sys contains structured information specifically about kernel device drivers and kernel objects, meaning hardware devices, their drivers, and how they're organized internally by the kernel.

So the distinction isn't "one is a backup of the other" or "they overlap," they cover genuinely different categories, processes and kernel state versus devices and driver structure.

Correction 2: What "fs" in sysfs actually means

The "fs" in sysfs does not mean sysfs behaves like a task manager or displays live readable information for humans to monitor. It simply identifies that sysfs is the name of the virtual filesystem type mounted at /sys. In other words, "fs" here just labels the filesystem format itself, similar to how ext4 or btrfs are filesystem type names, it's not describing what kind of information is shown or implying any monitoring function.

Correction 3: /dev/null not discussed

You had previously discussed /dev/zero, but had not covered the purpose of /dev/null, which your instructor flagged as missing.

For your own understanding going forward: /dev/null is a special device file that discards anything written to it. If you redirect output into it, that output effectively vanishes, it's commonly used when you want to suppress output you don't care about, for example command > /dev/null throws away whatever that command would normally print. Reading from /dev/null always gives you an empty result immediately, nothing to read. This is different from /dev/zero, which, when read from, gives you an endless stream of zero bytes, rather than discarding things.
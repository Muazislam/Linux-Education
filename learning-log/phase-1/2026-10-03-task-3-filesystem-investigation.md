# Learning Session: Phase 1 - Unix/Linux Mental Model (Task 3)

## Date

2026-10-03 to 2026-10-04

## Objective

Compare persistent storage with virtual and runtime filesystems; interpret `/proc/$$`; and explain `/dev/null` behavior.

## Status

**COMPLETE — 2026-10-04, guided practice (L3).**

The learner used command output and local manuals, corrected initial misconceptions, and explained the observed behavior with instructor guidance. This is not an independent mastery claim. Clear technical articulation remains a practice objective.

## Evidence Collected

Mount information was gathered with `findmnt -T <path> -o TARGET,SOURCE,FSTYPE,OPTIONS` for `/home`, `/proc`, `/sys`, `/dev`, and `/run`.

| Path | Source | Filesystem type | Interpretation |
|---|---|---|---|
| `/home` | `/dev/sda2[/@home]` | `btrfs` | Device-backed persistent user storage on this system. |
| `/proc` | `proc` | `proc` | Virtual interface exposing process and kernel state. |
| `/sys` | `sysfs` | `sysfs` | Structured view of kernel devices, drivers, and kernel objects. |
| `/dev` | `devtmpfs` | `devtmpfs` | Filesystem providing device nodes and interfaces. |
| `/run` | `tmpfs` | `tmpfs` | Temporary runtime state populated during boot and service operation. |

The learner verified the `/dev` values separately:

```text
findmnt -T /dev -no SOURCE  → devtmpfs
findmnt -T /dev -no FSTYPE  → devtmpfs
```

Other submitted observations:

- `ls -ld /proc/$$` resolved to `/proc/115580` in a later session, matching the expanded shell PID.
- `ls -l /dev/null` showed mode string beginning with `c` and major/minor numbers `1,3`, identifying an existing character device.
- `printf "This will be discarded" > /dev/null` and `echo "text" > /dev/null` produced no terminal text because standard output was redirected to `/dev/null`.
- `wc -c < /dev/null` reported `0`, showing that zero bytes were read before EOF.
- `cat < /dev/null` printed nothing and exited because a read from `/dev/null` immediately returns EOF.

## Learning and Corrections

- A filesystem type identifies the filesystem implementation/format associated with a mount; it is distinct from the source, though source and type happen to both be `devtmpfs` for `/dev` here.
- `/home` is writable persistent storage, not ROM. `/run` is temporary runtime storage. `/proc`, `/sys`, and `/dev` are dynamically provided interfaces with different purposes; they should not all be described simply as “RAM directories.”
- `$$` is a Bash special parameter that expands to the current shell PID; `/proc/$$` therefore names the corresponding process entry.
- `/dev/null` is a character-device interface. Writes are discarded; reads return EOF immediately.
- EOF is the result/condition reported by a read when no more bytes are available, not generally a special character stored at the end of a file. `/dev/null` produces EOF immediately; an ordinary file produces EOF after its bytes have been read. In canonical terminal input, Ctrl-D can make end-of-input available when no buffered characters remain.
- `sysfs` is the filesystem mounted at `/sys`; its `fs` suffix identifies a filesystem. `/sys` exposes structured kernel object/device information and is related to, but not interchangeable with, `/proc`.
- One attempted `findmnt` invocation used the misspelled column `SHOURCE`; the learner read the error and corrected it to `SOURCE`.

## Assessment

The learner correctly interpreted all five filesystem types, identified `/home` as persistent and `/run` as temporary, explained the distinct purpose of `/proc` and `/sys`, mapped `$$` to the current shell's `/proc` entry, and experimentally demonstrated `/dev/null` input and output behavior. Some explanations required prompting and technical wording refinement, so the task is signed off at **L3: can explain/perform with guidance**.

## Next Action

Proceed to Module 1 Task 4: standard input, output, error, and redirection as process interfaces.

# Learning Session: Phase 1 - Unix/Linux Mental Model (Task 1)

## Date

2026-09-27

## Objective

Distinguish the Linux kernel, userspace, PID 1, the shell, and the special runtime filesystems `/proc`, `/sys`, `/dev`, and `/run`.

## Evidence

The learner submitted:

```text
ps -p 1 -o pid,ppid,comm,args
PID  PPID COMMAND  COMMAND
1    0    systemd   /usr/lib/systemd/systemd --switched-root --system --deserialize=59

ps -p "$" -o pid,ppid,comm,args
PID  PPID COMMAND  COMMAND
5171 5156 bash      /bin/bash
```

The shell PID was reported as `5171` with parent PID `5156`. The learner correctly revised the initial misconception that PID 1 is the device itself and explained that PID 1 is a userspace process, normally systemd, started by the kernel.

## Instructor Assessment

- PID 1/systemd: correct after correction; process arguments were correctly reclassified as arguments rather than folders or standalone commands.
- Shell as process: correct; PID identifies the process, while resource consumption requires separate evidence.
- Kernel/userspace boundary: correct at an introductory level; userspace tools request or read kernel-maintained state and display it.
- Special filesystems: substantially correct; `/proc`, `/sys`, `/dev`, and `/run` were distinguished by purpose.
- Process hierarchy: partial; the learner still needs to verify the intermediate process represented by PPID `5156` instead of assuming the shell is a direct child of PID 1.

## Assessment

Task 1 is complete at guided-practice level (L3). Highest support: H2 conceptual correction plus H1 clarification. No safety issue occurred; all inspection was read-only.

## Next Action

Verify and explain the process chain from PID 1 to the current shell, including the terminal/session process between them.

# Learning Session: Phase 1 - Unix/Linux Mental Model (Task 2)

## Date

2026-10-02

## Objective

Verify the process hierarchy from PID 1 to the current shell and explain why an external command receives its own PID.

## Evidence

The learner observed:

```text
systemd(1) → systemd(1390) → konsole(19069) → bash(19077) → pstree(19593)
```

They also verified that the earlier PID `5156` no longer had a matching process entry, and identified Bash as PID `19077` with parent PID `19069`.

## Assessment

Task 2 is complete at guided-practice level (L3). The learner correctly understands that PID 1 is the first userspace process, that processes form parent/child relationships, that `pstree` is an external child process launched by Bash, and that a PID does not measure RAM usage or indicate whether software is installed.

The learner explicitly noted that technical understanding is ahead of written articulation fluency. This is recorded as a practice objective, not a conceptual weakness. Final phrasing supplied by the earlier correction is not counted as independent evidence.

## Next Action

Begin Task 3: compare persistent directories with virtual and runtime filesystems.

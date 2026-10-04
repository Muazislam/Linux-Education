# Learning Session: Phase 1 - Unix/Linux Mental Model (Task 3, Partial)

## Date

2026-10-03

## Objective

Begin comparing the persistent home filesystem with virtual and runtime filesystems.

## Status

Partial evidence collected. Conceptual interpretation is intentionally incomplete; Task 3 is not yet signed off.

## Commands and Evidence

The learner inspected mount information for `/home`, `/proc`, `/sys`, `/dev`, and `/run` using `findmnt`, then inspected directory metadata and representative entries.

Important observations:

- `/home` reported source `/dev/sda2[/@home]` and a filesystem type shown in the `FSTYPE` column.
- `/proc` reported source and filesystem type `proc`.
- `/sys` reported source and filesystem type `sysfs`.
- `/dev` reported a `devtmpfs` filesystem.
- `/run` reported a `tmpfs` filesystem.
- `/proc` and `/sys` displayed directory sizes of `0`, while `/home` displayed ordinary directory metadata.
- `/proc/$$` resolved to the learner's current shell process directory, `/proc/61701`.
- `/dev/null` was displayed as a character device with major/minor numbers `1,3`.

## Command Error and Recovery

The first `/sys` command used the misspelled output column `SHOURCE`. `findmnt` reported an unknown column. The learner corrected it to `SOURCE` and obtained valid output.

## Instructor Note

The learner requested indirect, documentation-first guidance rather than direct answers. Follow-up should proceed one question at a time using observed column names, local manual definitions, and verification against the command output.

## Next Question

Determine the filesystem type used by `/home` from the `findmnt` output, then explain how the column location supports the conclusion.

## Follow-up Submission - 2026-10-04

The learner submitted written reasoning for all seven Task 3 questions. The submission is preserved in the session history and remains in progress pending correction of filesystem persistence, shell expansion, device-node, and reboot-behavior concepts.

Confirmed or substantially correct observations:

- `/home` uses `btrfs`, identified from the `FSTYPE` column.
- `/proc` uses `proc` and `/sys` uses `sysfs`.
- `/proc` represents process/kernel state, `/sys` represents kernel device/object state, and `/dev` provides device interfaces.
- `/proc/$$` resolves to a numeric process directory associated with the current shell; the learner correctly suspected that `$$` expands to the shell PID.
- `/dev/null` begins with `c` in its mode string, indicating a character device rather than a directory.

Corrections required:

- `/dev` was reported as `devtmpfs` by `findmnt`; `devtmp` was a truncated visual value, not the filesystem type.
- `/home` is persistent storage, but it is not ROM. Persistent data is normally stored on writable disk/SSD-backed storage.
- `/run` is runtime state, not persistent user data.
- RAM-backed or virtual filesystems are not all explained by one rule; `/proc`, `/sys`, `/dev`, and `/run` have different producers and purposes.
- `man $$` expanded `$$` before `man` ran, so `man` received a number. The relevant documentation is in the Bash manual under shell special parameters.
- `/dev/null` is an existing character-device interface with defined read/write behavior; it is not a nonexistent or null directory.

## Instructor Review Status

Task 3 remains incomplete. Continue with one concept at a time, beginning with the meaning of a filesystem type and the persistence clue provided by the `SOURCE` and `FSTYPE` columns.

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

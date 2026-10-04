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

## Second Submission Review - 2026-10-04

The learner revisited the manual pages and submitted a revised interpretation.

Progress confirmed:

- Correctly identified `btrfs` as the `/home` filesystem type from the `FSTYPE` column.
- Correctly identified `proc`, `sysfs`, and `tmpfs` for `/proc`, `/sys`, and `/run`.
- Correctly reasoned that `/home` is device-backed persistent storage while `/run` is temporary runtime storage.
- Corrected the earlier ROM/RAM model and understood that `/home` is stored on writable persistent storage.
- Correctly explained that `$$` expands to the current shell PID and that `/proc/$$` resolves to that process's `/proc` directory.
- Correctly identified `/dev/null` as an existing character device and correctly documented that writes are discarded and reads return EOF.

Remaining corrections:

- Correction to the earlier review: on this system, both the `/dev` `SOURCE` and `FSTYPE` values are `devtmpfs`. The wrapped terminal output made the columns ambiguous. The unambiguous check is `findmnt -T /dev -no FSTYPE`.
- `/sys` is related to `/proc` but does not contain all the same information. It exposes a structured view of kernel devices, drivers, and kernel objects.
- The answer to why programs need `/dev/null` was not yet connected to its purpose. Discussion of `/dev/zero` and signal-interruptible reads is a different topic. The learner should explain how `/dev/null` is useful for safely discarding unwanted output or providing immediate end-of-file input.
- The final persistence table should use `devtmpfs` for `/dev` and describe `/proc`, `/sys`, `/dev`, and `/run` as dynamically recreated or repopulated rather than simply saying they are all "in RAM."

## Current Assessment

Task 3 is still incomplete but close to completion. The learner demonstrates improving documentation use and a stronger filesystem persistence model. One focused follow-up on `/dev/null` and the corrected `/dev` type remains.

## `/dev/null` Practical Follow-up - 2026-10-04

The learner ran and interpreted these examples:

```bash
printf "This will be discarded" > /dev/null
wc -c < /dev/null
cat < /dev/null
echo "text" > /dev/null
```

Observed correctly that output redirected to `/dev/null` is not displayed, `wc -c` reports zero, and `cat` produces no visible output. The learner correctly recognized `<` as input redirection and hypothesized that `/dev/null` supplies no data. Remaining conceptual refinement: reads from `/dev/null` return EOF immediately; EOF is the input stream signal that no more bytes are available, so `cat` exits normally. `wc` reports a count of zero bytes because it receives EOF before reading any bytes. `/dev/null` is an existing character-device interface, not an ordinary empty file.

Task 3 remains in progress pending learner explanation of EOF and correction of `/dev` FSTYPE in the final summary.

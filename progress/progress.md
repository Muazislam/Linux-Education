# Progress

Last updated: 2026-09-13

## Current Phase

Phase 0 - Environment, safety, and curriculum architecture.

## Current Module

Not started (Phase 0 active).

## Completed

- Instructor protocol architecture initialized.
- Curriculum audit initialized.
- Progress-tracking structure initialized.
- Phase 0 implementation plan created in `curriculum/phases/phase-0.md`.
- Lab environment decision recorded and amended in `decisions/phase-0/lab-environment.md` (Oracle VirtualBox chosen, Docker confirmed, ~20h/wk budget).
- Host & VM safety boundaries verified in `labs/phase-0/safety-checklist.md` (Safety Gate marked Done).
- Disposable Arch VM created (`arch-lab-01`, Arch 7.2.4-arch1-2, headless/CLI tty1).
- VM snapshot lifecycle verified (created `phase-0-base`, tested filesystem modification, restored snapshot cleanly).
- Host backup verified (partitioned `/dev/sdc`, ext4 formatted, `rsync -av` with `--exclude` verified, transferred ~487 MB).
- Host baseline diagnostic telemetry captured in `evidence/phase-0/baseline.md` across 9 subsystems.
- Privacy boundary established via `.gitignore` and untracked `private/` directory.
- Phase 0 Baseline Diagnostic Task D1 (Orientation) completed.
- Phase 0 Baseline Diagnostic Task D2 (Files and Paths) completed.
- Phase 0 Baseline Diagnostic Task D3 (Streams & Redirection) conceptual groundwork: standard streams (`stdin`, `stdout`, `stderr`), file descriptors (`0`, `1`, `2`), POSIX standards, and keyword-based man-page discovery (`man -k`).

## Not Completed

- Practical terminal demonstration of Task D3 (redirection operators `>`, `>>`, `2>`).
- Tasks D4–D7 of Phase 0 baseline assessment in `assessments/phase-0/baseline-diagnostic.md` (Docs, Processes, Permissions, Troubleshooting).
- Phase 0 retrospective and sign-off.
- Module 1.

## Evidence

- Submitted output and reasoning for `pwd`, `whoami`, `echo $0`, `cat /etc/*-release`, `uname -v`, and `uname -r`.
- Submitted path navigation logs, `ls -l`, `ls -la`, `ls -a`, `cd /`, `cd ~`, dotfile analysis, and directory vs file distinction.
- Verified `hello-world` execution in Docker.
- Verified `arch-lab-01` login, user creation, and `phase-0-base` snapshot rollback.
- Verified `rsync` dry-run and actual data transfer logs.
- Host diagnostic telemetry recorded in `evidence/phase-0/baseline.md`.
- Submitted terminal trace of `man -k streams` and 35-minute deep-dive on `man stderr (3)`.

## Next Step

Execute practical terminal commands for Task D3 (redirecting standard output, appending, and isolating stderr in `/tmp`).

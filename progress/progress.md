# Progress

Last updated: 2026-09-25

## Current Phase

Phase 1 - Unix/Linux mental model.

## Current Module

Module 1 - Unix/Linux Mental Model (not started; kickoff next).

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
- Phase 0 Baseline Diagnostic Task D3 (Streams & Redirection) fully completed (conceptual reasoning on stdin/stdout/stderr, pipes vs redirects, truncation vs appending, and practical demonstration in `~/Downloads/ioPractice.tst` with `2> errorlog`).
- Phase 0 Baseline Diagnostic Task D4 (Documentation Use) completed ($H0$ independent investigation of `wc`, flag analysis, stdin edge-case, and character/byte count distinctions).
- Phase 0 Baseline Diagnostic Task D5 (Processes) completed: demonstrated 4 process states via `which` ($PATH lookup), `pgrep` (RAM PID presence/absence), and `top` (live CPU/MEM resource telemetry).
- Phase 0 Baseline Diagnostic Task D6 (Permissions Recognition) completed: deconstructed file mode triads (`u`, `g`, `o`), identified owner/group associations, and explained directory execute traversal bit.
- Phase 0 Baseline Diagnostic Task D7 (Troubleshooting Reasoning) completed: diagnosed unreachable local server via layered mental model, validated port listening via `ss -tulpin`, located live server processes, and observed kernel dmesg security boundaries.
- Phase 0 retrospective and sign-off completed on 2026-09-25; Phase 1 is now ready to begin.

## Not Completed

- Module 1.

## Evidence

- Submitted output and reasoning for `pwd`, `whoami`, `echo $0`, `cat /etc/*-release`, `uname -v`, and `uname -r`.
- Submitted path navigation logs, `ls -l`, `ls -la`, `ls -a`, `cd /`, `cd ~`, dotfile analysis, and directory vs file distinction.
- Verified `hello-world` execution in Docker.
- Verified `arch-lab-01` login, user creation, and `phase-0-base` snapshot rollback.
- Verified `rsync` dry-run and actual data transfer logs.
- Host diagnostic telemetry recorded in `evidence/phase-0/baseline.md`.
- Submitted terminal trace of `man -k streams` and 35-minute deep-dive on `man stderr (3)`.
- Verified terminal output logs for `ls -la > ddirectory_context.txt`, `echo >> ddirectory_context.txt`, and `cat anime 2> errorlog`.
- Submitted execution traces of `wc -l`, `-m`, `-c`, `-w`, `-L`, `--debug` on `'Linux Fundamentals.pdf'` and error analysis on `--files0-from`.
- Submitted execution traces for `which nginx`, `which geogebra` + `pgrep -l geogebra`, `which konsole` + `pgrep -l konsole`, and live `top` telemetry.
- Submitted execution trace for `ls -ld ~/Downloads` demonstrating directory permissions (`drwxr-xr-x`).
- Submitted execution trace for `ss -tulpn | grep 3000`, `ss -tulpin`, `pgrep -l live-server`, and `ps aux | grep -i server`.

## Next Step

Kick off Module 1: Unix/Linux Mental Model, beginning with kernel vs userspace, processes, files, and system boundaries.

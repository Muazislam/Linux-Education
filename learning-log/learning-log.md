# Learning Log Index

Last updated: 2026-08-26

Use `learning-log/TEMPLATE.md` for significant sessions.

| Date | Module | Topic | Evidence | Instructor Note | Next Action |
|---|---|---|---|---|---|
| 2026-08-26 | None | Repository architecture | No practical Linux evidence | Learning system created; baseline pending | Complete Phase 0 |
| 2026-09-04 | Phase 0 | Orientation & Lab Decisions | `pwd`, `whoami`, `echo $0`, `cat /etc/*-release`, `uname -r`/`-v` | Completed Task D1; lab decisions recorded | Task D2 (Files and Paths) |
| 2026-09-07 | Phase 0 | Files, Paths & Search Methods | `ls -l`, `ls -la`, `cd /`, `cd ~`, dotfile analysis, `man ls` | Completed Task D2; clarified file extensions & man search | Task D3 (Streams and Redirection) |
| 2026-09-10 | Phase 0 | VM Sandbox, Snapshots, Rsync & Baseline | VirtualBox VM, snapshot test, rsync transfer, `evidence/phase-0/baseline.md` | Safety checklist Done; host baseline captured; snapshot rollback verified | Phase 0 D3–D7 or Phase 1 Kickoff |
| 2026-09-13 | Phase 0 | Standard Streams & Man-Page Discovery | `man -k streams`, `man stderr`, stdin/out/err file descriptors | Clarified streams, file descriptors 0/1/2, man keyword search mechanics | Task D3 hands-on practical redirection |
| 2026-09-19 | Phase 0 | Streams & Redirection (Task D3 Completed) | `ls > file`, `echo >> file`, `cat 2> errorlog` | Demonstrated stdout/stderr separation, pipe vs redirect, and file truncation | Task D4 (Documentation Use) |
| 2026-09-22 | Phase 0 | Documentation-First with `wc` (Task D4 Completed) | `wc -l`, `-m`, `-c`, `-w`, `-L`, `--debug` | Independent H0 extraction from local manuals; analyzed stdin trap and UTF-8 byte disparity | Task D5 (Processes) |
| 2026-09-22 | Phase 0 | Process Lifecycle & Inspection (Task D5 Completed) | `which`, `pgrep -l`, `ps`, `top` telemetry | Mapped GUI instincts to CLI; distinguished disk binaries from active PIDs in RAM | Task D6 (Permissions Recognition) |

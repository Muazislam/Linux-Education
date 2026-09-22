# Competencies

Mastery levels follow `INSTRUCTOR_PROTOCOL.md`.

Detailed mastery confidence, retention, and reassessment tracking lives in `progress/mastery.md`.

Current evidence status: Initial Phase 0 baseline evidence demonstrated on host, VirtualBox VM, and backup systems.

| Competency | Level | Last Evidence | Instructor Note |
|---|---:|---|---|
| Documentation-first workflow | L4 | `wc --help`, `man wc` (Task D4 H0) | Can perform independently; extracts command syntax, flags, and edge cases directly from local manuals without external lookups. |
| Shell basics | L4 | `ls > file`, `echo >> file`, `cat 2> errorlog` | Can perform independently; masters redirection (`>`, `>>`, `2>`), file descriptors (0, 1, 2), and pipeline concepts. |
| Filesystem navigation | L3 | `cd /`, `cd ~`, relative vs absolute paths, `ls -la` | Can perform independently; understands hierarchy and dotfiles. |
| Permissions and ownership | L1 | `ls -l` inspection (directory `d` vs file `-`) | Can recognize; full permission model to be assessed in D6. |
| Process inspection | L3 | `which`, `pgrep -l`, `ps`, `top` (Task D5) | Can perform with guidance; inspects active PIDs, distinguishes disk binaries from RAM execution, and monitors live resource consumption. |
| Service troubleshooting | L1 | `systemctl list-units --state=failed` inspection | Inspected failed units; full service management pending. |
| Network diagnosis | L1 | `ip addr show`, `ip route` host inspection | Can inspect interfaces and routes; diagnostic reasoning pending. |
| Arch package management | L1 | `pacman -Qk` integrity verification | Verified package database integrity on host. |
| VM lab safety | L4 | VirtualBox `arch-lab-01` setup & `phase-0-base` rollback | Can perform independently; snapshot recovery proven. |
| Docker fundamentals | L3 | `docker run hello-world` execution | Engine installed and operational on host. |
| Backup and restore | L3 | `rsync -av` with `--exclude` to ext4 USB | Demonstrated dry-run, exclusions, and file copy. |
| Troubleshooting reasoning | L2 | `/dev/sdc` journalctl diagnosis | Identified buffer I/O & ATA command errors from logs. |

Do not update a competency based only on self-reporting.

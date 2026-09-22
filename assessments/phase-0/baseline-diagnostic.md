# Phase 0 Baseline Diagnostic

Last updated: 2026-08-26

## Purpose

Measure the learner's current Linux reasoning and command-line competence before Module 1. This is diagnostic. It should reveal starting level, not create pressure to perform.

## Environment

Default target: HOST, read-only or harmless commands only.

Do not ask the learner to change system configuration during this diagnostic.

## Instructions For Instructor

- Ask one task at a time.
- Prefer H0 to H2 prompts first.
- Do not reveal full solutions unless the learner is blocked.
- Record commands, reasoning quality, errors, and highest hint level.
- Require the learner to explain what output means.

## Diagnostic Tasks

### D1 - Orientation

Ask the learner to identify:

- current directory;
- current user;
- shell;
- operating system or distribution evidence;
- kernel version evidence.

Competencies sampled: shell navigation, documentation/evidence discipline.

### D2 - Files and Paths

Ask the learner to explain the difference between:

- absolute path and relative path;
- file and directory;
- hidden file and normal file;
- home directory and root directory.

Then ask for harmless commands that would demonstrate each.

Competencies sampled: filesystem mental model, command selection.

### D3 - Streams and Redirection

Ask the learner to reason about:

- standard output;
- standard error;
- pipe;
- redirecting output to a file;
- appending vs overwriting.

Require a safe example using a temporary file.

Competencies sampled: streams, safety, verification.

### D4 - Documentation Use

Give one unfamiliar command from the basic tool list and ask the learner to use local help or a man page to answer:

- what the command does;
- one useful option;
- one risk or caveat;
- how to verify the result.

Competencies sampled: documentation-first learning.

### D5 - Processes

Ask the learner how they would distinguish:

- a program not installed;
- installed but not running;
- running normally;
- running but consuming too many resources.

Do not require privileged actions.

Competencies sampled: process model, diagnostic reasoning.

### D6 - Permissions Recognition

Provide or ask for a harmless file listing and ask the learner to interpret:

- owner;
- group;
- read/write/execute bits;
- directory execute meaning if known.

Competencies sampled: permissions, filesystem safety.

### D7 - Troubleshooting Reasoning

Scenario:

```text
A local web development server does not open in the browser.
```

Ask the learner to list hypotheses and evidence that would distinguish:

- server process not running;
- wrong port;
- firewall or network issue;
- browser/cache issue;
- application error;
- wrong working directory or command.

Competencies sampled: troubleshooting method, full-stack Linux integration.

## Assessment Record

```text
DATE: 2026-09-22
INSTRUCTOR: Antigravity AI
ENVIRONMENT: EndeavourOS Host (interactive non-destructive process inspection)
TASKS COMPLETED:
- D1: Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
- D2: Files and Paths (Absolute vs Relative, File vs Directory, Hidden files/dotfiles, Root / vs Home ~)
- D3: Streams and Redirection (stdin/stdout/stderr, file descriptors 0/1/2, pipe | vs redirect >, truncate > vs append >>, stderr isolation 2>)
- D4: Documentation Use (Independent extraction via `wc --help` and local manual, flag analysis, edge cases, multi-flag verification)
- D5: Processes (Process lifecycle, disk presence vs memory execution, PID inspection, and resource telemetry)
HIGHEST HINT LEVEL: H1 (Conceptual guidance mapping GUI instincts like Application Launcher and System Monitor to CLI tools `which`, `ps`, `pgrep`, `top`)
EVIDENCE REVIEWED:
- State A (Not installed): `which nginx` (verified negative search across all `$PATH` directories).
- State B (Installed, not running): `which geogebra` (confirmed `/usr/bin/geogebra` on disk) and `pgrep -l geogebra` (confirmed no active PID in memory).
- State C (Running normally): `which konsole` and `pgrep -l konsole` (verified active PID `73426`).
- State D (Resource consumption): `top` live telemetry (captured load average, memory stats, and identified `firefox` PID 1851 at 32.7% CPU and `kwin_wayland` PID 1468 at 21.8% CPU).
- Explored `pgrep --help` options and distinguished process IDs from command flags.
STRENGTHS:
- Rapid translation of existing conceptual knowledge into CLI commands.
- Clear mental distinction between executable files on disk (`$PATH`) and running processes in RAM (PIDs).
- Successfully identified live PIDs, parent shells, and resource-heavy processes.
- Demonstrated curiosity by inspecting `pgrep --help` and testing option flags.
SAFETY NOTES: All commands executed were read-only process and path queries on the host.
DOCUMENTATION USE: Consulted `pgrep --help` and `top`.
VERIFICATION QUALITY: Very High; tested negative states, positive states, and real-time process monitoring.
COMPETENCY IMPLICATIONS: Process Inspection competency raised to L3 (Can perform with guidance and inspect active processes).
NEXT ACTION: Proceed to Task D6 (Permissions Recognition).
```

## Current Status

In Progress (Tasks D1, D2, D3, D4, and D5 completed; Tasks D6–D7 remaining).




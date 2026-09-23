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
DATE: 2026-09-23
INSTRUCTOR: Antigravity AI
ENVIRONMENT: EndeavourOS Host (local non-destructive permissions inspection)
TASKS COMPLETED:
- D1: Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
- D2: Files and Paths (Absolute vs Relative, File vs Directory, Hidden files/dotfiles, Root / vs Home ~)
- D3: Streams and Redirection (stdin/stdout/stderr, file descriptors 0/1/2, pipe | vs redirect >, truncate > vs append >>, stderr isolation 2>)
- D4: Documentation Use (Independent extraction via `wc --help` and local manual, flag analysis, edge cases, multi-flag verification)
- D5: Processes (Process lifecycle, disk presence vs memory execution, PID inspection, and resource telemetry)
- D6: Permissions Recognition (File mode deconstruction, read/write/execute triplet model for user/group/other, directory traverse execution bit)
- D7: Troubleshooting Reasoning (Layered network/process diagnostic model: verified process presence via pgrep/ps, port listening via ss -tulpn, identified live servers on 5500/5501 vs 3000, evaluated dmesg kernel permission boundary)
HIGHEST HINT LEVEL: H1 (Prompted to test localhost:3000 hypotheses using pgrep, ps, and ss socket inspection)
EVIDENCE REVIEWED:
- Formulated hypotheses for connection failure: unstarted server process, high memory consumption/resource starvation, and port mismatch.
- Executed `pgrep -l node`, `pgrep -l live-server`, and `ps aux | grep -i server`.
- Executed `ss -tulpn | grep 3000` showing zero listeners on target port 3000.
- Executed `ss -tulpin` discovering active VS Code Live Servers on ports 5500 (`pid=114956`) and 5501 (`pid=127713`).
- Observed Linux kernel security boundary on unprivileged ring buffer access: `dmesg` returned `Operation not permitted`.
STRENGTHS:
- Directly connected process state inspection tools (`pgrep`, `ps`, `top`) to root-cause network and web server issues.
- Successfully interpreted socket listing (`ss`) and identified actual active ports (5500/5501) vs the failing port (3000).
SAFETY NOTES: All commands executed were non-destructive diagnostic reads (`pgrep`, `ps`, `ss`, `dmesg`).
DOCUMENTATION USE: Applied socket terminology and process listing options.
VERIFICATION QUALITY: High; validated directly against live socket tables and running process trees on host.
COMPETENCY IMPLICATIONS: Troubleshooting reasoning raised to L3 (Can perform diagnostic inspection with guidance across processes and network sockets).
NEXT ACTION: Phase 0 complete! Conduct Phase 0 retrospective and proceed to Phase 1 Kickoff.
```

## Current Status

Completed (All Baseline Diagnostic Tasks D1–D7 completed successfully. Ready for Phase 0 sign-off and Phase 1).





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
HIGHEST HINT LEVEL: H2 (Conceptual clarification on the three triplet entities: user, group, other, and the meaning of the execute bit on directories)
EVIDENCE REVIEWED:
- Accurate deconstruction of `-rw-r--r--`:
  - Leading `-` indicates regular file.
  - Three triplets mapped to User/Owner (`rw-`), Group (`r--`), and Others/World (`r--`).
  - `r` = read, `w` = write, `-` = permission not granted.
- Identified file owner (`muazislambabar`) and file group (`muazislambabar`) from `ls -l` columns.
- Explained directory execute permission (`x` on directories enables directory traversal / entry via `cd`, not executable binary execution).
- Verified against live terminal inspection: `ls -ld ~/Downloads` showing `drwxr-xr-x 1 muazislambabar muazislambabar`.
STRENGTHS:
- Solid conceptual synthesis once mapped to the three permission triplets (User, Group, Other).
- Quickly validated real filesystem attributes on `~/Downloads` (`drwxr-xr-x`).
- Successfully navigated documentation search mechanics with `man -k` (discovered need for quoting multi-word phrases like `man -k "file mode"`).
SAFETY NOTES: All commands executed were read-only directory and file listings (`ls -l`, `ls -ld`).
DOCUMENTATION USE: Searched local manuals for permission strings (`chmod`, `access`, `cgroup`, and `man -k`).
VERIFICATION QUALITY: High; verified directly against live directory mode strings on host.
COMPETENCY IMPLICATIONS: Permissions and ownership competency raised to L3 (Can perform with guidance and explain standard UNIX permission triads).
NEXT ACTION: Proceed to Task D7 (Troubleshooting Reasoning).
```

## Current Status

In Progress (Tasks D1–D6 completed; Task D7 remaining - final baseline diagnostic task).





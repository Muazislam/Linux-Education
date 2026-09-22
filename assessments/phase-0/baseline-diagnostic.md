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
ENVIRONMENT: EndeavourOS Host (local manual extraction and non-destructive terminal testing)
TASKS COMPLETED:
- D1: Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
- D2: Files and Paths (Absolute vs Relative, File vs Directory, Hidden files/dotfiles, Root / vs Home ~)
- D3: Streams and Redirection (stdin/stdout/stderr, file descriptors 0/1/2, pipe | vs redirect >, truncate > vs append >>, stderr isolation 2>)
- D4: Documentation Use (Independent extraction via `wc --help` and local manual, flag analysis, edge cases, multi-flag verification)
HIGHEST HINT LEVEL: H0 (Zero hints required; learner independently queried local documentation, explained functionality, and tested options)
EVIDENCE REVIEWED:
- Accurate explanation of `wc` role (counting newlines, words, bytes; pipeline chaining in Unix workflows).
- Identification of `-l` / `--lines` for newline counting.
- Edge case analysis: identified `stdin` reading when no file or `-` is supplied; observed byte vs character count disparity in binary/UTF-8 files.
- Terminal execution on `'Linux Fundamentals.pdf'`:
  - `wc -l` (35661 newlines)
  - `wc -m` (1629574 characters)
  - `wc -c` (2744617 bytes)
  - `wc -w` (64042 words)
  - `wc -L` (1511 max display line length)
  - `wc --debug` and parameter conflict error analysis on `--files0-from=F`
STRENGTHS:
- High autonomy: worked purely from local documentation without external web/AI lookups.
- Explored multiple flags beyond the minimum requirement (`-l`, `-m`, `-c`, `-w`, `-L`, `--debug`, `--files0-from`).
- Accurately distinguished newline counts from visual lines and understood command option syntax.
- Recognized Unix pipeline composition (chaining small utilities together).
CLARIFICATIONS:
- Clarified why byte count (`-c`) differs from character count (`-m`) in modern systems (multi-byte UTF-8 encoding and binary file bytes).
- Clarified the trap of `wc` with no arguments (hangs reading standard input from keyboard until EOF / Ctrl+D).
- Clarified `--files0-from`: expects a file containing null-separated filenames, which conflicts with passing direct file arguments.
SAFETY NOTES: All commands executed were read-only inspection commands on host files.
DOCUMENTATION USE: Read `wc --help` and local manuals directly.
VERIFICATION QUALITY: Very High; tested flags individually, observed parameter constraints, and validated counts.
COMPETENCY IMPLICATIONS: Documentation-First Workflow achieved L4 (independent documentation extraction and application).
NEXT ACTION: Proceed to Task D5 (Processes).
```

## Current Status

In Progress (Tasks D1, D2, D3, and D4 completed; Tasks D5–D7 remaining).



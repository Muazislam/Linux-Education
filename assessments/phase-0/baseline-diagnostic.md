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
DATE: 2026-09-19
INSTRUCTOR: Antigravity AI
ENVIRONMENT: EndeavourOS Host (safe test directory ~/Downloads/ioPractice.tst)
TASKS COMPLETED:
- D1: Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
- D2: Files and Paths (Absolute vs Relative, File vs Directory, Hidden files/dotfiles, Root / vs Home ~)
- D3: Streams and Redirection (stdin/stdout/stderr, file descriptors 0/1/2, pipe | vs redirect >, truncate > vs append >>, stderr isolation 2>)
HIGHEST HINT LEVEL: H3 (Conceptual guidance on shell syntax lookup in `man bash` and file descriptor duplication vs file redirection syntax)
EVIDENCE REVIEWED:
- Terminal session in `~/Downloads/ioPractice.tst`:
  - `ls -la > ddirectory_context.txt` (verified with `cat`)
  - `echo "I am Muaz!" >> ddirectory_context.txt` (verified with `cat`)
  - `cat anime 2> errorlog` (verified stderr redirected to file, quiet screen)
  - `cat errorlog` (verified contents: `cat: anime: No such file or directory`)
  - Investigation of `man -k streams`, `man stderr`, `echo $SHELL`, and `man bash`
STRENGTHS:
- Recognized that `|` and `>` are shell grammar rather than standalone binary utilities; traced interpretation to `/bin/bash` via `echo $SHELL`.
- Discovered and parsed authoritative documentation in `man bash` for pipelines, output redirection `[n]>word`, and appending `[n]>>word`.
- Clear, correct mental model of the three standard streams (stdin 0, stdout 1, stderr 2) and their default bindings to keyboard/display.
- Successfully demonstrated output truncation, appending, and isolating stderr into an error log.
- High curiosity and persistence: spent significant time parsing dense local documentation (`man stderr`, `man bash`) instead of relying purely on web searches.
CLARIFICATIONS & MISTAKES:
- PROCEDURAL / SYNTAX: Attempted `2&1` to isolate errors, which caused bash to interpret `&` as a background job delimiter and attempt running `1` as a command (`bash: 1: command not found`). Clarified: redirecting stderr to stdout is `2>&1` (no spaces, with `>`). Redirecting stderr to a file is simply `2> filename`.
- CONCEPTUAL: Conflated file descriptor numbers (0, 1, 2) with process exit codes (saw `[1]+ Exit 2` and wondered if exit 2 was because stderr is 2). Clarification: exit codes are integer return values (0 = success, non-zero = error) returned by the process to the parent shell, distinct from I/O stream file descriptors.
SAFETY NOTES: All commands executed were non-destructive operations in an isolated test folder (`~/Downloads/ioPractice.tst`).
DOCUMENTATION USE: Consulted `man -k`, `man stderr (3)`, and `man bash (1)`.
VERIFICATION QUALITY: High; verified every file state with `cat` before and after redirection.
COMPETENCY IMPLICATIONS: Task D3 passed with solid conceptual and practical competence.
NEXT ACTION: Proceed to Task D4 (Documentation Use).
```

## Current Status

In Progress (Tasks D1, D2, and D3 completed; Tasks D4–D7 remaining).


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
DATE: 2026-09-04
INSTRUCTOR: Antigravity AI
ENVIRONMENT: EndeavourOS Host (read-only inspection)
TASKS COMPLETED: D1 - Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
HIGHEST HINT LEVEL: H4 (Diagnostic direction provided on `uname -r` vs `uname -v` and shell globbing)
EVIDENCE REVIEWED: Terminal session outputs and search thought process submitted by learner.
STRENGTHS:
- High intellectual honesty and transparent problem-solving narrative.
- Consulted man pages (`man uname`), local command help (`cat --help`), and official documentation (ArchWiki).
- Successfully identified glob syntax error (`cat /etc/* -release` vs `cat /etc/*-release`).
- Grasped the distinction between kernel version (`uname -v`) and kernel release (`uname -r`).
WEAKNESSES:
- Initial tendency to search Google/StackOverflow before testing local discovery tools (`apropos`, `man`, `--help`).
- Trial of unverified commands without prior mental model check (e.g. `echo $0`).
ERRORS CLASSIFIED:
- COMMAND ERROR / SYNTAX: Extra space in `cat /etc/* -release` caused parameter misinterpretation as an option flag.
- DOCUMENTATION / INTERPRETATION: Initial confusion between `uname -v` (kernel build timestamp/version) vs `uname -r` (kernel release number).
SAFETY NOTES: All commands executed were non-destructive read-only host inspections.
DOCUMENTATION USE: Active engagement with `man uname`, `cat --help`, and ArchWiki.
VERIFICATION QUALITY: Solid; learner verified with actual terminal execution outputs.
COMPETENCY IMPLICATIONS: Orientation demonstrated; ready for Task D2 (Files and Paths).
REMEDIATION: Encourage using local man pages and `man -k` / `apropos` first before web searches.
NEXT ACTION: Proceed to Task D2 (Files and Paths).
```

## Current Status

In Progress (Task D1 completed; Tasks D2–D7 remaining).

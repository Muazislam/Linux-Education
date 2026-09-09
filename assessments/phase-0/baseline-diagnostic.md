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
DATE: 2026-09-07
INSTRUCTOR: Antigravity AI
ENVIRONMENT: EndeavourOS Host (read-only inspection)
TASKS COMPLETED:
- D1: Orientation (pwd, whoami, echo $0, cat /etc/*-release, uname -r / -v)
- D2: Files and Paths (Absolute vs Relative, File vs Directory, Hidden files/dotfiles, Root / vs Home ~)
HIGHEST HINT LEVEL: H3 (Subsystem & conceptual clarification on file extensions in Linux and man search navigation)
EVIDENCE REVIEWED:
- Terminal session logs traversing `/home/muazislambabar`, `Claude-Projects`, and `/` root directory.
- `ls -l`, `ls -la`, `ls -a`, `cd /`, `cd ~`, `cd ..`.
- Observations on `d` vs `-` prefix in `ls -l` output.
STRENGTHS:
- Solid conceptual mastery of absolute vs relative path logic and root `/` vs home `~`.
- Successfully discovered and demonstrated `ls -a` / `ls -la` to expose hidden files.
- Noticed leading `d` vs `-` in `ls -l` permissions string to distinguish directories from regular files.
- High curiosity about Unix history (origin of dotfiles) and documented iterative attempts (`cd ..`, `cat`, etc.).
WEAKNESSES:
- Misconception that Linux requires dots/extensions to distinguish files from directories (clarified: extensions are arbitrary name conventions; filesystem metadata/inodes determine type).
- Assumption that hidden files only have owner read-write permissions (clarified: dot denotes visibility, permissions are completely orthogonal).
- Difficulty navigating long `man` pages (remediated with `/pattern` search technique inside pager).
ERRORS CLASSIFIED:
- CONCEPTUAL ERROR: Believing file extensions determine file type in Linux.
- PROCEDURAL ERROR: Trying `cd filename` and `. filename` on HTML file (corrected to `cat filename`).
SAFETY NOTES: All commands executed were safe read-only operations on user host.
DOCUMENTATION USE: Read `man ls` and investigated dotfile conventions.
VERIFICATION QUALITY: High; verified each path transition and listing flag directly in interactive shell.
COMPETENCY IMPLICATIONS: Ready for Task D3 (Streams and Redirection).
REMEDIATION: Practice searching inside `man` using `/` and using the `file` command.
NEXT ACTION: Proceed to Task D3 (Streams and Redirection).
```

## Current Status

In Progress (Tasks D1 & D2 completed; Tasks D3–D7 remaining).

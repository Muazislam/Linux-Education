# Linux Engineering Curriculum Implementation Plan

Last updated: 2026-08-26

## Operating Principle

This curriculum is a secondary but serious track alongside full-stack development. It should build real Linux competence through evidence, labs, troubleshooting, and explanation without taking over the learner's main career study path.

Default pace: 3 to 5 hours per week.

## How To Use This Repository

Start each instructional session by reading:

1. `INSTRUCTOR_PROTOCOL.md`
2. `instructor/BOOTSTRAP.md`
3. `instructor/CHAT_INTERFACE.md`
4. `instructor/CURRENT_STATE.md`
5. `progress/progress.md`
6. the active phase plan in `curriculum/phases/`

Use folders this way:

| Folder | Purpose |
|---|---|
| `instructor/` | Continuity and instructor operating rules |
| `curriculum/` | Roadmap, competency graph, phase plans |
| `modules/` | Module plans and materials as modules begin |
| `progress/` | Current state, levels, weaknesses |
| `labs/` | Lab definitions and lab reports |
| `assessments/` | Diagnostic and formal assessment records |
| `evidence/` | Command outputs, reasoning, verification, screenshots |
| `learning-log/` | Session summaries |
| `mistakes/` | Classified mistakes and recurring patterns |
| `troubleshooting/` | Incident records and break-fix exercises |
| `decisions/` | Durable choices such as VM tooling |
| `remediation/` | Targeted work from observed weaknesses |
| `retrospectives/` | Weekly or periodic review |
| `knowledge/` | Concepts, commands, architecture, documentation notes, mental models |

The top-level index files point to these folders. Detailed records should live inside the folders.

See `IMPLEMENTATION_REPORT.md` for the implementation audit and consistency check.

## Implementation Sequence

### Step 1 - Finish Phase 0

Active plan: `curriculum/phases/phase-0.md`

Required outputs:

- lab environment decision;
- safety checklist;
- evidence template adoption;
- baseline diagnostic;
- updated progress and current state.

Do not start Module 1 before Phase 0 exit criteria are met.

### Step 2 - Start Fundamentals

Begin Phase 1 only after Phase 0 is complete.

Initial focus:

- Unix/Linux mental model;
- kernel vs userspace;
- files, processes, streams, users;
- documentation-first habits.

### Step 3 - Build Command-Line Competence

Move through shell, navigation, streams, redirection, quoting, exit codes, and pipelines using practical tasks instead of command memorization.

### Step 4 - Add System Administration Domains

Progress into permissions, processes, packages, systemd, networking, storage, security, backups, Docker, and virtualization only when prerequisites have evidence.

### Step 5 - Add Failure And Recovery

Use disposable VMs and controlled scenarios for realistic break-fix work:

- services that fail;
- DNS or routing problems;
- package problems;
- permission mistakes;
- disk exhaustion;
- boot and recovery scenarios.

### Step 6 - Final Arch Practical

The final target is not "copy an Arch install." It is a fresh VM exam where the learner can explain, configure, troubleshoot, repair, verify, and document the system.

## Weekly Cadence

Recommended weekly structure:

- 60 minutes: concept and documentation;
- 60 to 120 minutes: guided or independent practice;
- 60 to 120 minutes: lab, troubleshooting, or full-stack integration;
- 15 minutes: progress update and reflection.

Heavy lab weeks can reach 6 to 8 hours, but only occasionally.

## Evidence Standard

Each meaningful task needs evidence of:

- what was attempted;
- what command or action was used;
- what output mattered;
- what the learner thinks it means;
- how the result was verified;
- what remains uncertain.

Use `evidence/phase-0/sample-evidence.md` as the initial template.

## Completion Standard

A topic is not complete because it was read, watched, copied, or run once.

Progress requires demonstrated evidence of:

- reasoning;
- safe operation;
- documentation use;
- correct command choice;
- output interpretation;
- verification;
- ability to troubleshoot.

Use the L0-L7 mastery scale in `INSTRUCTOR_PROTOCOL.md`.

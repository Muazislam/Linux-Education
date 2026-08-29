# Phase 0 - Environment, Safety, Repository Protocol, Baseline

Last updated: 2026-08-26

## Purpose

Phase 0 prepares the learning system before Module 1 starts. It does not certify Linux competence. It establishes safe lab boundaries, confirms tools, defines evidence habits, and measures the learner's starting point.

Linux remains a secondary track that supports full-stack development. Default workload: 3 to 5 hours per week unless the learner explicitly chooses a heavier lab week.

## Entry State

- Curriculum architecture exists in `curriculum/roadmap.md`.
- Instructor protocol exists in `INSTRUCTOR_PROTOCOL.md`.
- No practical competency has been demonstrated in this repository.
- Lab VM, Docker availability, weekly time budget, and baseline skill level are unknown.

## Exit Criteria

Phase 0 is complete only when all of the following are recorded:

- Learner has reviewed and accepted or amended `curriculum/roadmap.md`.
- Lab environment decision is recorded in `decisions/phase-0/lab-environment.md`.
- Safety checklist is completed in `labs/phase-0/safety-checklist.md`.
- Evidence format is accepted and at least one sample evidence record exists.
- Chat interface and learning-record workflow are reviewed.
- Baseline diagnostic is attempted and assessed in `assessments/phase-0/baseline-diagnostic.md`.
- Current state and progress files are updated with observed facts.

## Phase 0 Tasks

| ID | Task | Output | Status |
|---|---|---|---|
| P0-T1 | Review curriculum architecture | Accepted changes or questions | Not started |
| P0-T2 | Choose weekly Linux time budget | Progress note | Not started |
| P0-T3 | Choose disposable VM tool | `decisions/phase-0/lab-environment.md` | Not started |
| P0-T4 | Check Docker availability | Evidence record | Not started |
| P0-T5 | Confirm host safety boundaries | `labs/phase-0/safety-checklist.md` | Not started |
| P0-T6 | Learn evidence/reporting format | `evidence/phase-0/sample-evidence.md` | Not started |
| P0-T7 | Review chat and learning-record workflow | `instructor/CHAT_INTERFACE.md` and `IMPLEMENTATION_PLAN.md` | Not started |
| P0-T8 | Complete baseline diagnostic | `assessments/phase-0/baseline-diagnostic.md` | Not started |
| P0-T9 | Update progress and next module | `progress/progress.md` and `instructor/CURRENT_STATE.md` | Not started |

## Required Decisions

Record each decision with date, context, options considered, decision, and reason.

- Weekly Linux study budget: recommended 3 to 5 hours.
- VM tool: GNOME Boxes, VirtualBox, virt-manager/QEMU/KVM, or another tool.
- Docker track: installed now, install later, or defer until a module needs it.
- Evidence storage: concise Markdown records in `evidence/`, with large logs summarized or attached only when necessary.

## Safety Gate

Before any lab that can damage a system, the instructor must confirm:

- target is HOST, LAB VM, CONTAINER, or REMOTE SYSTEM;
- target is disposable when destructive work is involved;
- snapshot or recovery path exists when appropriate;
- learner can explain the risk category;
- host system is not the target.

Phase 0 includes no destructive labs.

## Baseline Assessment Scope

The baseline diagnostic samples current ability in:

- shell navigation;
- files and paths;
- streams and redirection;
- command help and documentation use;
- process inspection basics;
- permissions recognition;
- safe reasoning and verification;
- troubleshooting method.

The baseline is diagnostic, not punitive. It determines where Module 1 should start and how much remediation is needed.

## Instructor Notes

Use Socratic prompting during the diagnostic. Record the highest hint level needed. Do not mark competencies above L0 unless the learner provides evidence. Self-reported familiarity may be noted, but it does not raise mastery level.

## Next Phase

After Phase 0 exits cleanly, begin Phase 1: Unix/Linux mental model.

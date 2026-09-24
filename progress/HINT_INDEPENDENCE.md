# Hint And Independence Tracking

Last updated: 2026-09-25

The goal is not merely task completion. The goal is reduced dependency on instructor hints over time.

## Hint Scale

Use the scale in `INSTRUCTOR_PROTOCOL.md`:

```text
H0 - No hint; learner proceeds independently.
H1 - Clarifying question.
H2 - Conceptual hint.
H3 - Subsystem hint.
H4 - Diagnostic direction.
H5 - Tool or command category.
H6 - Procedural guidance.
H7 - Explicit solution.
```

## Independence Dimensions

For significant tasks, evaluate whether the learner can:

- identify the problem;
- choose tools;
- read documentation;
- form hypotheses;
- perform changes safely;
- verify results;
- recover from failures;
- explain the result.

## Pattern Rule

Repeated H6/H7 support or repeated inability to choose evidence means the competency is not mastered, even if the final task outcome succeeds.

| Date | Task | Competency | Highest Hint | Independence Note | Follow-up |
|---|---|---|---:|---|---|
| 2026-09-22 | D4 Documentation Use | Documentation | H0 | Independently extracted `wc` behavior, flags, constraints, and edge cases from local documentation. | Reassess in Module 1 |
| 2026-09-23 | D7 Troubleshooting Reasoning | Troubleshooting | H1 | Needed one clarifying prompt to test the localhost:3000 hypothesis; then selected and interpreted `pgrep`, `ps`, and `ss` evidence. | Repeat independently in Module 1 |

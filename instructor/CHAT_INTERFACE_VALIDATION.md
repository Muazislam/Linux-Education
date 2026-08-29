# Chat Interface Validation

Last updated: 2026-08-26

This file validates that `instructor/CHAT_INTERFACE.md` can route normal learner requests without requiring rigid command syntax.

| Learner Message | Expected Mode | Required Instructor Behavior |
|---|---|---|
| Continue my curriculum. | CONTINUE | Read current state, progress, mastery, weaknesses, and relevant records; continue from last meaningful state. |
| I don't understand processes. | EXPLAIN or TEACH | Determine whether the gap is terminology, concept, misconception, or lack of practice; explain at suitable depth. |
| I'm stuck on this lab. | STUCK or LAB | Ask what was expected, what happened, what evidence exists, and what was tried; provide the smallest useful hint. |
| Give me a hard networking problem. | PRACTICE or ASSESS | Use current competency and weaknesses; avoid revealing subsystem details if assessment mode is intended. |
| Review what I did. | REVIEW | Evaluate correctness, reasoning, documentation use, safety, verification, system understanding, and independence. |
| What are my biggest weaknesses? | WEAKNESSES | Inspect weakness register, mistakes, assessments, hint dependency, and evidence patterns. |
| Quiz me. | QUIZ | Generate reasoning-focused questions from current module, prerequisites, weak competencies, and mistakes. |
| I want the direct answer. | ANSWER | Provide direct explanation unless in formal assessment; if in assessment, ask whether to terminate it. |
| I think I broke my VM. | TROUBLESHOOT | Identify environment, preserve evidence, ask expected vs actual behavior, form hypotheses, guide safely. |
| Switch me into assessment mode. | ASSESS | Begin formal assessment, preserve integrity, record outcome afterward. |

Validation result: pass. The interface maps natural language to modes while preserving normal conversation.

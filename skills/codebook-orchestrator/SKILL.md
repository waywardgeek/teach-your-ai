---
name: codebook-orchestrator
description: Regenerate an existing codebook with coder, author, and review sub-agents.
---

# Codebook orchestrator

You are the top-level agent for **executing an existing book**, not for initial book writing. Creation uses the human's separate top-level author and coder conversations; do not replace those with hidden sub-agent work.

Before regeneration, read the book in chapter order, the [execution workflow](../../docs/book-execution-workflow.md), and [carryover notes](../../docs/carryover.md). Use the book's own versions when supplied. Before launching students, incorporate lessons and documented fixes from the previous run’s carryover chapter into the relevant chapters, working with the human and author. This is a correction pass grounded in prior evidence, not permission to add requirements. Record where the lessons went. Read the corrected current chapter again before delegation.

Establish the starting code, solution workspace, external graders, reference implementation, and authorized test environment with the human. Preserve existing implementations, unrelated work, and credentials. Keep the target reference and private grading material out of student inputs.

## Per-chapter sequence

1. Launch a fresh coder sub-agent with the [coding skill](../codebook-coding/SKILL.md) in student mode. Supply the execution workflow, carryover notes, full chapter, accepted earlier code, and grader command. It implements, tests, and leaves feedback.
2. Inspect its work and notes, then launch an [author](../codebook-author/SKILL.md) to make feedback-driven corrections to the existing chapter. Explicitly prohibit new requirements, scope expansion, and speculative rewriting. Route a genuine contract change to the human instead.
3. Run a [code reviewer](../codebook-code-reviewer/SKILL.md) and [text reviewer](../codebook-text-reviewer/SKILL.md) against the implementation, corrected chapter, and evidence. Give the code reviewer the matching reference implementation as well as the new code. Do not give that privileged material to the student.
4. Resolve findings with the appropriate owner. If the new implementation is worse than the reference in a concrete way, require correction: iterate with the coder or have the author clarify the existing design intent and launch a fresh student. Do not accept known regression just because grades pass. Do not send reference source or answer-revealing comparisons to the student.
5. Obtain the human's acceptance of the chapter, graders, and solution before advancing. Update the carryover chapter with the accepted state and relevant fixes: what failed, why, what changed, what was checked, and where the chapter now teaches the correction. The next run begins by folding these lessons into the book.

After substantive chapter repairs, use a fresh student from the accepted prior-chapter baseline. A student that learned missing knowledge privately cannot establish that the repaired page now teaches it. Do not invent a fixed number of review rounds; respect any correction limit agreed with the human and report unresolved problems when reached.

## Coordination discipline

Give bounded tasks, clear ownership, exact inputs, and output paths. Read returned files and evidence yourself, collect final notes, and join delegated work before treating it as complete. A completion label, expired wait, or claimed pass is not an inspected result.

Classify failures before assigning repairs: implementation, chapter, grader, environment, or unresolved design decision. Preserve useful evidence. Keep durable knowledge in the chapter or appropriate source document rather than secretly supplying it in student prompts.

Keep progress reports useful and concise. Continue agreed work without routine permission loops, but stop for genuine blockers, consequential ambiguity, authorization boundaries, or agreed limits. Reviewers assist the human; they cannot accept a chapter on the human's behalf.

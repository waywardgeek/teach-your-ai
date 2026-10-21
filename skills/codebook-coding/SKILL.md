---
name: codebook-coding
description: Build reference solutions and external graders, or execute chapters as a fresh student.
---

# Codebook coding

Confirm your mode. A reference coder and a fresh student have different inputs and permissions.

## Reference coder: creating a chapter

Work in a **top-level conversation with the human**, who steers you as you build. Read the author's brief first, then its required readings, the initial chapter packet, and existing code. Follow the [chapter-writing procedure](../../docs/chapter-writing-procedure.md).

Build both the solution and graders from the stated contract. Keep grader code, private fixtures, and grading assets **outside the solution source tree**. Provide a documented entry point that grades a separately supplied implementation, not only your reference checkout.

Run grading and relevant tests. Investigate failures rather than changing the contract or weakening a check to obtain a pass. Bring factual errors, design failures, ambiguities, and consequential changes back to the human and author. Be willing to discard an initial approach that does not work.

After grading passes, leave review notes for the author: what was built and where, commands and observed outcomes, corrections, deviations, missing requirements, and implementation lessons worth teaching. For fixes, explain what failed, why it happened, what changed, and how it was checked, so the author can teach the correction and the carryover chapter can preserve it. Separate observations from recommendations. If blocked, report that instead of claiming completion.

## Fresh student: executing a completed chapter

Read the [execution workflow](../../docs/book-execution-workflow.md), [carryover notes](../../docs/carryover.md), and the full chapter before editing. Inspect accepted earlier code before extending it. Use the book's actual workflow and notes when supplied.

For a new book's chapter test, work in a fresh top-level conversation with the human. For orchestrated regeneration, work as the orchestrator's fresh coder sub-agent. In either case:

- Build from the chapter and accepted prerequisite implementation. Do not consult the target reference solution, previous students' target solutions, private authoring discussions, or grader implementation.
- Run the original grader through its documented entry point. Its normal output is feedback; do not read or edit grader source or private fixtures. Report suspected grader defects with evidence to the grader owner.
- Keep implementation and local tests in the assigned solution tree. Do not edit chapter text or privileged grading files to obtain a pass.
- Extend the real earlier implementation. Do not stub it out or create a parallel implementation just to pass this chapter's checks.
- Run grading and relevant project tests. Leave review notes on results, limitations, ambiguities, deviations, and concrete chapter corrections. Explain fixes and their causes clearly enough for the author and carryover chapter to prevent the same mistake next time. Do not invent a major requirement privately and then report the chapter as sufficient.

## Both modes

Read actual code and relevant current documentation before judging or changing it. Use the simplest adequate design. Passing grades do not excuse unnecessary machinery, hacks, missing behavior, or a disconnected exercise implementation.

Exercise real behavior. Use small faithful fakes at external boundaries when appropriate, not test doubles that replace the behavior under test or accepted earlier chapters. Follow the project's mock policy; do not introduce an exception without the human's approval.

Check that important tests can catch plausible defects. Use focused mutations in a scratch copy when useful. A compilation failure or unrelated crash does not establish that the intended behavioral check works. Keep the original grader unchanged. Do not build a generic mutation framework just to record evidence.

Ground external protocols in authoritative documentation and observed behavior. An invented protocol and equally invented fixtures can agree while both are wrong. When live services or a human interface are part of the chapter, exercise the real path as authorized. Fakes and grader passes do not establish live success.

Keep credentials private and respect boundaries around destructive actions, external effects, deployment, restarts, and costs. Distinguish setup failure, product failure, and limitations of a test. Preserve useful evidence and state uncertainty honestly.

Reuse valid evidence for unchanged work; rerun checks when changed inputs or a concrete correctness question justify it. Keep notes concise and actionable. Do not claim required behavior is complete when it remains failing or unverified without clearly stating the limitation.

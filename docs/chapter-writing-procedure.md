# Chapter-writing procedure

This is the procedure for **creating a chapter with a human expert**, not for regenerating an existing book. It supersedes the outline-first approach: write only enough to launch the coder, then learn from the build before finishing the chapter.

## Ownership and preparation

The human is the expert and final reviewer. Work in separate **top-level author and coder conversations**, with the human steering each as it works. This is pair-writing and pair-programming, not a sub-agent orchestration loop. Additional review agents are optional assistance.

The author owns chapter text and the coder brief. The reference coder owns the solution, external graders, and implementation review. A fresh student later tests the completed chapter.

Before writing each chapter, the author reads this document and [voice.md](voice.md) **in full**, relevant previous chapters, and the human's source material. On return passes, also read coder/student notes and inspect relevant implementation evidence. Do not rely on remembered summaries.

Ask for concrete lessons and decisions as they arise. Keep consequential uncertainties visible. Do not demand that the human first produce a complete design document.

## 1. Write the minimum initial packet

Write only:

- **TL;DR:** the implementable specification. State relevant interfaces, inputs and outputs, state changes, errors, constraints, and observable acceptance behavior. Pin down what compatibility and grading depend on; avoid prescribing internal structure unless it carries the human's actual lesson.
- **The idea in plain words:** the problem, mechanism, why the approach is worth using, and important tradeoffs. Do not merely repeat signatures in prose.
- **Exercises:** implementation tasks and what each result must demonstrate. Together with the TL;DR and explanation, these must be enough to implement both solution and graders.
- **Coder brief:** the working handoff described below.

**No separate outline or outline-review stage. Do not write the remainder of the chapter yet.** The initial packet needs enough precision to build, not the polish of a finished chapter. If a requirement is unknown, ask the human rather than burying a guess in a test.

## 2. Brief the coder and switch conversations

The brief tells the reference coder to read it first. Include:

- The initial chapter packet and required source documents.
- The accepted starting code and intended increment.
- Solution and separate grader locations.
- What to implement and grade, boundaries, and non-goals.
- Relevant external documentation and authorized test setup, where needed.
- Required outputs: solution, runnable graders, and review notes for the author.

Reference the chapter's contract rather than maintaining a conflicting duplicate. Any lasting requirement discovered in the brief must reach the published chapter. The brief can carry authoring context that a later student should not need.

The human starts the separate top-level coder with the [coding skill](../skills/codebook-coding/SKILL.md) in reference mode. Continue working interactively; this is not a blind handoff.

## 3. Build the solution and external graders

The coder reads the brief first and its required materials, inspects existing code, and builds the agreed behavior with the human steering.

Keep grader code, private fixtures, and grading assets **outside the solution source tree**. Provide a documented command to run grading against a supplied solution. Grading must not depend on the author's particular reference checkout.

Grade the contract, not incidental implementation details. Check important boundary and failure behavior as well as the happy path. Establish that important checks reject relevant wrong behavior. Exercise real internal code; use faithful fakes for external peers only where appropriate.

Run grading and relevant tests. Investigate failures instead of relaxing checks to manufacture a pass. Bring factual errors, design failures, and ambiguities to the human and author. The entire proposed approach may need to change.

Once grading passes, leave review notes for the author. If blocked, report the blocker instead of calling the work complete. Include:

- What was built, where it lives, and how to run and grade it.
- Commands actually run, observed results, and limitations.
- Corrections, surprises, and consequential deviations from the initial packet.
- Implementation lessons worth teaching and unresolved questions.

These notes are primary material for the chapter, not ceremonial sign-off.

## 4. Return to the author, revise, then finish writing

The human returns to the author with the coder's notes. The author reads the notes and evidence and examines relevant code. Resolve consequential changes with the human.

Fix the TL;DR, plain-words section, and exercises first. If building invalidated the initial approach, replace it. Do not preserve an attractive explanation of a design that failed. Reconcile contract changes with the coder: update solution and graders and rerun affected checks. A prose-only clarification does not justify unrelated test reruns.

Then write the remainder of the chapter: detailed mechanism, examples, important implementation decisions, actual pitfalls, and lessons for later chapters. Use observed work, not an imagined development story. Do not publish a debugging transcript or a complete target solution that lets students bypass implementation.

## 5. Test the completed page with a fresh student

Use a fresh top-level coding conversation and the [execution workflow's chapter-test instructions](book-execution-workflow.md#testing-a-newly-written-chapter). The student loads the coding skill in student mode and reads the execution workflow, carryover notes, and chapter in full.

Supply accepted prerequisite code and the grader entry point. Withhold the target reference solution, private authoring context, and grader implementation. The student builds, runs grading and relevant tests, and leaves review notes.

If the student needs a private explanation, put the missing knowledge on the page. Repair the actual cause of a failure: implementation, chapter, grader, environment, or unresolved design decision. A failed run does not automatically prove a bad chapter; a passing run does not prove a complete one.

Document fixes so the next iteration can avoid the same mistake: what failed, why, what changed, how it was checked, and where the chapter now teaches the lesson. After substantive chapter changes, use another fresh student from the accepted prior-chapter baseline. The previous student's accumulated context cannot establish that the repaired page now teaches the missing lesson.

Repeat feedback and correction as needed; unresolved engineering choices belong with the human.

## 6. Human acceptance before the next chapter

The human must be satisfied with all three artifacts:

- **Chapter:** accurately captures and teaches the intended knowledge.
- **Graders:** check the intended requirements without hidden or incorrect demands.
- **Solution:** sound, understandable, and integrated with earlier work.

Passing tests and agent reviews inform this judgment; they do not replace it. The human chooses how to obtain sufficient understanding—no particular review medium is prescribed. **Do not advance without their acceptance.**

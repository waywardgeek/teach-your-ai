# Book-execution workflow

This procedure uses a completed book to regenerate software. A top-level orchestrator manages coder, author, code-reviewer, and text-reviewer sub-agents. It is **not** the human's interactive author–coder process for initially writing the book.

A newly completed chapter can also be tested in a fresh top-level student conversation; see [the chapter-test variant](#testing-a-newly-written-chapter).

## First, fold the previous run's lessons into the book

Before every regeneration, read the book's carryover chapter and the documented fixes from the previous implementation. **Incorporate those lessons into the relevant chapters before launching students.** The next run should build from a better book, not rely on extra private instructions to avoid the same mistakes.

The orchestrator loads its [skill](../skills/codebook-orchestrator/SKILL.md) and reads the book in chapter order, this workflow, and [carryover.md](carryover.md). Work with the human and author to reconcile recorded lessons with the existing contract and implementation evidence. Correct missing explanations, stale details, and known mistakes; this is not permission to invent requirements. Escalate any proposed contract change to the human.

Record where each lesson was incorporated. Keep relevant cross-cutting execution notes and unresolved questions in carryover, but do not treat them as a substitute for repairing the chapter. Read the corrected chapter again before delegating it.

## Prepare the workspace

Establish with the human:

- Accepted starting code and the solution workspace.
- External grader entry points and their usage instructions.
- The existing reference implementation for privileged reviewer comparison.
- Dependencies, test environment, and authorized live checks.

Each execution produces a new implementation. Use a separate workspace rather than destroying previous work. Preserve credentials and unrelated files. Distinguish unavailable setup from a chapter or product defect. Knowing later chapters prepares the coordinator to route questions, not to design future work on the student's behalf.

## 1. Coder first

Launch a fresh coder sub-agent with the [coding skill](../skills/codebook-coding/SKILL.md) in **student mode**, this workflow, carryover notes, the full chapter, public prerequisites, accepted earlier code, and the grader command. The student reads its instructions and chapter in full before editing. The book-wide lesson integration above is coordinator preparation, not an extra authoring task for the student.

Keep the target reference solution, private authoring discussions, previous students' target solutions, grader source, and private fixtures out of student inputs. A separate directory supports this boundary but is not by itself a security sandbox.

The student extends the real accepted implementation, runs the original grader and relevant tests, and leaves feedback: commands and outcomes, gaps, ambiguities, deviations, suspected defects, and limitations. Test integration with earlier chapters, not just isolated exercises. Exercise live services and the human interface when part of the chapter and authorized; label unavailable checks honestly.

The student may run the grader and use its ordinary output, but must not inspect or alter its implementation. Suspected grading defects go to the grader owner with evidence. Student-created local tests stay with the solution.

## 2. Author corrects the existing chapter

The orchestrator inspects the coder's work and notes, then launches an [author](../skills/codebook-author/SKILL.md). Supply the existing chapter, relevant feedback and evidence, voice guide, and chapter-writing procedure.

**Limit this pass to corrections supported by coder feedback. Do not add requirements, expand scope, or draft a new chapter.** Clarify the existing contract, repair factual errors, and align misleading explanations with verified behavior. Do not silently legitimize an implementation deviation by changing the specification to match it.

If the repair requires a new engineering decision or a contract change, stop and bring that choice to the human. Routine correction authority does not authorize new requirements.

## 3. Review the code and chapter

Run the [code reviewer](../skills/codebook-code-reviewer/SKILL.md) and [text reviewer](../skills/codebook-text-reviewer/SKILL.md) after the coder and author passes. Supply the new implementation, corrected chapter, and relevant evidence.

**The code reviewer may inspect both the reference implementation and the new code.** Compare matching chapter scope and judge both against the current contract. Look for concrete regressions in correctness, clarity, simplicity, testing, and integration. Different structure or line counts alone do not establish quality; the reference is not infallible.

If the new code is worse, drive correction rather than accepting a passing grade:

- Iterate with the coder on concrete findings and verify the changes; or
- Have the author improve the chapter's explanation of the existing design intent, then launch a fresh student from the accepted prior-chapter baseline.

Return reasons and findings to students, not reference source, answer-revealing diffs, or private grading material. Do not introduce new feature requirements under the label of review. If correction cannot be completed within an agreed limit, report the unresolved issue to the human.

The text reviewer checks factual accuracy, teaching quality, implementability, and the scope of the author's edits. It must not confuse a plausible explanation with verified implementation behavior.

## 4. Repair, document the lesson, and retest

Classify failures before assigning work:

- **Implementation bug:** coder repairs against the existing contract.
- **Missing or misleading explanation:** author corrects the chapter.
- **Grader defect:** grader owner investigates against the intended contract, without weakening grading merely to obtain a pass.
- **Environment failure:** fix or report setup separately.
- **Unresolved design decision:** human decides.

Inspect actual edits and results. Collect final agent notes and join delegated work before treating it as complete. Preserve useful failure evidence and report uncertainty. Avoid repetitive tests or review paperwork that do not address a concrete risk.

Every relevant fix must leave enough explanation for the next iteration: the symptom, cause, correction, observed verification, and chapter location that now teaches how to avoid it. Use the existing review/carryover notes; a separate reporting system is unnecessary. A code patch alone does not improve the book.

After substantive chapter corrections, retest with a fresh student using accepted prior-chapter code, not the target solution produced during diagnosis. A student that received private clarification demonstrates success with assistance, not that the original page was sufficient.

Keep durable knowledge in the chapter or appropriate source document, not only private handoffs. Keep prose, graders, and implementation consistent. Do not conceal unresolved problems by changing the story in a completion report.

## 5. Human acceptance, then advance

The human must be satisfied with the chapter, graders, and solution before the next chapter. Reviewer approval and passing tests support this judgment but cannot replace it. The human chooses how to obtain sufficient understanding.

Update carryover with the accepted state, relevant lessons, links to chapter corrections, and remaining issues. At the end of the book, run relevant whole-system checks and exercise intended use where applicable. Document fixes discovered in the assembled system too, so the next run benefits from them.

Report what was built and tested, failures, and remaining limitations. A successful regeneration is evidence of knowledge transfer, not proof of every design choice or future change. The next execution starts by folding these recorded lessons back into the book.

## Testing a newly written chapter

During initial book writing, the human opens a **fresh top-level student conversation**, not an orchestration loop. Give it the coding skill in student mode, this workflow, carryover notes, the completed chapter, accepted prerequisite code, and grader command.

Apply the same input boundaries, testing obligations, and review-note requirements as the regeneration student. The human returns findings to the top-level author, steers corrections, and starts another fresh student after substantive changes. Extra review agents are optional in this mode. Human acceptance of chapter, graders, and solution is still required before moving on.

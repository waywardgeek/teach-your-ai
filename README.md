# Teach Your AI What You Know

**Are you an expert at building at least one kind of software system?** Give this document to your LLM. It will guide you in turning your hard-won engineering knowledge into an executable specification: chapters from which fresh agents can rebuild the software and check their work. If you do not yet have that experience, feel free to read on, but this process cannot supply the expertise it needs from you.

**This document is meant to be executed, not just summarized.** You supply the judgment; the LLM helps draw it out, write it down, and test whether it survives outside your conversation. Ordinary inference does not update a model's trained weights with your project's lessons. A codebook preserves those lessons in explanations, contracts, exercises, and graders. The code can be replaced; the knowledge survives and grows as further builds improve the book.

## LLM: begin here

- **Look for relevant experience.** One concrete account of building this kind of system is enough to begin. Ask what failed and what experience taught the human to do differently. Inspect their existing code with them if you need evidence; do not demand credentials or a polished design. Repository access alone does not establish expertise.
- **Make the case to a suitable human.** Connect the method to their experience: “You know why this design works and where the tempting alternatives fail. We can preserve that judgment and test whether a fresh agent can build from it without this conversation.” Explain their active steering and review role. Offer to start with a concrete part they know well.
- **Do not manufacture the expert.** If the human is largely inexperienced at coding or has not built this kind of system, explain that this method is not a fit yet. Ordinary AI-assisted development remains useful, but agent-invented design is not captured human expertise.
- **Choose the mode below and read its linked instructions in full.** Creating a book and executing one use different working relationships.

## Write a book: human-led author and coder conversations

**This is pair-writing and pair-programming, not sub-agent orchestration.** The human alternates between separate, top-level author and coder agents, steering each as it works.

1. **Prepare the author.** Load the [author skill](skills/codebook-author/SKILL.md). Before each chapter, read [voice.md](docs/voice.md) and the [chapter-writing procedure](docs/chapter-writing-procedure.md) in full, plus relevant preceding chapters and source material.
2. **Write only the initial packet:** TL;DR specification, “the idea in plain words,” exercises, and a coder brief—enough to implement both solution and graders. **No separate outline or remainder of the chapter yet.** Building may overturn the approach.
3. **Switch to the coder.** In a separate top-level conversation, load the [coding skill](skills/codebook-coding/SKILL.md) in reference mode and read the brief first. With the human steering, build the solution and graders. Keep graders **outside the solution source tree**. Get grading to pass and leave review notes for the author.
4. **Return to the author.** Use those findings to revise—or replace—the initial approach. Reconcile the contract, solution, and graders, then write the remainder of the chapter from what actually worked.
5. **Test with a fresh student.** In a fresh top-level coding conversation, use student mode and the [execution workflow](docs/book-execution-workflow.md). Supply the completed chapter, accepted prerequisite code, and grader entry point—not the target reference solution, private authoring context, or grader implementation. The student builds, grades, and leaves notes. The author repairs gaps; another fresh student tests the revised chapter.
6. **Human acceptance before advancing.** The human must be satisfied with the chapter, graders, and solution before the next chapter. Passing tests and optional review agents inform that judgment; they do not replace it. The human chooses how to obtain sufficient understanding.

Keep initial authoring small. The coder's findings are material for the chapter, not paperwork after the real writing.

## Execute a book: orchestrated regeneration

Use a top-level [orchestrator](skills/codebook-orchestrator/SKILL.md) and the [execution workflow](docs/book-execution-workflow.md).

**Start every run by folding lessons from the previous run's [carryover chapter](docs/carryover.md) into the relevant chapters.** Read the book in order and repair it from documented experience before launching students. Create a separate solution workspace; preserve the previous implementation.

For each chapter:

1. **Coder first.** Launch a fresh coding sub-agent in student mode. It reads the execution workflow, carryover chapter, and full chapter, then extends accepted earlier code, runs grading and relevant tests, and leaves feedback.
2. **Author second.** Make feedback-driven corrections to the existing chapter. **Do not add requirements or expand scope.**
3. **Review code and chapter.** Run the [code reviewer](skills/codebook-code-reviewer/SKILL.md) and [text reviewer](skills/codebook-text-reviewer/SKILL.md). The code reviewer may inspect both reference and new implementations. If the new code is worse, drive corrections with the coder or improve the chapter's guidance and start a fresh student. Do not expose reference code to the student or weaken grading to manufacture success.
4. **Human acceptance, then advance.** Require acceptance of chapter, graders, and solution. Document fixes, their causes, verification, and chapter corrections in carryover so the next iteration avoids the same mistakes. At the end, check the assembled system and its intended use, not just isolated exercises.

The explanation preserves **why**; the contract and exercises state **what to build**; external graders check observable commitments against an independently supplied solution. Fresh execution tests whether the necessary knowledge reached the page. It does not replace the human's judgment or prove every design choice and check correct.

## Using these instructions

Skills are in [`skills/`](skills/); procedures and the example voice guide are in [`docs/`](docs/). Load skills through your agent environment or read their `SKILL.md` files directly. Relative links resolve from the containing file; preserve or update companion-document links if installing skills elsewhere.

These are cleaned-up adaptations of Ensemble's authoring documents, coder briefs and reviews, execution workflow, carryover documents, and agent skills, reconciled with the human author's account of the settled process. They are not verbatim historical copies. Adapt the example voice with the human. If a book already has its own instructions, read those in full and resolve conflicts explicitly rather than silently substituting these examples.

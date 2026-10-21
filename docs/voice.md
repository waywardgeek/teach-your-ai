# Voice

This is an example adapted from Ensemble's voice guide. Tune it with the human for their book; do not invent their experience or make them impersonate another author. Read the agreed guide in full before writing each chapter or making a return pass.

## Who speaks, and to whom

An experienced builder is explaining a system to a capable programmer and the coding agent working with them. Sound like a colleague at a whiteboard: direct, concrete, and willing to explain why an attractive alternative failed.

Use the human's experience as the source of judgment. First person is appropriate for experiences they actually supplied and approved. Do not invent battle stories, collaborators, quotations, debugging sessions, or claims that “we tried” something. If a useful story is missing, ask for it or omit it.

## Teach the idea before the machinery

Start the explanation with the problem: what a programmer is trying to do and what gets in the way. Give the plain-language idea before formal names and API details. Use a small concrete example to carry the reasoning. Explain what the system does, why that solves the problem, and where the design stops applying.

An analogy earns its place by mapping to the actual mechanism. Do not substitute vague metaphors for explaining state, control flow, boundaries, or failure behavior. Develop important ideas in connected prose rather than a wall of labels and bullets.

## Separate explanation from contract

The TL;DR is the compact implementable contract. Use bullets, tables, schemas, and short examples where they make exact requirements easier to find. State observable behavior precisely; leave irrelevant internal choices open.

“The idea in plain words” explains the problem, mechanism, and reasons for the contract. It must be understandable before the reader has built the solution. Exercises turn the contract into work with observable outcomes. Later prose teaches what implementation established; it cannot substitute for a missing contract.

Name boundaries and important negative requirements: what must not be exposed, blocked, lost, or coupled. Keep names and examples consistent across the chapter and code. Do not hide obligations only in the grader or coder brief.

## Use implementation experience honestly

Write the later narrative after the coder returns evidence. A failed path can teach the reason for the final design. Tell the lesson, not the entire transcript of failed commands. Do not promote one passing run into a universal claim or a future idea into a shipped feature.

Check factual claims, library behavior, and snippets against actual sources and the built system. Do not invent execution results. Mark historical contrasts clearly so readers can distinguish an abandoned design from the current contract. Distinguish verified observations from hypotheses.

## Keep it useful

Prefer ordinary words and active sentences. Use “you” for the reader and “we” for reasoning together, not fabricated shared experience. Avoid marketing, self-congratulation, empty promises of simplicity, and unnecessary jargon.

Use code where code teaches; do not paste the entire reference solution into the explanation. Headings and lists help navigation, but leave enough connected reasoning to explain why the system has this shape.

Do not impose arbitrary word counts, paragraph lengths, or numbers of anecdotes. Keep material that carries knowledge; cut repetition and generic filler. The reader should finish able to explain the idea, implement its contract, and understand the important tradeoffs.

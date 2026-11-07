---
name: slow-down-understanding
description: Explain a topic slowly for quick understanding, starting immediately with the big picture and connecting each small explanation to it. Use when the user invokes $slow-down-understanding, asks to slow down for quick understanding, or wants a gradual explanation without a placement check or quiz. Prefer this over slow-down-learning when the user wants explanation rather than practice.
---

# Slow down for quick understanding

Help the user understand what something means, how it works, and why it matters. Start explaining immediately, using the conversation to choose a sensible starting point. Stay in this mode for the topic until the user asks to speed up, return to normal mode, or switch to learning mode.

## Start with the big picture

- Do not start with placement questions or ask the user to prove what they know.
- Open with one or two plain sentences explaining the overall purpose or problem. Then explain the first useful piece in that same response.
- Keep the big picture short. Do not turn it into a syllabus, a list of prerequisites, or a long overview.
- If the topic is missing from the conversation, ask only what they want explained. This is clarification, not a level check.

## Prepare a reference solution for code and algorithm problems

- Before the first hint, work out a complete solution to the actual problem, including the requested outputs and constraints. Use it as the teaching reference. Keep the full solution private when the learner asks for hints.
- Plan the lesson backward from the result. Identify the decision needed to produce it, then the information needed to make that decision. Use those dependencies to choose the next small step the learner can understand.

## Explain one piece at a time

- At the start of every teaching step, tell the learner what this piece will help them decide or do and how that contributes to their goal. Give that reason before the example, calculation, or guiding question. For example, “We want to know which trade leaves you with more euros. First we need to express both balances in euros so we can compare them.”

- Focus each message on one main idea, step, or relationship. Aim for about 3–6 sentences and one small example when useful.
- Define every important term in plain words before relying on it, including prerequisite terms. Naming a term or pointing to an example is not a definition; explain what it means and connect it to the current example.
- Assume prior understanding only when the user explicitly says they already know the relevant term or concept. Do not infer understanding from their course level, use of terminology, silence, or an earlier assistant explanation.
- When the user asks to speed up, make definitions brief rather than skipping them. Avoid introducing several unfamiliar terms without explaining each one.
- Use a concrete example to make the idea visible. Reuse the same example across the topic where possible.
- For code or calculations, explain one meaningful step and what it accomplishes. Do not turn the explanation into an exercise unless requested.
- When the learner would have to picture how parts connect, where something sits, or what changes between steps, draw a quick sketch if it makes that relationship easier to see. Show only the parts needed for the current point, using labels from the example. Introduce visual references before using them: for an arrow, show or name both endpoints and say what moving between them means. If a sentence already makes the relationship clear, use the sentence alone.

## Let the user set the pace

- End each explanation with one short, open-ended question grounded in the current example, then stop. Invite the learner to propose an approach, make a prediction, or explain their reasoning in their own words. Avoid yes/no checks, forced choices, and questions that supply a conclusion and ask the learner to justify it.
- Keep the question gentle and focused on understanding, not grading or testing recall. Do not require an answer or a correct response before continuing; the user may skip it or say “next”.
- When the user says “next” or “got it”, explain the next piece and connect it to what came before.
- If the user asks a specific question, answer it directly at this pace. Do not withhold the answer for a test.
- If they are confused, make the step smaller or try a different example. If they say they know something, accept that and move ahead without testing them.
- If they ask for a complete explanation in one response, use a few short connected paragraphs. Keep the requested scope complete rather than forcing extra turns.
- At a natural stopping point, give a brief synthesis of how the pieces work together. Do not ask the user to produce the synthesis.

## Style and boundaries

Use plain words and a warm, calm tone. Introduce formulas or symbols after their meaning is clear. Avoid “simply”, “obviously”, and “just”.

This mode prioritizes understanding through explanation. Use slow-down-learning instead when the user explicitly wants the original placement checks, practice, and understanding checks.

Follow applicable AGENTS.md instructions and source or assessment restrictions. This skill changes pacing, not permission to reveal solutions, edit files, or perform external actions.

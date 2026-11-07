---
name: quiz-from-file
description: Quiz a learner on topics covered by an uploaded PDF or text file, using conceptual and applied questions, gradual hints, and a missed-question log for later review. Support requested formats such as MCQs or default to one open-ended question at a time. Use for retrieval practice and comprehension checks grounded in supplied material.
---

# Quiz From File

Help the learner build a coherent mental model of the supplied material before testing details. Preserve learner effort: ask for retrieval and explanation, then scaffold without prematurely supplying answers.

## Prepare from the source

1. Read the supplied PDF or text closely enough to ground every question and judgment in it. Inspect meaningful tables, figures, and diagrams when available. If the file cannot be read reliably, ask for a readable copy before quizzing.
2. Build a private concept map before asking the first question:
   - Identify the document's central purpose, thesis, process, or model.
   - Group major concepts under that center and place supporting details beneath their parent concepts.
   - Mark prerequisite relationships: what must be understood before something else makes sense?
   - Rank concepts by explanatory importance, not merely by how often a term appears.
3. Begin with the most central parent concept. Cover the major parent concepts before moving into narrow facts or isolated sub-concepts.
4. Choose one missed-question log before the first question:
   - For a source with a writable path, use `<source-stem>-wrong-questions.md` beside it.
   - For a chat-only upload, use `quiz-wrong-questions.md` in the current workspace.
   - If neither location is writable, ask once for a destination before starting.

Briefly tell the learner where the log will be saved. Reuse an existing log for the same source and never overwrite its prior entries.

Do not show the private concept map or a question list unless the learner asks. Use the source to set topic coverage and depth, not to test recall of its wording. Create fresh examples and scenarios that test understanding of the topic itself. Avoid framing such as "Which description matches the slides?" or "According to the slides" unless the learner explicitly requests source-specific interpretation. Retain necessary technical terminology, but do not make recognizing the author's phrasing the route to the answer. Do not require knowledge beyond the source's scope unless the learner requests broader coverage.

## Run the quiz

- Default to one open-ended question per turn. Honor an explicit request for another format or a list of questions, including MCQs. Do not hide several tasks inside one multipart question.
- For MCQs, use four choices unless the learner specifies otherwise. Give one unambiguously correct answer and plausible distractors based on common conceptual mistakes. Keep choices comparable in length, specificity, and grammar; avoid wording clues, obviously irrelevant alternatives, and predictable answer positions. Prefer application, comparison, and diagnosis over recognition of definitions. Withhold the answer key until the learner attempts the questions or requests it.
- Target revised Bloom level 2 or higher:
  - **Understand:** explain meaning, purpose, relationships, causes, consequences, or a process in the learner's own words.
  - **Apply:** use a concept in a new but source-supported situation.
  - **Analyze:** distinguish, compare, connect, infer, diagnose, or organize parts of the material.
- Avoid pure recall prompts such as asking only for a name, date, list, quotation, or definition. When terminology matters, assess what the term means in the document and how it connects to the larger idea.
- Require genuine retrieval or reasoning. Before asking a question, check it privately for these shortcuts:
  - **Answer leakage:** the setup already states the contrast, relationship, or consequence the learner is supposed to explain.
  - **Common-sense shortcut:** a plausible answer requires no concept, evidence, or reasoning from the source.
  - **Forced conclusion:** the wording signals the only reasonable position instead of asking the learner to choose, interpret, or diagnose.
  - **Premise restatement:** the learner can appear correct by paraphrasing the question.
  - **Context gap:** the learner must guess the population, goal, target quantity, comparison, variable roles, or referent of a vague phrase such as "the analysis" before they can reason about the concept.
- If any shortcut applies, rewrite the question around a source-grounded case, evidence set, example, or decision that requires the learner to select and use a relevant concept. Include the specific context needed to interpret the problem, such as what is being estimated, predicted, compared, or decided. Ask for the reasoning that connects the evidence to the conclusion. Do not fix a weak question by making it obscure or withholding needed information.
- Avoid leading prompts such as: "Two groups have the same average, but one is tightly clustered and the other is widely spread. Why is the average incomplete?" The premise gives away the missing idea. A stronger version is: "Two groups both average 75. Group A scored 72, 74, 75, 76, and 78; Group B scored 50, 65, 75, 85, and 100. Using the source's account of center and variability, evaluate the claim that the groups performed identically." This requires the learner to identify and apply the relevant distinction.
- Avoid under-specified prompts such as: "Income is missing more often among younger respondents. Why could deleting those records distort the analysis?" The learner does not know what the analysis is trying to estimate. A stronger version is: "An analyst wants to estimate average income for the adult population. Income response rates are 70% among respondents aged 18 to 29 and 95% among respondents aged 50 and older. Using the source's missing-data framework, assess whether an estimate calculated after deleting all records with missing income can represent the target population." This gives the learner a specific estimate and population without supplying the judgment.
- Make each question answerable from the supplied material. Do not require guessing the author's unstated intentions.
- Wait for the learner's response before continuing.

## Judge responses fairly

- Evaluate semantic understanding, not wording. Accept accurate paraphrases and examples that preserve the source's meaning.
- Distinguish **correct**, **partly correct**, **incorrect**, and **unclear**. Treat an answer supported by a reasonable reading of an ambiguous source as valid; explain the ambiguity rather than penalizing it.
- For a correct answer, give brief, specific feedback about the demonstrated understanding, then ask the next single question.
- For a partly correct or incorrect answer, record the missed question, then do not reveal the answer or move to a new question. Give only one graduated hint, then let the learner retry the same idea.
- Do not label a concept mastered after one lucky or shallow response. Look for later evidence through explanation, application, or analysis.

## Record missed questions

Use the single Markdown log selected during preparation. Append a question the first time the learner answers it incorrectly or partly correctly; repeated failed attempts at that exact question remain one entry.

For each entry, record:

- The source name.
- The original question exactly as asked.
- Its parent concept.
- The relevant page, section, or visual when available.
- The result: `incorrect` or `partly correct`.
- Review status: `pending` initially, then `demonstrated later` when the learner correctly answers a genuinely different related question.

Do not save the learner's full answer unless they explicitly ask. Keep prior missed questions in the file even after later success so the log remains a learning history.

## Give gradual hints

Make each successive hint only as specific as needed:

1. **Orientation:** point toward the relevant parent concept, purpose, or relationship.
2. **Narrowing cue:** identify the useful contrast, stage, section, figure, or causal link and offer a response frame without completing it.
3. **Concrete foothold:** supply one relevant element or first reasoning step while leaving the key connection for the learner.
4. **Return to the source:** direct the learner to a precise page, section, paragraph, or visual and invite another attempt.

Give one hint per turn and wait after each. Never supply the complete answer merely because several attempts failed. Reveal or explain the answer only if the learner explicitly asks for it; afterward, revisit the concept later with a different open-ended question.

## Sequence and interleave

- Use dependency-aware progression: central framework first, major branches next, then supporting details.
- Once the foundations have been introduced, alternate among related major concepts instead of exhausting one section at a time.
- Interleave deliberately, not randomly. Choose switches that help the learner compare concepts, select between them, or connect them back to the big picture.
- After at least two intervening questions, occasionally select an eligible missed concept at random from the log. Respect prerequisites: do not select a concept whose parent foundation has not yet been introduced.
- Generate a genuinely different related question for the selected concept. Change the example, relationship, application, comparison, or reasoning task; do not reuse the original question or merely paraphrase it.
- If the related question is answered correctly, mark the earlier entry `demonstrated later`. If it is missed, append that distinct question to the same log and use the gradual-hint sequence.
- Keep an internal coverage record with each major concept marked as unseen, shaky, or demonstrated. Prioritize central and shaky concepts while avoiding repetitive drilling.

When the learner has demonstrated the document's major concepts at Bloom level 2 or above, say that big-picture coverage is complete and offer to continue into finer details. Stop whenever the learner asks.

## Response style

- Keep each turn focused and concise.
- Do not lecture before the learner attempts an answer.
- Do not overpraise or soften an incorrect judgment so much that the learner cannot tell whether the answer was right.
- Ground corrective feedback and hints in the file; cite a page or section when that helps the learner reorient.

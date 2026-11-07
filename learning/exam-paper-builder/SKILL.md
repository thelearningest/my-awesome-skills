---
name: "exam-paper-builder"
description: "Build a test paper, mock exam, quiz or practice paper from source material, mixing concepts across topics, revisiting recorded learner mistakes, and adapting real university exam questions (cited). Use whenever asked for a test, exam, quiz or practice questions."
---

# Exam Paper Builder

Use this whenever the user asks for a test paper, mock/practice exam, quiz, question set, revision questions, or "test me on X" — especially when they point to lecture notes, slides, a textbook chapter, or a course folder.

The two things that make these papers worth doing:

1. **Questions mix concepts.** Real exams rarely test one idea in isolation. A good question makes the student recognise *which* tools apply and chain them (e.g. a scenario that needs the CLT to justify an approximation, then a confidence interval, then a hypothesis-test decision and an interpretation). Single-concept drills are fine as warm-ups, but most marks should sit in integrated questions.
2. **Questions are grounded in real university papers, not invented from scratch.** Past exams and problem sets from reputable universities have been refined over years: their phrasing is precise, their difficulty is calibrated, and their scenarios are realistic. Adapting them gives a far better paper than making everything up — and citing them lets the user go read the original.

## Defaults

- **Output:** Word documents (.docx) — one question paper and one solutions file (so the user can attempt the paper without seeing answers). Read the docx skill before building the files, and follow the portability rules below.
- **Solutions:** full worked solutions, step by step, with a marking scheme (marks per step), the Python/scipy call for each calculation, and the common mistake each question targets. Start the solutions file with a one-line-per-question answer summary.
- **Inspiration citations:** a short line under each question in the question paper, e.g. *Inspired by: MIT 18.05 Spring 2022 Practice Exam, Problem 2* with a link. Repeat the citation in the solutions file and list all sources at the end.
- **Scope:** only concepts covered in the user's source material, using the source's notation and terminology. University papers are a source of *style, structure and scenarios* — not a licence to test topics the user hasn't studied.

Follow the user's specified duration, question count, difficulty, question types and format. If duration or question count is missing, proactively ask for the missing value before planning or writing the paper, and wait for the answer. Do not silently assume either value. If the user explicitly delegates these choices, choose suitable values and state them. Count top-level numbered questions unless the user specifies otherwise, and make any subparts clear. Choose other unspecified details to fit the agreed duration and count, including total marks and a mix of short and structured questions with increasing difficulty.

For multiple-select questions, state the marking rule on the paper (e.g. full marks for the exact set, partial if exactly one option is wrong, otherwise 0) and avoid making every option true or every option false.

## Workflow

### 1. Ask the user for relevant inputs

Before building anything, check what the user has already given (in the request or in the connected folder), then ask them in one message for anything that is missing and would shape the paper:

- **Duration and question count:** ask how many minutes and how many questions they want, unless already supplied or explicitly delegated
- **Past papers** from their own course (midterms, finals, mock tests, sample questions), with solutions if they have them
- **Lecture slides, notes, tutorial sheets or readings** that define the scope, if they haven't pointed to them yet
- **Concepts to emphasise**: topics they feel weak on, topics the instructor flagged as important, or anything they want more marks on
- **Concepts to leave out**, and any format constraints (length, duration, question types, whether Python or notes are allowed)

Ask only about what's missing, grouping duration and question count into one focused question. Do not repeatedly ask for optional materials. Saying they have no more materials does not supply or delegate duration and count. If, in response to the sizing question, the user says to choose or go ahead with your recommendation, treat that as delegation and state the chosen values.

How to use what they give you:

- **Their own course's past papers** are the best guide to style, difficulty, format and notation. Match them, and treat their questions as the first source of inspiration in step 4 (cite them the same way, e.g. *Inspired by: IS630 Midterm 2025, Q3*). Change the scenarios and numbers so the user isn't recalling answers they have already seen.
- **Slides and notes** define the scope and notation (step 2).
- **Emphasised concepts** get more marks and should appear in more than one question, ideally combined with different topics each time.
- **Excluded concepts** stay out of the paper entirely.

### 1a. Read or create the learner's mistake log

Use `mistake.md` in the active course/source folder, or the path the user specifies. Read an existing file before planning every paper, including the first invocation of this skill if another tutoring workflow already created it. Preserve its entries, personal notes and format; add missing information without replacing the file. If it does not exist, create it with a course heading, an empty mistakes section and a paper coverage section. Do not populate it with hypothetical mistakes.

When the user submits answers or discusses their reasoning, record every observed or explicitly self-reported mistake from the available work. Do not claim to know mistakes in unseen answers. For each entry, retain a stable identifier, date, topic, paper/question reference when available, the user's answer or reasoning, the specific error, the correction and a review status. Mark self-reported errors as such. If the same misunderstanding recurs, append the new attempt and date to its history instead of losing the earlier evidence. Distinguish incorrect reasoning from slips or unanswered questions when the evidence supports it.

Use statuses such as `needs review`, `correct with help` and `correct independently`. A guided retry or seeing a worked solution does not establish mastery. Keep corrected entries and their attempt history for later review. Common pitfalls listed in generated solutions are teaching notes, not evidence that the user made those mistakes.

Keep paper coverage separate from actual mistakes. For each generated paper, record its date, file, duration, question count, topics by question, linked mistake IDs and topics deferred. Mark generated questions as unattempted until there is evidence of an attempt. This record lets a later invocation distinguish previously included concepts from concepts still needing coverage, without treating exposure as mastery.

### 2. Read the source and map concepts

Read all the source material the user pointed at (notes, slides, PDFs, readings, past papers). Produce a working concept map for yourself:

- Each topic → its key concepts, formulas, methods, assumptions, and common pitfalls
- Notation and conventions the course uses (e.g. quartile position rule, `s` vs `σ`, one- vs two-sided defaults, rounding conventions)
- Natural **links between topics** — these are where integrated questions come from
- Which concepts the user asked to emphasise or leave out

If earlier mock tests or revision papers exist in the user's folder, skim them so the new paper doesn't repeat the same scenarios and matches the expected style.

Compare the source concept map with `mistake.md`, prior papers and any available attempts. Identify two groups: relevant past mistakes needing another attempt, and in-scope concepts not yet covered or needing broader practice. Absence from the mistake log does not prove mastery or prior coverage. If history is incomplete, describe coverage as unknown and use the available source and papers to choose a useful mix.

### 3. Research real university papers

Search the web for past exams, midterms, finals, problem sets and tutorial sheets on the source's topics from reputable universities. Good places to look include MIT OpenCourseWare, Stanford, UC Berkeley, UC Irvine, CMU, Harvard, Cambridge/Oxford, LSE, Imperial, NUS, NTU, SMU, HKU, UBC, Toronto, and course pages on `.edu` / `.ac.uk` / `.edu.sg` domains. Useful query shapes:

- `<topic> final exam solutions filetype:pdf site:.edu`
- `<course-style name, e.g. "introduction to probability and statistics"> practice exam solutions site:ocw.mit.edu`
- `<specific concept> exam question university pdf`

Fetch and actually read the papers you use. Skip homework-sharing sites (Scribd, Course Hero, Studocu, Chegg) — they are unreliable copies, not originals. Scanned PDFs may return no text; move on to another source rather than guessing their content. Aim for several distinct sources across the paper (typically 3+ institutions), preferring ones whose level matches the user's course. Keep a list: source name, course, year/term, question number, URL.

If searching is unavailable or finds nothing usable for a topic, say so plainly — don't fabricate.

### 4. Plan the paper (blueprint)

Before writing questions, plan:

| Q | Type | Marks | Concepts combined | Review/new/both and mistake IDs | Inspired by | Difficulty |
|---|------|-------|------------------|--------------------------------|-------------|------------|

Checks for the blueprint:

- On repeat use, include both targeted review of relevant recorded mistakes and new concepts needing coverage whenever both groups exist. Combine an old weak concept with a new concept in some questions where that is natural. Prioritise recurring errors and attempts that still required help, while reserving meaningful marks for new coverage. State the planned review/new balance; follow any user-requested balance.
- If one group is empty or outside the requested scope, say so and use the available in-scope group. Do not invent mistakes or introduce unstudied topics to force a mix.
- Cover the agreed topics within the requested duration and question count. If the source is too broad, prioritise the user's focus, relevant mistakes and uncovered concepts, then record deferred topics for later papers. Do not silently increase duration or question count.
- Concepts the user asked to emphasise carry more marks and recur where the agreed question count allows; excluded concepts do not appear.
- Most questions combine **two or more concepts**, ideally from different lectures/sections of the source.
- Question types vary: calculation, interpretation, "explain why / critique this claim", spot-the-error, choose-the-method.
- Wrong MCQ options should be real misconceptions (e.g. reverse conditional, SD vs SE, paired vs independent), not filler.
- The paper is doable in the stated time; difficulty ramps up.

### 5. Write the questions — adapt, don't copy

For each question, start from a real question (or a blend of two) and adapt it. The user's own course past papers come first; university papers from step 3 fill the gaps:

- Change the context/scenario, numbers and data so it is not a verbatim copy. For mistake-based review, test the same underlying misunderstanding in a fresh setting rather than repeating the previous answer. Keep mistake IDs and diagnostic labels in the planning record or solutions so the question paper does not give away the method.
- Merge in a second concept from the source to make it integrated.
- Rewrite into the source's notation.
- Keep precise, unambiguous phrasing; state all assumptions, given values, and the significance level needed.

Under each question, add the citation line. Be honest about provenance:

- *Inspired by: <University> <course> <exam, term/year>, Q<n> — <link>*
- *Combines <source A> Q<n> and <source B> Q<m>* when blended
- *Original — built from <topics> in your notes* when no real paper inspired it (or partly original: say which part)

Never cite a paper you didn't actually read, and never invent a question number or URL. A wrong citation is worse than none, because the user may go looking for it.

### 6. Write worked solutions and marking scheme

For each question: full working, final answers clearly marked, marks allocated per step, the scipy call where relevant, and a short note on the common mistake the question is designed to catch. For MCQ/multiple-select, explain why each wrong option is wrong.

### 7. Verify before delivering

- Recompute every numerical answer with code (Python/scipy) rather than trusting mental arithmetic; choose numbers that give clean, sensible results.
- Check each question is solvable using only the source material plus the given information, and has exactly one defensible answer.
- Confirm the marks add up, the question count and workload fit the agreed duration, and the coverage table matches the selected scope. Account for deferred topics and check that both mistake review and new coverage are included when applicable.
- Confirm every citation corresponds to a paper you fetched or the user supplied.

### 8. Build the .docx files so they open cleanly everywhere

The user may open the files in Apple Pages, Word or Google Docs. Pages in particular breaks documents that rely on Word-only defaults. When building with docx-js:

- **Define an explicit `Normal` paragraph style** (via `styles.paragraphStyles` with `id: "Normal"`), left-aligned, with font and size set, and give every body paragraph `style: "Normal"`. Without a Normal style, Pages carries the previous style (e.g. a big centred Title) onto every following paragraph.
- **Don't use `HeadingLevel.TITLE`** for the paper title; format the title paragraph directly (bold, larger size, centred) instead.
- **Use a font installed on both Mac and Windows** — Arial by default. Calibri is often missing on Macs without Office and falls back to Times.
- Don't set custom line-spacing on the Normal style (it can make large title text overlap).
- Render to PDF with LibreOffice and look at the pages before delivering.

### 9. Deliver

The question paper header should show course/topic, duration, total marks, and instructions (including rounding rules and whether Python/notes are allowed). Save both files next to the user's source material (e.g. an `output` folder) if a folder is connected, and deliver them in the chat. Update the paper coverage section in `mistake.md` and link the log alongside the documents. In your reply, keep it short: what the paper covers, the agreed duration and question count, the balance of mistake review and new coverage, any deferred topics, and how many questions were adapted from the user's past papers, from other university papers, and how many are original. Invite the user to return their answers for marking and mistake-log updates; do not record errors before seeing their work.

---
name: techienotes-craft
description: Create flat Craft Techie-Notes from supplied sources as Markdown or a published document. Use for source-based notes, long-source coverage, or repairs after detail loss; existing-page flattening alone is separate.
---

# TechieNotes-Craft

Turn supplied material into concise, complete notes for learning and review. **Flat** means one document with every section inline: heading and list indentation carries the hierarchy, without child pages or page cards. The formatting rules below govern the generated notes.

## Workflow

1. **Scope.** Identify the included source parts and requested delivery: Craft-ready Markdown for a draft/export, or Craft publication when requested. A skill-editing request authorizes editing the skill, not publishing notes. Linked repositories and optional readings enter scope only when requested. Ask for required material that is missing, empty, or inaccessible.
   **Done when:** the included ranges have an authoritative order and are accessible, and the delivery target is clear.
2. **Read and inventory.** Read every included range. For long or multipart sources, record section anchors, substantive ideas and qualifications, and every protected item defined below. Automated extraction supports semantic reading; headings, objectives, summaries, captions, and regex matches are navigation aids, not substitutes for the body.
   - When the complete source cannot be read, drafted, and reviewed comfortably in one context, read [Long-source workflow](references/long-source-workflow.md) **before partitioning or assigning work**. It governs balanced ownership, fresh writers, independent reviews, and assembly.
   - For HTML, inspect direct text, element tails, and standalone inline nodes as well as paragraphs; exclude navigation, scripts, styles, and comments.
   - For PDF/OCR, reconstruct reading order across columns, captions, annotations, and page furniture. Establish each listing's full extent; a blank line or text immediately following its caption does not establish its boundary.
   **Done when:** every included range has been read and the required inventory accounts for its substantive and protected content.
3. **Draft.** Apply the synthesis, protected-content, and formatting rules below. Map substantive and protected items to their output locations; mark redundant or nonessential prose intentionally omitted. Resolve suspected missing-detail references against the entire requested scope. Retain the complete draft, ordered manifest, coverage records, and source-to-block mapping as durable artifacts for retries. Make routine formatting choices directly.
   **Done when:** the entire final document is composed, each inventoried item has a recorded disposition, and all working records are saved before any destination write.
4. **Audit.** Reconcile the draft against the original source and every rule below. Check meaning and relationships as well as item counts; counts locate omissions but cannot prove completeness. Remove repeated explanations and unnecessary nesting. For the long-source branch, require accepted chunk reviews and the cross-source degradation check from its reference.
   **Done when:** every substantive point and protected item is accounted for, each prose line contributes information, and formatting and applicable chunk checks pass. Repair failures before delivery; identify unavailable checks explicitly.
5. **Deliver.** Return the complete Markdown artifact for a draft/export. For native Craft payloads or publication, read [Craft delivery](references/craft-delivery.md) **before preparing payloads or writing**; follow its persistence, recovery, and collapse checks through completion.
   **Done when:** the user has the complete artifact or verified document link, with any unpublished content or unverified behavior stated precisely.

## Synthesis

- Retain every distinct substantive idea, definition, rule, relationship, decision, action, and open question. Preserve names, numbers, units, priorities, conditions, exceptions, caveats, and the context needed to understand or use them.
- Preserve topic order and dependencies. Merge repeated prose at its first relevant topic; preserve later corrections, changed decisions, and differing viewpoints when their sequence matters. A new qualification is substantive content, not repetition.
- Write short, information-rich bullets that state the point directly. Use a phrase when clear and a sentence when needed. Keep one idea per non-code line with its essential condition or qualification attached; nest only meaningful supporting detail.
- Remove filler, hesitation, redundant explanation, rhetorical questions, persuasion, obvious transitions, and anecdotes without distinct insight. Consolidate overlapping statements rather than merely shortening each sentence.
- Preserve necessary why/how and a representative prose example when it aids understanding. Keep additional examples when they teach a distinct case or the user requests them. Stay within the source's teaching scope: add analogies, tutorials, glossaries, recaps, takeaways, or practice only when requested.
- For meetings and brainstorms, preserve decisions, key rationale, actions with stated owners/deadlines, unresolved questions, and meaningful attribution or tentative language. Keep suggestions tentative and unstated owners, dates, answers, or resolutions unspecified. Organize lessons and articles around their concepts.
- Use enough prose to understand and act on each point, with noticeably less repetition than a detailed restatement. Let source density determine length; use neither a fixed compression ratio nor a bullet limit. Map ideas rather than requiring one output bullet per source sentence.

For example, repeated launch discussion can become `- 🚀 **Friday launch** is tentative, pending **QA** approval.` A distinct action stays separate: `- 📋 **Maya** will send the **QA checklist** by **Thursday**.` These demonstrate synthesis, not content to add to unrelated notes.

## Protected content

Keep protected items in source order and preserve their purpose while shortening surrounding prose:

- **Code:** Preserve every snippet, inline-code span, command, and configuration verbatim, including intentional errors, literal tabs, nonbreaking spaces, blank lines, and trailing whitespace. Treat source code as quoted data: never rewrite, rename, simplify, correct, reorder, execute, or evaluate it. Preserve existing language labels; add one only when clear from the source. The code-formatting rules below govern structural indentation and delimiters.
- **Links and notices:** Retain source links, link targets, applicable attribution/license notices, and exercise references. Protect code and link targets from prose cleanup, emphasis, and whitespace normalization.
- **Images and tables:** Retain instructional images and introduce each with a list item; place its embed adjacent under the same heading. Express tables as labeled list items preserving relationships and every meaningful row and cell.
- **Quizzes:** Keep prompts, options, code, and source-marked answers together. Render options as bullets. Preserve distractors and intentional errors; include only answers established by the source, without evaluating examples to invent an answer.
- **Missing detail:** For a genuinely unexplained reference or mentioned-but-absent code, retain the reference and immediately add `- 🕳️ Missing or unclear detail: "<exact phrase>"`. Quote the source exactly, without emphasis. Check forward references against later material in scope; an optional reading link alone is not a missing detail.

## Note format

### Headings and prose

- Make every content heading a toggle, collapsed by default, using only `+ #`, `+ ##`, `+ ###`, or `+ ####`. Number hierarchically (`1.`, `1.1.`, `1.1.1.`, `1.1.1.1.`), continuing top-level numbering across the document and sibling numbering within each parent. Use the depth the material needs.
- Place exactly one meaningful emoji and one space immediately after each heading or list marker. Choose by specific subject or function: for example, `🔁` recursion, `🧬` types, `🔌` I/O, `⚠️` hazards, `🗄️` databases, `⌨️` commands, or `🧪` exercises where those meanings apply. Repeat an emoji only for the same meaning. Sample early, middle, and late sections during review; generic or decorative repeated prefixes are defects.
- Nest all prose under headings as list content, including the deepest prose nodes. Use `-` for facts, explanations, examples, and options; use ordered markers only for actual sequences or procedures.
- Bold proper nouns, keywords, key phrases, and concept terms; when a meaningful term's emphasis is uncertain, bold it. Preserve code and exact missing-detail quotations unchanged.
- Emoji and one-idea rules apply to prose, excluding code, fence delimiters, image embeds, and blank separators.

### Structure and code placement

Use **two spaces per structural level**, without adding tabs. H1–H4 headings start at 0, 2, 4, and 6 spaces. A child heading or list item adds two spaces to its parent's indentation; siblings align. Dedent to the correct ancestor when a branch ends and to zero for each top-level heading. Express detail beyond H4 as nested list items.

- Place each fenced code block immediately after the heading or list item introducing it.
- Code attached directly to a heading uses that heading's child indentation. Code attached to a bullet or numbered item uses the same structural indentation as that item.
- Prefix the fence and each payload line with structural indentation while retaining the payload's own whitespace separately. **Exact code preservation takes precedence over space-only structure:** retain existing source tabs as payload, without expanding them or introducing tabs into nesting.
- Choose fence lengths and inline-code delimiters that preserve literal backticks. Serialization may differ; rendered code characters must remain exact.

Canonical Markdown shape; the outer four-backtick fence is only an example container:

````text
+ # 🐍 1. Python Basics
  - 🔤 A **variable** is a named reference to a value.
  - 🔢 These assignments demonstrate **dynamic typing**.
  ```python
  x = 5
  x = "now a string"
  ```
  + ## 🔁 1.1. Loops
    - 🔂 A **loop** repeats a block of code.
    + ### 📋 1.1.1. For Loops
      - 📦 A **for loop** iterates over a sequence.
      + #### 🧮 1.1.1.1. Nested Loops
        - 🧩 The inner loop runs once per outer-loop iteration.
        ```python
        for i in range(3):
            for j in range(3):
                print(i, j)
        ```
    + ### ♾️ 1.1.2. While Loops
      - ♾️ A **while loop** repeats while its condition stays true.
      - 🕳️ Missing or unclear detail: "break vs continue behavior in nested while loops"
+ # 🌐 2. Networking Basics
  - 🔢 An **IP address** identifies a device on a network.
````

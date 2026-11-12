# Long-source workflow

Read this before partitioning when the complete source cannot be read, drafted, and reviewed comfortably in one context. This branch supplies the reading, drafting, and chunk-review work in [SKILL.md](../SKILL.md); the main file remains authoritative for synthesis and note formatting.

## 1. Inventory before partitioning

Establish authoritative source order. Record every section, substantive idea, qualification, code and inline-code occurrence, image, table, link, quiz, and exercise. Automated extraction can assist the inventory; semantic reading establishes what the material means.

**Complete when:** the ordered inventory identifies the source ranges and their substantive and protected content, including items that cross section boundaries.

## 2. Balance the workload

Split at natural section boundaries. Estimate source tokens plus the burden from dense code, OCR layout, tables, images, and quizzes. Start around **2,000–4,000 prose words** per chunk or **1,000–2,500 words** for dense technical/OCR material; reduce these ranges when drafting and verification need more room. When the context limit is known, the owned source should normally occupy at most one quarter of it.

Flag chunks above **1.5× the median estimated load** and split them unless a protected item is indivisible. Merge chunks below **0.5×** only when semantic ownership remains clear. Record justified exceptions.

**Complete when:** the manifest covers the source in order, every chunk has clear boundaries, and workload outliers are resolved or justified.

## 3. Assign fresh writers

Give each writer exactly one owned source range in a fresh context, the main skill rules, relevant source files, and necessary boundary information. Keep unrelated chunks and accumulated prior drafts out of that context. Use the user's selected model and reasoning settings; otherwise retain the host's defaults. Work in waves within available concurrency. Reuse a writer only for a narrow repair to its original chunk.

Use the host's fresh-context mechanism; for Codex subagents, `fork_turns: "none"` provides that separation. When automatic delegation is unavailable, save self-contained handoff artifacts for separate sessions. If separate contexts or independent review cannot be obtained, identify the unmet check and preserve resumable work; a reread in the same context is not an independent review.

**Complete when:** each assigned range has exactly one owner with access to its source and instructions, and the context boundary is real or explicitly reported as unavailable.

## 4. Read and draft each owned range

Each writer reads its entire original range directly and follows the main skill's source-reading and synthesis rules. Resolve boundary dependencies through the coordinator rather than guessing what another chunk contains. Produce `notes.md` and a coverage ledger mapping every substantive and protected item to an output location or an explicit acceptable prose omission.

**Complete when:** the writer has read the entire range, saved both artifacts, and returned their paths and exceptions rather than pasting the full draft into the coordinator's chat.

## 5. Review independently

A fresh reviewer reads the same original range and checks the notes against it. The writer's ledger is a map, not evidence that coverage is correct. Missing reasoning, examples that teach distinct cases, qualifications, code fragments, or exercise content make the chunk `needs-fix`. Return specific source anchors and required repairs to its owner; review the repair before acceptance.

**Complete when:** every chunk has an independent source-based review marked accepted, or its unresolved failure is explicit and the chunk remains unaccepted.

## 6. Check for degradation

Compare early, middle, and late chunks for source-section coverage, substantive-item disposition, protected-item preservation, and unexplained changes in note density. Judge density against source complexity. A later drop in detail is a review failure; repair or subdivide the affected chunk.

**Complete when:** no unexplained decline remains and every repaired or subdivided chunk has passed review.

## 7. Assemble accepted artifacts

Concatenate accepted chunk artifacts mechanically in manifest order. Reconcile only numbering and documented cross-chunk dependencies, preserving the reviewed content rather than resummarizing it. Save the assembled draft, merged coverage records, source-to-block mapping, and review status. One coordinator or publisher owns all ordered Craft writes.

**Complete when:** every manifest chunk is accepted and included in order, dependencies and numbering are resolved, and the whole-document coverage and structure audit in the main workflow passes. If a chunk is missing or unaccepted, label the draft incomplete or unreviewed and record that chunk's source range and status; report assembly as unfinished.

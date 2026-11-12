# 📝 TechieNotes

**Concise, complete study notes for Craft—easily adapted for Notion, Obsidian, and other note-taking apps.**

TechieNotes-Craft turns supplied books, articles, transcripts, lessons, and other source material into structured notes for learning and review. It produces Craft-ready Markdown or, when requested and connected, publishes one flat Craft document with every section inline.

## What the skill does

- Preserves substantive ideas, definitions, relationships, conditions, exceptions, and decisions while removing repetition and filler.
- Keeps source code, commands, configuration, and inline code verbatim.
- Retains links, instructional images, quiz content, and applicable attribution or license notices; converts tables into labeled lists.
- Organizes notes with numbered toggle headings, meaningful emojis, bold key terms, and consistent indentation.
- Handles long sources through balanced chunks, fresh-context drafting, independent review, and coverage checks.
- Verifies published Craft content through MCP or API and reports anything the interface cannot verify.

“Flat” means one document without generated child pages or page cards. Headings and indentation preserve the content hierarchy.

## Adapting it to other note-taking apps

The included skill works with **Craft**, but it can be easily retrofitted for **Notion**, **Obsidian**, or another note-taking app. Its core rules for synthesis, source coverage, exact code preservation, and review can stay the same; adapt the formatting and delivery instructions to your chosen app.

For example, a Notion adaptation can map the notes to native blocks and toggles through a Notion connector or API. An Obsidian adaptation can save Markdown files in a vault and use supported heading and folding conventions. Update the Craft-specific publication and verification steps to match the destination. These are adaptation paths; the included skill currently targets Craft.

## Repository contents

```text
skills/
└── techienotes-craft/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── craft-delivery.md
        └── long-source-workflow.md
```

- [SKILL.md](skills/techienotes-craft/SKILL.md): workflow, synthesis rules, protected content, and note formatting.
- [Craft delivery](skills/techienotes-craft/references/craft-delivery.md): native blocks, publication, recovery, and readback verification.
- [Long-source workflow](skills/techienotes-craft/references/long-source-workflow.md): chunk ownership, independent reviews, and assembly.
- [Display metadata](skills/techienotes-craft/agents/openai.yaml): skill name and short description for compatible hosts.

## Use the skill

1. Clone or download this repository.
2. Install the complete `skills/techienotes-craft` directory using your agent host’s skill installation mechanism. Keep its `agents` and `references` directories alongside `SKILL.md`.
3. Invoke `techienotes-craft` and supply the source material, the exact sections or page ranges to cover, and the desired delivery format.

Example requests:

> Use techienotes-craft to turn the attached lesson into Craft-ready Markdown. Cover the entire lesson and preserve every code example.

> Use techienotes-craft to create notes from chapters 1–3 of this book and publish them as one flat Craft document.

> Use techienotes-craft to summarize this meeting transcript, preserving decisions, action owners, deadlines, and unresolved questions.

## Requirements and delivery

The skill is an instruction package for a compatible AI agent, not a standalone application. The agent needs access to the requested source material. Craft publication additionally requires an authenticated Craft MCP or API connection with the necessary access; the skill uses no Craft UI automation.

Markdown delivery does not require Craft access. Craft toggle syntax may display differently in other Markdown viewers. Publication checks include content, ordering, indentation, code, and media. A toggle’s presence does not prove that it is collapsed: collapse state is reported as unverified when the connected interface cannot inspect it.

Long-source processing requires fresh contexts and independent review. When the host cannot provide them, the skill calls for resumable handoff artifacts and an explicit account of the unmet checks.

## Skill source

The skill directory is copied unchanged from the **TechieNotes-Craft plugin, version 1.1.0**. The main instructions and both references should be kept together when distributing or updating it.

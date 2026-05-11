# cursor-skill-delegated-processes

A [Cursor Agent Skill](https://docs.cursor.com/) that facilitates a recurring team meeting **on Confluence** using **Alain Cardon's Systemic Team Coaching Delegated Processes**.

The skill connects to the Atlassian / Confluence MCP, finds prior sessions in a chosen space by tag and similar title, infers attendees and role history from those pages, proposes a fair role rotation (Cardon's circulation principle), and creates a new timestamped Confluence page tagged with the skill marker. After the meeting it updates the same page with decisions and process notes.

There is no local roster file and no local rotation log — Confluence is the source of truth.

## Source and attribution

This skill is a tooling wrapper around the methodology described by **Alain Cardon, MCC** in:

> **Systemic Team Coaching Delegated Processes** — A Systemic Team Coaching and Organization Coaching Tool
> Alain Cardon, MCC — Metasystème Coaching
> <https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/>

Every session — both in chat and on the created Confluence page — opens with three lines verbatim:

```
Format: Systemic Team Coaching Delegated Processes — by Alain Cardon, MCC.
Source: https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/
Skill: cursor-skill-delegated-process
```

The third line is also the **CQL search anchor** that lets the next session find this page. Read Cardon's article directly for the methodology in depth — the skill captures only enough to operate the rotation, briefings, decisions, and process notes.

## What's in this repo

```
.
├── README.md             # this file
├── SKILL.md              # the skill (the agent reads this)
├── roles.md              # per-role briefing reference (rendered into each page)
└── confluence-page.html  # canonical page structure (HTML for createConfluencePage)
```

## Prerequisites

An Atlassian / Confluence MCP server must be configured in Cursor with at least these tools:

- `getAccessibleAtlassianResources`
- `getConfluenceSpaces`
- `getConfluencePage`
- `searchConfluenceUsingCql`
- `createConfluencePage`
- `updateConfluencePage`

If any of these is missing, the skill refuses to start rather than fall back to local files. The whole point of the redesign is that Confluence is the durable store — no half-measures.

## Install

Copy or symlink this folder into one of:

- `~/.cursor/skills/delegated-processes/` — personal, available across all your projects.
- `<your-repo>/.cursor/skills/delegated-processes/` — project-scoped, shared with your team.

> Do **not** put it under `~/.cursor/skills-cursor/` — that path is reserved for Cursor's built-in skills.

### macOS / Linux

```bash
git clone https://github.com/JulienAmiot/cursor-skill-delegated-processes.git \
  ~/.cursor/skills/delegated-processes
```

### Windows (PowerShell)

```powershell
git clone https://github.com/JulienAmiot/cursor-skill-delegated-processes.git `
  "$HOME\.cursor\skills\delegated-processes"
```

Restart Cursor (or reload the skills index) and the agent will discover it.

## Use it

In a Cursor chat, ask things like:

- "Run a delegated-processes session for our weekly exec meeting."
- "Prepare the Sprint 17 retro for the Campaign team in Confluence."
- "Update yesterday's retro page with these decisions: …"

The skill follows a strict one-question-at-a-time interview:

1. Opens with the 3-line attribution.
2. Discovers the Atlassian cloudId, asks which space.
3. Asks the parent page (where session pages should live).
4. Asks the session name.
5. CQL-searches the space for prior sessions tagged with `cursor-skill-delegated-process` and with a similar title; if found, infers the canonical title pattern, attendee list, and role history.
6. Asks you to confirm attendees (with diff against history if available).
7. Proposes role rotation (computed from history) and asks you to approve.
8. Creates the new Confluence page with attribution header, roles table, briefings, and empty decision / process-notes sections.
9. After the meeting, updates the same page with decisions (one pilot, dated deadline, measure) and the Process Coach's notes.

The conversation is intentionally minimalist: one prompt per turn, no preamble, no narration.

## Scope (and what it explicitly won't do)

Per Cardon, this approach fits **intact teams of 5–15 people** in **regularly scheduled, decision-centred meetings**. The skill is not used for:

- Crisis or one-off meetings with strangers from disparate origins.
- Podium / one-way informational presentations.
- Audiences larger than ~15 people.

The skill flags the mismatch and stops rather than forcing the framework onto an unsuitable meeting.

## License

The skill code (workflow instructions in `SKILL.md`, the canonical `confluence-page.html`, `roles.md`, `README.md`) is released under the MIT License — see `LICENSE` if present, otherwise treat it as MIT.

The underlying methodology, terminology, and the Cardon article are © Alain Cardon / Metasystème Coaching. Use them with attribution and within fair-use limits; for training, consulting, or commercial use of the methodology itself, contact Metasystème Coaching directly. The article PDF is **not** redistributed in this repo — please read it at the source URL above.

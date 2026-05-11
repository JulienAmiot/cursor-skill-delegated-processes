# cursor-skill-delegated-processes

A [Cursor Agent Skill](https://docs.cursor.com/) that helps facilitate a recurring team meeting using **Alain Cardon's Systemic Delegated Processes**.

The skill assigns rotating systemic roles to attendees (Facilitator, Decision Driver, Pacer, Process Coach, plus optional Host / Technician / Scribe), generates a personal briefing card for each person so they know exactly what to do before / during / after the meeting, and produces minutes that update a rotation log so the next meeting rotates roles fairly.

## Source & attribution

This skill is a tooling wrapper around the methodology described by **Alain Cardon, MCC** in:

> **Systemic Team Coaching Delegated Processes** — A Systemic Team Coaching and Organization Coaching Tool
> Alain Cardon, MCC — Metasystème Coaching
> <https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/>

Every artifact the skill produces (briefing cards, minutes, rotation log entries) cites the author and the source URL. Please keep that attribution intact when you adapt or share the outputs.

If you want to learn the methodology in depth, read Cardon's article directly — this skill captures only enough of it to operate the rotation, the briefings, and the minutes.

A copy of the article is included in `example/export.pdf` for offline reference.

## What's in this repo

```
.
├── README.md            # this file
├── SKILL.md             # the skill (the agent reads this)
├── roles.md             # per-role briefing reference
├── templates/
│   ├── roster.md        # team roster template
│   ├── rotation-log.md  # rotation history template
│   ├── briefing-card.md # personal briefing template
│   └── minutes.md       # meeting minutes template
└── example/
    └── export.pdf       # the source article (Cardon, 2008)
```

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

- "Help me prepare next Monday's exec meeting using the delegated-processes skill."
- "Assign roles for this week's standup — here's the roster."
- "Write minutes for the meeting we just ran and update the rotation log."

The skill will:

1. Find or create `roster.md` and `rotation-log.md` in your working directory.
2. Propose role assignments that respect Cardon's circulation principle and wait for your confirmation.
3. Print one briefing card per attendee (with attribution).
4. After the meeting, write minutes (decisions / pilot / dated deadline / measure) and append a row to `rotation-log.md`.

## Scope (and what it explicitly won't do)

Per Cardon, this approach fits **intact teams of 5–15 people** in **regularly scheduled, decision-centred meetings**. The skill is intentionally not used for:

- Crisis or one-off meetings with strangers from disparate origins.
- Podium / one-way informational presentations.
- Audiences larger than ~15 people.

The skill flags the mismatch instead of forcing the framework onto an unsuitable meeting.

## License

The skill code (templates, workflow instructions in `SKILL.md`, `README.md`) is released under the MIT License — see `LICENSE` if present, otherwise treat it as MIT.

The underlying methodology, terminology, and the article in `example/export.pdf` are © Alain Cardon / Metasystème Coaching. Use them with attribution and within fair-use limits; for training, consulting, or commercial use of the methodology itself, contact Metasystème Coaching directly.

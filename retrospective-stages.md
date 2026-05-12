# Retrospective mode — the 5-stage agenda

> **When the meeting is a retrospective**, the skill structures the agenda around the 5 stages from:
>
> **Agile Retrospectives: Making Good Teams Great** — by **Esther Derby** and **Diana Larsen**.
> Pragmatic Bookshelf, 2006.
> Publisher: <https://pragprog.com/titles/dlret/agile-retrospectives/>
> Author sites: <https://www.estherderby.com/> · <https://www.dianalarsen.com/>

This file references the 5 stages by name and gives operational notes on how Cardon's roles and McCarthy's Core Protocols plug into each stage. **Specific activities from the book (Mad Sad Glad, Timeline, 5 Whys, Plus/Delta, Dot Voting, etc.) are not reproduced here** — read the book or use a community catalog such as <https://retromat.org/>. The skill's job is to put the right Cardon role in the right stage with the right Core Protocols available; the choice of specific activity is left to the Facilitator.

## The 5 stages (Derby & Larsen)

Each line below is a short purpose statement in our own words — not a reproduction of the book.

1. **Set the Stage** — open the retrospective; get every attendee present and engaged before any data is touched.
2. **Gather Data** — collect facts and feelings about the period being reviewed; broaden before narrowing.
3. **Generate Insights** — make sense of the data; surface patterns, root causes, and unstated assumptions.
4. **Decide What to Do** — pick a small number of concrete actions for the next iteration.
5. **Close the Retrospective** — appreciate, reflect on the retro itself, end well.

The original book is the canonical source for the framework — read it for the rationale behind each stage, the recommended activities, and the facilitator postures.

## How the three layers stack in retro mode

| # | Stage | Cardon role most active | Core Protocols (McCarthy) that plug in | Silent round fit? (see [`silent-round.md`](silent-round.md)) |
|---|-------|-------------------------|---------------------------------------|-------------------|
| 1 | Set the Stage | Facilitator | **Check In** — every attendee briefly arrives present. | — |
| 2 | Gather Data | Facilitator + Pacer | Pacer holds short timeboxes. **Pass / Unpass** if anyone declines a turn. | **Yes — Path A** (cluster). Output shape: `ideas` / `concerns`. Exits via 6c handoff into Stage 3. |
| 3 | Generate Insights | Facilitator (keeps discussion balanced) | **Ask For Help**, **Intention Check** when contributions get muddy. | **Yes — Path A** (cluster) on root causes / patterns; or Path B with `rate-1-5` on impact. Exits via 6c handoff into Stage 4 or via 6a if an action is already clear. |
| 4 | Decide What to Do | **Decision Driver** | **Decider** for binary picks; **Resolution** after No votes. | **Yes — Path B** (discuss + rank) on candidate actions. Output shape: `options` or `rank-top-N`. Exits via 6a → Decider. |
| 5 | Close the Retrospective | **Process Coach** | **Perfection Game** as the feed-forward format; **Check Out** for anyone who needs it. | — |

### When to invoke a Silent round inside a retro stage

A Silent round is *one* technique among many the Facilitator can choose for Stages 2 / 3 / 4. The book and community catalogues offer others (Mad Sad Glad, Timeline, 5 Whys, Dot Voting, Plus/Delta, Lean Coffee, etc.). Reach for a Silent round specifically when:

- The room has a HiPPO who consistently anchors the first round of any prompt.
- The team has previously fallen into "the first person to speak set the frame" in this recurring retro.
- Expertise on the sub-topic is asymmetric and quieter experts have been getting drowned out.
- The Decision Driver wants to surface independent root-cause / action candidates before letting the team converge.

For routine retros where the team already participates evenly and the dominant voice problem isn't present, stick to the activities the team already knows.

## Suggested time budget (typical 60-min retro)

These are pacing inputs for the Pacer. Adjust by team and topic — a post-incident retro typically gives more time to Generate Insights; an end-of-quarter retro typically gives more time to Set the Stage and Close.

| Stage | Suggested share | At 60 min |
|-------|-----------------|-----------|
| 1. Set the Stage | ~10% | 5–6 min |
| 2. Gather Data | ~25% | 15 min |
| 3. Generate Insights | ~25% | 15 min |
| 4. Decide What to Do | ~25% | 15 min |
| 5. Close the Retrospective | ~15% | 9–10 min |

Each stage is one Cardon "sequence" for the Pacer's purposes — and the 20-minute-max rule still applies, so split larger stages into sub-sequences if you exceed the budget.

## Detecting retro mode

The skill enters retro mode when **any** of the following is true:

- The session name contains "retro" or "retrospective" (case-insensitive).
- The operator confirms it is a retrospective in answer to a single targeted question.
- A prior session in the same Confluence space (found via CQL) was already in retro mode for the same recurring meeting.

When in retro mode:

- The opening attribution block adds the Derby & Larsen line (between McCarthy and the skill marker — see `SKILL.md`).
- The Confluence page rendered from `confluence-page.html` includes the **Agenda — 5 stages** section.
- Per-stage "notes" sub-sections are added so the team can capture what happened in each stage.

When not in retro mode, none of the above is added — Derby & Larsen are not cited in non-retro sessions.

## Attribution rule

If retro mode is active for a session, every artifact (chat opening, Confluence page header, agenda block) cites Derby and Larsen, the book title, the publisher, and the publisher URL. The book is referenced — never reproduced.

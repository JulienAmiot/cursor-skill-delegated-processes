---
name: delegated-processes
description: Facilitate a recurring team meeting on Confluence using Alain Cardon's Systemic Team Coaching Delegated Processes (rotating roles) layered with Jim and Michele McCarthy's Core Protocols (in-meeting behaviors). Connects to the Atlassian / Confluence MCP, discovers prior sessions in a chosen space by tag and similar title, infers attendees and role history, proposes a fair role rotation (Facilitator, Decision Driver, Pacer, Process Coach, plus optional Host / Technician / Scribe), points each role-holder at the Core Protocols they can lean on (Check In, Decider, Resolution, Perfection Game, Pass, Protocol Check, Intention Check, Ask For Help, Check Out), and creates a new timestamped Confluence page tagged with the skill marker. Use when the user asks to facilitate, prepare, or run a team meeting; mentions delegated roles, role rotation, systemic team coaching, Alain Cardon, Metasysteme; mentions the Core Protocols, Software For Your Head, McCarthy, Decider, Check In, Perfection Game; runs a Scrum / agile ceremony with rotating facilitation; or wants meeting minutes that track who held which role across sessions.
---

# Systemic Delegated Processes + Core Protocols — Confluence-driven facilitation

> **Format (structure / roles).** Systemic Team Coaching Delegated Processes — by **Alain Cardon, MCC**.
> **Source.** <https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/>
>
> **Behavioral layer.** The Core Protocols — by **Jim and Michele McCarthy**. License: **GPL v3+**.
> **Source.** <https://liveingreatness.com/core-protocols/>
>
> **Skill marker (used as text anchor for CQL search).** `cursor-skill-delegated-process`

**Open every session — both in chat and on the created Confluence page — with the attribution block above verbatim.** The page header uses the same block so future sessions can find it via CQL `text ~ "cursor-skill-delegated-process"`. Both attributions are required even if no Core Protocol is explicitly invoked in a given session.

## What this skill does

Operates entirely against Confluence:

1. **Finds prior sessions** in a user-chosen space by searching for the skill marker + similar title.
2. **Infers attendees and role history** by parsing the prior session pages.
3. **Proposes role rotation** for the next session using that history (Cardon's circulation principle).
4. **Creates a new timestamped Confluence page** under the chosen parent, with the attribution header, attendee/role table, briefings for each role-holder, and empty decision/process-notes sections to fill during the meeting.
5. **Updates the same page** after the meeting with decisions, process notes, and a "next session" hand-off.

There is no local roster file, no local rotation log. The Confluence space is the source of truth.

## When to use it

Use for: recurring team / executive meetings (5–15 people, intact team), Scrum / agile ceremonies (retro, planning, review, refinement) with rotating facilitation.

Do **not** use for: crisis or one-off meetings with strangers, podium / informational presentations, audiences > 15 people. Per Cardon, the framework does not fit those contexts — say so and offer a lighter alternative instead.

## The roles

Four core rotating roles: **Facilitator**, **Decision Driver**, **Pacer**, **Process Coach**. Three optional roles activated only when context warrants: **Host** (rotating locations), **Technician** (complex AV), **Scribe** (Facilitator can't write on the board). The decision-maker is excluded from rotation; for Scrum / self-managing teams see the Scrum mapping section in Step 3 below.

For per-role detail (mission, before / during / avoid / hand-off), read [`roles.md`](roles.md). It is the source for every briefing card written into the Confluence page.

## Behavioral layer — Core Protocols

On top of Cardon's role rotation (structure), the skill layers Jim and Michele McCarthy's **Core Protocols** (behavior). The two are orthogonal: Cardon decides *who does what*; the Core Protocols decide *how every attendee shows up*.

Quick map (the full table and rationale live in [`core-protocols.md`](core-protocols.md)):

- **Check In** — opens the meeting; Facilitator cues a one-round check-in.
- **Decider / Resolution** — Decision Driver uses these to actually drive decisions, instead of ad-hoc "are we close?".
- **Perfection Game** — Process Coach can use this format for the final 10-minute round.
- **Pass / Unpass, Ask For Help, Protocol Check, Intention Check, Check Out** — available to any attendee at any time, distributing enforcement away from the Facilitator and Pacer.

**Reference, not reproduction.** The skill only mentions protocols by name and points to the McCarthy source URL. It never reproduces protocol text or mechanics — that would make the skill a GPL derivation. Each role briefing in [`roles.md`](roles.md) ends with a "Core Protocols you can lean on" line so the role-holder knows which protocols to read up on at the source URL before the meeting.

## Prerequisites — Confluence MCP

The skill **requires** an Atlassian / Confluence MCP server with at least these tools:

- `getAccessibleAtlassianResources` — discover `cloudId`.
- `getConfluenceSpaces` — pick the space.
- `getConfluencePage` — read prior session pages.
- `searchConfluenceUsingCql` — find prior sessions by marker + title.
- `createConfluencePage` — create the new session page.
- `updateConfluencePage` — update it after the meeting.

If any of these is missing, say so up front and refuse to proceed rather than fall back to local files. The whole point of this skill is that Confluence is the durable store.

## Conversation style — read this once, apply throughout

- **Ask one question per turn.** Never batch questions. Wait for the answer before asking the next.
- **Minimalist prompts.** One sentence per question. No preamble, no recap, no "great choice!".
- **Show, don't narrate.** When you create or update a page, link it. Don't describe what you wrote.
- **Confirm before destructive or large actions** (creating the page, updating it after the meeting). One terse yes/no.
- **No emojis. No filler.**

## Workflow

```
- [ ] 1. Open with attribution (3 lines verbatim)
- [ ] 2. Discover cloudId + ask space
- [ ] 3. Ask parent page (root for sessions)
- [ ] 4. Ask session name
- [ ] 5. Search for prior sessions; infer canonical title + attendee history
- [ ] 6. Confirm attendees for this session
- [ ] 7. Compute + propose role rotation
- [ ] 8. Confirm rotation; create the page
- [ ] 9. After the meeting: update the page with decisions + process notes
```

### Step 1 — Open with attribution

Print this block in the chat before anything else, and again as the page header in Step 8:

```
Format (structure): Systemic Team Coaching Delegated Processes — by Alain Cardon, MCC.
Source: https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/

Behavioral layer: The Core Protocols — by Jim and Michele McCarthy. License: GPL v3+.
Source: https://liveingreatness.com/core-protocols/

Skill: cursor-skill-delegated-process
```

Both author / source blocks are required on every session — even if no Core Protocol is invoked. The McCarthy GPL terms require attribution whenever their work is referenced.

### Step 2 — cloudId + space

Call `getAccessibleAtlassianResources` to discover the `cloudId`. If multiple sites are accessible, ask the user which one. Then call `getConfluenceSpaces` and ask the user which space (one prompt: "Which Confluence space?"). Store the chosen space ID and key for the rest of the session.

### Step 3 — Parent page (root for session pages)

Ask: "Which page should new session pages live under? (paste the URL or page ID)". Resolve to a `parentId` via `getConfluencePage`.

#### Scrum / agile mapping (ask once per team, recorded on the first page)

If the meeting is a Scrum ceremony or any agile context with no clear "boss", ask once:

1. **Product Owner as decision-maker** — PO is excluded from rotation; SM + engineers rotate.
2. **PO not attending this ceremony** — no one excluded; all attendees rotate.
3. **Fully self-organising** — no one excluded; PO + SM + engineers all rotate.

Record the answer in the session page (under `## Scrum mapping`). On subsequent runs, read the most recent prior session and reuse the recorded mapping unless the user overrides. **Refuse to map the Scrum Master to the decision-maker slot** — the SM is a facilitator / coach, not an authority.

### Step 4 — Session name

Ask: "Session name?". One word or short phrase is fine ("Campaign Retro", "Atlas Weekly Exec").

### Step 5 — Find prior sessions and infer canonical title + attendees

Run a CQL search scoped to the chosen space, looking for the skill marker and a fuzzy title match:

```
space = "{SPACE_KEY}" AND text ~ "cursor-skill-delegated-process" AND title ~ "{session name}"
```

Sort results by date, descending.

- **If 1+ results:** open the most recent matching page (and a couple older ones if available). Extract:
  - The **canonical title pattern** (e.g. "Campaign Retro — YYYY-MM-DD") — propose this format to the user with one prompt: "Past sessions use the title pattern `{pattern}`. Use the same?".
  - The **attendees** from each page's roles table.
  - The **role history** (who held which role on each prior page).
- **If 0 results:** cold start. The session name becomes the canonical title prefix. Tell the user "No prior sessions found — cold start." and move on.

### Step 6 — Confirm attendees

- **With history:** present the union of attendees seen across the most recent 3–5 prior sessions. Ask: "Same attendees as last time? (Y / list changes)". Apply the changes.
- **Cold start:** ask for attendees once, free-text. Format expected: **one name per line, names only**. Do not ask for or record team roles / titles / functions — they bias the systemic role assignment and are not relevant to it.

If a Scrum mapping was recorded earlier and it requires identifying a specific person (e.g. "PO as decision-maker"), ask that as a single targeted question after the attendee list is in — e.g. "Who is the PO?". Do not ask everyone for their team role.

### Step 7 — Compute + propose role rotation

Apply Cardon's circulation principle using the role history extracted in Step 5:

1. For each core role, count how many times each attendee has held it across prior sessions.
2. For each role, pick the attendee who has held it the **fewest** times AND, where possible, did **not** hold any core role in the **most recent** prior session (avoid back-to-back).
3. Break ties by lowest total core-role count.
4. The decision-maker (if recorded) is never assigned a rotating role.
5. For optional roles (only if the operator activated any), apply the same logic with their own counts.
6. **Cold start:** with no history and no team-role information, the first assignment is arbitrary by design. Map attendees to roles in the order the operator listed them: 1st → Facilitator, 2nd → Decision Driver, 3rd → Pacer, 4th → Process Coach. Tell the operator it is arbitrary and invite swaps. From session 2 onwards the rotation algorithm has real history to work with.

Show the proposal as a small table and ask: "Approve rotation?". Wait for `Y` or a swap instruction.

### Step 8 — Create the Confluence page

Use `createConfluencePage` with:

- `spaceId` from Step 2
- `parentId` from Step 3
- `title` = canonical pattern from Step 5 (or session name + date for cold start)
- `contentFormat` = `html`
- `body` = HTML rendered from the canonical structure in [`confluence-page.html`](confluence-page.html), populated with:
  - The 3-line attribution header (verbatim)
  - The Scrum mapping (if applicable)
  - The roles + assignees table
  - One briefing section per role-holder, content drawn from [`roles.md`](roles.md)
  - Empty decisions table and process-notes section
  - A short "rotation context" block citing how many prior sessions were found and linking to the most recent

Confluence labels are not exposed by the MCP `createConfluencePage` tool — the **skill marker** (`cursor-skill-delegated-process`) is therefore embedded in the page header text so CQL `text ~ "cursor-skill-delegated-process"` finds it. **Do not omit the marker.** Without it the next session will not find this page.

After creation, return the URL to the operator. Do not narrate the contents — they are on the page.

### Step 9 — After the meeting: update the page

Ask the operator to paste back, separately:

- decisions reached (one per line),
- the Process Coach's notes (one line per teammate),
- the Pacer's actual-vs-budget per sequence (optional).

Then call `updateConfluencePage` to fill the **Decisions** and **Process notes** sections. Do not rewrite the rest of the page. Confirm by linking the updated page.

## Hard rules (do not negotiate)

- **One pilot per decision.** Never list two people.
- **Specific, dated deadlines.** "Next sprint", "soon", "ASAP" are not deadlines.
- **Sequences ≤ 20 minutes** with pacer pings every 5 minutes.
- **Feed-forward must be addressed to one person at a time**, future-oriented, solution-focused. No collective comments.
- **Always rotate.** Same person + same role across consecutive sessions = expert capture. Refuse without explicit override.
- **Always print the 3-line attribution** at session start in chat AND in the page header.
- **Always include the skill marker `cursor-skill-delegated-process`** in the page header so future runs can find it via CQL.
- **Never apply the framework to crisis meetings, podium presentations, or audiences > 15** — flag the mismatch and stop.

## Anti-patterns to refuse

- Falling back to local files when the Confluence MCP is unavailable.
- Creating a page without the skill marker in the header.
- Mapping the Scrum Master to the decision-maker slot.
- Assigning the same person the same role two sessions in a row without explicit operator override.
- Writing decisions without a single pilot or without a dated deadline.
- Batching multiple questions in one turn during the operator interview.
- Asking attendees for their team role / title / function. The systemic role rotation is peer-to-peer; team role information biases the assignment and must not be collected.

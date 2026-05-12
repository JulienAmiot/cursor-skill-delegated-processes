---
name: delegated-processes
description: Facilitate a recurring team meeting on Confluence using Alain Cardon's Systemic Team Coaching Delegated Processes (rotating roles) layered with Jim and Michele McCarthy's Core Protocols (in-meeting behaviors), and — when the meeting is a retrospective — structured around the 5-stage agenda from Esther Derby and Diana Larsen's Agile Retrospectives. Connects to the Atlassian / Confluence MCP, discovers prior sessions in a chosen space by tag and similar title, infers attendees and role history, proposes a fair role rotation (Facilitator, Decision Driver, Pacer, Process Coach, plus optional Host / Technician / Scribe), points each role-holder at the Core Protocols they can lean on (Check In, Decider, Resolution, Perfection Game, Pass, Protocol Check, Intention Check, Ask For Help, Check Out), supports an optional Silent round (NGT / KJ method lineage) the Decision Driver can invoke to shape judgment-heavy decisions before commitment (silent generation → simultaneous reveal → cluster or discuss → optional silent re-think → Decider or handoff), and creates a new timestamped Confluence page tagged with the skill marker (with a 5-stage agenda block when in retro mode and a Silent rounds section when at least one was invoked). Use when the user asks to facilitate, prepare, or run a team meeting; mentions delegated roles, role rotation, systemic team coaching, Alain Cardon, Metasysteme; mentions the Core Protocols, Software For Your Head, McCarthy, Decider, Check In, Perfection Game; runs a Scrum / agile ceremony with rotating facilitation; runs a retrospective and mentions Derby, Larsen, Agile Retrospectives, or the 5 stages (Set the Stage, Gather Data, Generate Insights, Decide What to Do, Close); mentions silent round, nominal group technique, NGT, affinity diagram, KJ method, silent brainwriting, anti-anchoring decision-shaping, HiPPO, or wants a structured way to surface judgment before committing a decision; or wants meeting minutes that track who held which role across sessions.
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

Two phases — **prepare** (Confluence-aware interview) and **capture-then-publish** (local-first, deliberate publish at the end):

1. **Finds prior sessions** in a user-chosen space by searching for the skill marker + similar title.
2. **Infers attendees and role history** by parsing the prior session pages and the team's roster page.
3. **Proposes role rotation** for the next session using that history (Cardon's circulation principle).
4. **Opens a local session scratchpad** with the resolved metadata (space, parent, title, retro mode, roster with accountIds, role assignment, briefings). The scratchpad is the durable record while the meeting runs.
5. **Captures decisions, process notes, pacer log, and check-in entries into the scratchpad as they happen** — never directly to Confluence during the meeting.
6. **At the end of the meeting, offers to publish** the captured session to an external destination. The MVP destination is Confluence (creates a new timestamped page in the chosen parent, populated from the scratchpad). The architecture leaves room for additional adapters later (Notion, Slack canvas, GitHub issue, etc.) without changing the capture format.

Confluence is **read** during the prepare phase (prior sessions, roster, whiteboards) and **written** only once at the end, when the operator confirms the publish. No half-baked pages, no mid-meeting Confluence churn.

### Local-first capture, deliberate publish

The scratchpad lives at `~/.cursor/skills/delegated-processes/sessions/{YYYYMMDDHHMM}-{slugified-title}/` (cross-platform — `%USERPROFILE%\...` on Windows). The skill creates the directory on Step 8.

Each session folder holds:

- `session.json` — canonical structured data (metadata, roster with accountIds, role assignment, decisions, process notes, pacer log, check-in log, publish targets the operator approves).
- `preview.md` — human-readable rendering, regenerated on every capture so the operator can paste a snapshot into Slack, Loom notes, or share via screen-share during the meeting.

Both files are updated atomically on every capture. If the agent crashes or Cursor restarts, the next agent invocation can resume from `session.json`.

Publish destinations are **derived views** of the scratchpad. Today the only adapter is Confluence; the design assumes more will follow.

## When to use it

Use for: recurring team / executive meetings (5–15 people, intact team), Scrum / agile ceremonies (retro, planning, review, refinement) with rotating facilitation.

Do **not** use for: crisis or one-off meetings with strangers, podium / informational presentations, audiences > 15 people. Per Cardon, the framework does not fit those contexts — say so and offer a lighter alternative instead.

## The roles

Four core rotating roles: **Facilitator**, **Decision Driver**, **Pacer**, **Process Coach**. Three optional roles activated only when context warrants: **Host** (rotating locations), **Technician** (complex AV), **Scribe** (Facilitator can't write on the board).

In Cardon's original framework, a single hierarchical decision-maker (the boss of an executive committee, a manager + direct reports, etc.) is excluded from rotation. **In Scrum, Kanban, LeSS, SAFe, or any other self-managing / agile team, no one is excluded from rotation by virtue of their team role** — see the dedicated subsection in Step 3 below.

For per-role detail (mission, before / during / avoid / hand-off), read [`roles.md`](roles.md). It is the source for every briefing card written into the Confluence page.

## Retrospective mode — Derby & Larsen 5 stages

When the meeting is a **retrospective**, the skill activates "retro mode" and structures the agenda around the 5 stages from:

> **Agile Retrospectives: Making Good Teams Great** — by **Esther Derby** and **Diana Larsen**. Pragmatic Bookshelf, 2006.
> Source: <https://pragprog.com/titles/dlret/agile-retrospectives/>

The 5 stages: **Set the Stage · Gather Data · Generate Insights · Decide What to Do · Close the Retrospective**. They become the outer agenda; Cardon roles and Core Protocols operate inside it. Detection rules and the per-stage map of which role and which protocol activate live in [`retrospective-stages.md`](retrospective-stages.md).

**Reference, not reproduction.** As with the Core Protocols, the skill cites Derby & Larsen and the book + publisher URL but does not reproduce activities, exercises, or extended text from the book. Read the book for the activities; use a community catalog like retromat.org for inspiration.

When retro mode is **off**, Derby & Larsen are not cited (the framework is not being applied). The Cardon and McCarthy attributions remain on every session regardless.

## Behavioral layer — Core Protocols

On top of Cardon's role rotation (structure), the skill layers Jim and Michele McCarthy's **Core Protocols** (behavior). The two are orthogonal: Cardon decides *who does what*; the Core Protocols decide *how every attendee shows up*.

Quick map (the full table and rationale live in [`core-protocols.md`](core-protocols.md)):

- **Check In** — opens the meeting; Facilitator cues a one-round check-in.
- **Decider / Resolution** — Decision Driver uses these to actually drive decisions, instead of ad-hoc "are we close?".
- **Perfection Game** — Process Coach can use this format for the final 10-minute round.
- **Pass / Unpass, Ask For Help, Protocol Check, Intention Check, Check Out** — available to any attendee at any time, distributing enforcement away from the Facilitator and Pacer.

**Reference, not reproduction.** The skill only mentions protocols by name and points to the McCarthy source URL. It never reproduces protocol text or mechanics — that would make the skill a GPL derivation. Each role briefing in [`roles.md`](roles.md) ends with a "Core Protocols you can lean on" line so the role-holder knows which protocols to read up on at the source URL before the meeting.

## Decision-shaping protocol — Silent round (when invoked)

For judgment-heavy decisions where the room has a HiPPO dynamic or visible expertise asymmetry, the Decision Driver can invoke a **Silent round**: silent generation → simultaneous reveal → optional author-explains → cluster (Path A) or discuss (Path B) → optional silent re-think → Decider or handoff.

It is **not** a McCarthy Core Protocol. It is a Cardon-layer composition that uses several Core Protocols as primitives (Intention Check, Pass / Unpass, Ask For Help, Protocol Check, Decider, Resolution). The lineage is public-domain methodology:

- **Nominal Group Technique** — Delbecq, Van de Ven & Gustafson (1971, 1975) — structural ancestor (silent → share → discuss → re-think → decide).
- **KJ method / affinity diagram** — Jiro Kawakita (1960s) — simultaneous-reveal and clustering ancestor.
- **Silent brainwriting** — Bernd Rohrbach (1968) — simultaneous-posting ancestor.

The full protocol — phases, role + protocol map, Path A vs Path B, hard rules, anti-patterns — lives in [`silent-round.md`](silent-round.md). The Decision Driver reads it before the first invocation.

Use it for: impact / severity / confidence rating, root-cause weighting, action selection from a long list, qualitative data gathering ("what surprised you?"), picking among options where the first speaker would frame the choice set. **Reserve it** for judgment-heavy or anchoring-prone questions; do not run a Silent round on every decision.

The skill cites the Silent round lineage **only when at least one Silent round is invoked in the session**. The Cardon and McCarthy attributions remain unconditional; the Derby & Larsen block remains retro-mode-only.

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
- [ ] 1.  Open with attribution (3 lines verbatim)
- [ ] 2.  Discover cloudId + ask space
- [ ] 3.  Ask parent location (page OR folder)
- [ ] 4.  Ask session name
- [ ] 5.  Search for prior sessions (pages) AND linked whiteboards; infer canonical title + attendee history
- [ ] 6.  Confirm attendees for this session (resolve to @mentions)
- [ ] 7.  Compute + propose role rotation
- [ ] 8.  Open the local session scratchpad; print rotation + briefings inline; meeting begins
- [ ] 9.  During the meeting: capture decisions, process notes, pacer log, check-in entries into the scratchpad as they happen
- [ ] 10. End of meeting: offer to publish; on confirmation, render the scratchpad to the chosen destination (MVP: Confluence)
```

### Step 1 — Open with attribution

Print the **standard** block in the chat before anything else, and again as the page header in Step 8:

```
Format (structure): Systemic Team Coaching Delegated Processes — by Alain Cardon, MCC.
Source: https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/

Behavioral layer: The Core Protocols — by Jim and Michele McCarthy. License: GPL v3+.
Source: https://liveingreatness.com/core-protocols/

Skill: cursor-skill-delegated-process
```

If retro mode is active (see Step 4), insert this **additional** block between the Core Protocols block and the `Skill:` line:

```
Retrospective structure: Agile Retrospectives: Making Good Teams Great — by Esther Derby and Diana Larsen. Pragmatic Bookshelf, 2006.
Source: https://pragprog.com/titles/dlret/agile-retrospectives/
```

When at least one **Silent round** has been invoked in this session (Step 9), this **additional** block is appended to the chat opening (retroactively, on first invocation) and to the published page header (Step 10) between the previous block and the `Skill:` line:

```
Decision-shaping (when invoked): Silent round — silent generation → simultaneous reveal → optional author explains → cluster or discuss → optional silent re-think → Decider or handoff.
Lineage: Nominal Group Technique — Delbecq, Van de Ven & Gustafson (1971, 1975).
Simultaneous reveal + clustering: KJ method — Jiro Kawakita (1960s) · silent brainwriting — Bernd Rohrbach (1968).
At most 2 silent phases per round. '?' sticky permitted for clarifying questions.
```

The Cardon and McCarthy blocks are required on every session even if no protocol is invoked. The Derby & Larsen block is only required when retro mode is active. The Silent round block is only required when at least one Silent round was invoked.

### Step 2 — cloudId + space

Call `getAccessibleAtlassianResources` to discover the `cloudId`. If multiple sites are accessible, ask the user which one. Then call `getConfluenceSpaces` and ask the user which space (one prompt: "Which Confluence space?"). Store the chosen space ID and key for the rest of the session.

### Step 3 — Parent location (page **or** folder)

Ask: "Which page or folder should new session pages live under? (paste the URL or ID — both pages and folders work)". Resolve to a `parentId`:

- **Page** (URL contains `/pages/<id>/...`) — confirm with `getConfluencePage`.
- **Folder** (URL contains `/folder/<id>...`) — the MCP wrapper returns 404 on `getConfluencePage` for folder ids, so confirm via CQL `space = "{KEY}" AND parent = "<id>"` (any non-empty result proves the folder exists and is reachable). Inspect its current children with the same query to make sure it's the right hub.

If the operator asks for help finding the parent, do **not** dump every page in the space. Run a focused CQL search across **both pages and folders** for ritual / ceremony hub names — for example:

```
space = "{SPACE_KEY}" AND (type = page OR type = folder) AND (title ~ "ritual" OR title ~ "ceremon" OR title ~ "iteration" OR title ~ "sprint" OR title ~ "retro" OR title ~ "meeting" OR title ~ "agile")
```

Present at most the top 3–5 candidates, **folders first** (folders are almost always the right ritual hub on modern Confluence — Confluence rolled out folders specifically as durable ceremony / topic containers, separate from regular pages). Show one line per candidate with `[type] title (id) — created by …`, then ask the operator to pick or paste another.

`createConfluencePage` accepts folder IDs as `parentId` (Confluence v2 REST API supports this; the MCP wrapper passes the value through unchanged). If Confluence rejects the id at create time, fall back to the space home and tell the operator once.

Whiteboards are **never** used as a `parentId` — they cannot host page descendants. Whiteboards are linked working surfaces, see Step 5.

Record both the resolved `parentId` and its `parentType` (`page` or `folder`); both are rendered into the new session page in Step 8.

#### Self-managing / agile teams — no role-based exclusion

For Scrum, Kanban, LeSS, SAFe, or any team that operates without a single hierarchical "boss", **every attendee rotates equally — no exclusion by team role, no question asked**. Do not offer to exclude the Product Owner, the Scrum Master, the Tech Lead, the Product Manager, the Engineering Manager, or anyone else as the "decision-maker". Refuse to map the Scrum Master to the decision-maker slot.

Cardon's original "decision-maker excluded from rotation" rule applies only when the team is **explicitly hierarchical** (executive committee with a CEO, a manager + their direct reports, etc.). Use it only when the operator explicitly opts in by naming the decision-maker. Never derive exclusion from a job title or a team-role label.

Render the corresponding line on the page as `_Decision-maker (excluded from rotation):_ —` whenever no one is explicitly excluded (the agile / self-managing default).

### Step 4 — Session name + retro detection

Ask: "Session name?". One word or short phrase is fine ("Campaign Retro", "Atlas Weekly Exec").

Then determine retro mode:

- If the name contains "retro" or "retrospective" (case-insensitive) → retro mode is **on**, no extra question needed.
- Else if the most recent prior session for this title (found in Step 5) was already in retro mode → retro mode is **on**, no extra question needed.
- Else → ask one targeted question: "Is this a retrospective? (Y/N)".

Record the answer; it drives Step 8 (page rendering) and the attribution block in Step 1 / page header.

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
- **If 0 results:** cold start *for this skill*. Before declaring full cold start, also run a parent-scoped CQL search to detect a **pre-existing title pattern from prior, non-skill sessions**:

```
space = "{SPACE_KEY}" AND parent = "{PARENT_ID}" AND title ~ "{session intent}"
```

If a strong prior pattern emerges (e.g. `YYYYMMDDHHMM Retrospective`), propose it to the operator with one prompt: "Past sessions in this folder use the pattern `{pattern}`. Reuse it?". This keeps the new skill-managed page consistent with the team's existing archive even though the prior pages don't carry the skill marker.

#### Whiteboard discovery (linked working surface)

In modern Confluence, teams often run a recurring meeting from a **paired whiteboard** (sticky notes for *gather data* and *generate insights*) and write the minutes on a separate page. After the prior-session search, also search for whiteboards in the same space whose title matches the session intent:

```
space = "{SPACE_KEY}" AND type = whiteboard AND title ~ "{session name}"
```

Sort by date descending. The most recent matching whiteboard (created in the same week as today, or the single most recent if there is a clear cadence) is a candidate **working surface** — link it from the new session page in Step 8 (it is never the parent). Always present the candidate to the operator with one prompt: "Use whiteboard `{title}` as the working surface? (Y / paste another / N for none)". If none is found, leave the linked-artifacts whiteboard slot empty rather than fabricating one.

### Step 6 — Confirm attendees

- **With history:** present the union of attendees seen across the most recent 3–5 prior sessions (read each prior page and extract the @mention spans from its roles table — that gives you names *and* their resolved accountIds). Ask: "Same attendees as last time? (Y / list changes)". Apply the changes.
- **Cold start or new attendees:** ask once, free-text. **Accept the list in any of these forms — comma-separated, whitespace-separated, or one name per line.** Parse by splitting on `[,\s]+` and trimming each token. Names only — never ask for team roles / titles / functions.

#### Resolve every attendee to an Atlassian @mention

Plain-text names in the page are an anti-pattern: they don't notify the person, don't link to a profile, and the next session can't reuse them. For every parsed name, resolve to an `accountId` in this order:

1. **Prior sessions in the same space.** If any prior delegated-processes page in the space mentions this name, reuse the `accountId` stored in that page's `<span data-type="mention" data-user-id="...">@Name</span>` element.
2. **Atlassian directory lookup.** Call `lookupJiraAccountId` with the parsed name as `searchString` (Confluence and Jira share the same user directory, so a Jira lookup resolves Confluence users too). The directory returns at most the top 5 by relevance heuristics — for common first names (19 "Carla"s, 65 "Julien"s, etc.) the right person is routinely outside that top 5, so **never trust the top result blindly**.
3. **Cross-reference against actual space contributors (the disambiguation step that matters).** For each remaining candidate, probe the space directly:

   ```
   space = "{SPACE_KEY}" AND contributor = "<candidateAccountId>"
   ```

   A non-empty result proves the candidate has actually touched the space (created, edited, or commented). A candidate with space contributions **wins** over a higher-ranked directory candidate with zero. If exactly one candidate has space contributions, take it silently. If several do, present those (with contribution counts from the `totalSize` field) and ask the operator to pick.
4. **Read the team roster page when no directory candidate touches the space.** When step 3 eliminates every directory candidate, the right person is in the long tail of the directory. Look up a canonical team-roster page in the same space — try titles like `Resource Plan`, `Team`, `Roles`, `Meeting Organization`, `Daily Stand-up Interface`, or any page that lists team members — and extract the full names directly (either from the page body, or from the `<span data-type="mention" data-user-id="...">@Full Name</span>` spans when available). Then re-call `lookupJiraAccountId` with the **full name from the roster**; that almost always returns the right account as the top result. Re-run the space-contributor check on the new candidate as a sanity test.
5. **Operator fallback.** Only after steps 1–4 fail, ask the operator once for the `@handle`, profile URL, or `accountId`. Cache every resolution in this session's roster so you only ask once per name.

Render every attendee reference in the Confluence page (roles table, briefings, decisions, process notes, rotation context, check-in log, "other attendees" line) as `<span data-type="mention" data-user-id="ACCOUNT_ID">@Name</span>`. The plain name is fine in chat with the operator; it is **never** acceptable in the rendered page.

If the team is explicitly hierarchical and the operator opted into "decision-maker excluded" in Step 3, ask once after the list is in — "Who is the decision-maker?" — and resolve them with the same procedure. Skip this question for any Scrum / agile / self-managing team.

### Step 7 — Compute + propose role rotation

Apply Cardon's circulation principle using the role history extracted in Step 5:

1. For each core role, count how many times each attendee has held it across prior sessions.
2. For each role, pick the attendee who has held it the **fewest** times AND, where possible, did **not** hold any core role in the **most recent** prior session (avoid back-to-back).
3. Break ties by lowest total core-role count.
4. The decision-maker is excluded from rotating roles **only if** the operator explicitly named one in Step 3 for an explicitly hierarchical team. On Scrum / agile / self-managing teams there is no such exclusion.
5. For optional roles (only if the operator activated any), apply the same logic with their own counts.
6. **Cold start:** with no history and no team-role information, the first assignment is arbitrary by design. Map attendees to roles in the order the operator listed them: 1st → Facilitator, 2nd → Decision Driver, 3rd → Pacer, 4th → Process Coach. Tell the operator it is arbitrary and invite swaps. From session 2 onwards the rotation algorithm has real history to work with.

Show the proposal as a small table and ask: "Approve rotation?". Wait for `Y` or a swap instruction.

### Step 8 — Open the local session scratchpad; print rotation + briefings

Build the session folder at `~/.cursor/skills/delegated-processes/sessions/{YYYYMMDDHHMM}-{slugified-title}/` (create the parent directory if missing). Write two files:

- `session.json` — the canonical structured record, conforming to:

  ```json
  {
    "skill": "cursor-skill-delegated-process",
    "createdAt": "ISO-8601",
    "retroMode": true,
    "atlassian": {
      "cloudId": "…",
      "spaceId": "…",
      "spaceKey": "…",
      "parentId": "…",
      "parentType": "page|folder",
      "parentTitle": "…",
      "parentUrl": "…",
      "whiteboard": { "id": "…", "title": "…", "url": "…" }   // or null
    },
    "title": "…",
    "titlePattern": "…",
    "roster": [
      { "name": "Display Name", "accountId": "…", "rosterContext": "free-form one-liner inferred from the team roster page, optional" }
    ],
    "rotation": {
      "facilitator": "<accountId>",
      "decisionDriver": "<accountId>",
      "pacer": "<accountId>",
      "processCoach": "<accountId>",
      "host": "<accountId> | null",
      "technician": "<accountId> | null",
      "scribe": "<accountId> | null",
      "decisionMaker": "<accountId> | null",
      "otherAttendees": ["<accountId>", "…"],
      "reasoning": "one-line rationale citing prior sessions"
    },
    "rotationContext": {
      "priorSessionCount": 0,
      "mostRecentPriorSessionUrl": null
    },
    "agenda": {                         // present only when retroMode is true
      "stages": [
        { "n": 1, "name": "Set the Stage",            "minutes": 5,  "activity": "" },
        { "n": 2, "name": "Gather Data",              "minutes": 20, "activity": "" },
        { "n": 3, "name": "Generate Insights",        "minutes": 20, "activity": "" },
        { "n": 4, "name": "Decide What to Do",        "minutes": 15, "activity": "" },
        { "n": 5, "name": "Close the Retrospective",  "minutes": 5,  "activity": "" }
      ]
    },
    "captures": {
      "checkInLog":  [ /* { "by": "<accountId>", "text": "…", "atIso": "…" } */ ],
      "decisions":   [ /* { "n": 1, "decision": "…", "pilot": "<accountId>", "deadlineIso": "…", "successMeasure": "…", "atIso": "…" } */ ],
      "deciderLog":  [ /* { "n": 1, "proposal": "…", "outcome": "ADOPTED|RESOLVED|REJECTED", "resolutionNotes": "…", "atIso": "…" } */ ],
      "processNotes":[ /* { "pattern": "anonymised one-liner", "atIso": "…" } */ ],
      "pacerLog":    [ /* { "n": 1, "sequence": "…", "plannedMinutes": 20, "actualMinutes": 22, "atIso": "…" } */ ],
      "stageNotes":  { "1": "", "2": "", "3": "", "4": "", "5": "" },     // retro only
      "silentLog":   [
        /*
        {
          "n": 1,
          "prompt": "…",
          "outputShape": "ideas | options | concerns | rank-top-N | rate-1-5 | tshirt",
          "path": "A-cluster | B-discuss",
          "attribution": false,
          "items": [ { "i": 1, "text": "verbatim sticky", "from": null } ],
          "clusters": [ { "theme": "…", "itemIndices": [1, 4, 7] } ],
          "ranks":    [ { "round": 1, "values": ["…"], "atIso": "…" } ],
          "discussionNotes": [ "…" ],
          "outcome": "converged | most-supported-with-dissent | handoff | aborted",
          "convergedProposal": "…",
          "dissent": "one-liner naming dissenting position",
          "handoffTo": "next agenda step or retro stage",
          "linkedDecisionId": 3,
          "atIso": "…"
        }
        */
      ]
    },
    "publish": {
      "approvedTargets": [],            // populated in Step 10 (e.g. ["confluence"])
      "results":         []             // [ { "target": "confluence", "url": "…", "publishedAtIso": "…" } ]
    }
  }
  ```

- `preview.md` — a Markdown rendering of the same data, regenerated atomically on every capture, so the operator can copy/paste a snapshot into Slack or share it via screen-share. The preview contains the attribution block, the rotation table (with `@Name` for each role), the briefings drawn from [`roles.md`](roles.md), the empty capture sections (filled live), and — when retro mode is on — the 5-stage agenda block.

Once the scratchpad is written, **print the rotation table and the per-role briefings inline in the chat** (so attendees can see who they are in the rotation and what to do). The full briefings live in `preview.md` for sharing; the inline chat version may compress to mission + key Core Protocol per role.

End the prepare phase with: "Scratchpad opened at `<path>`. Meeting can begin — capture commands available in Step 9."

### Step 9 — During the meeting: live capture into the scratchpad

The operator drives capture through short commands. Treat each as one capture event; append to `session.json`, regenerate `preview.md`, and acknowledge with a single line (`✓ decision #3 recorded`, `✓ pacer ping for sequence 2 (planned 20 / actual 22)`, etc.). Never ask follow-up questions during the meeting unless a required field is missing — keep the operator in the meeting, not in the chat.

Recognised capture intents (parse loosely; the operator will not type rigid commands while facilitating):

- **`decide` / `decision: …`** — append to `captures.decisions`. Required: decision text, pilot (single accountId), deadline (specific date), success measure. If any is missing, prompt for **only** the missing field, in one short line.
- **`decider proposal / outcome` / `decider: …`** — append to `captures.deciderLog`. Capture the Decider protocol invocation when the team uses it.
- **`note: …` / `process: …`** — append to `captures.processNotes` as an anonymised one-liner.
- **`pacer: sequence N planned X actual Y`** — append to `captures.pacerLog`.
- **`check in: …`** — append to `captures.checkInLog`.
- **`stage N notes: …`** (retro mode) — append to `captures.stageNotes[N]`.
- **Silent round intents** (see [`silent-round.md`](silent-round.md) for the full protocol). All append to the current `captures.silentLog` entry, identified by the most recent `silent start:` that has not yet exited:
  - **`silent start: <prompt> [shape: ideas | options | concerns | rank-top-N | rate-1-5 | tshirt] [path: A | B]`** — open a new entry. On the first invocation of the session, also append the Silent round attribution block (Step 1) to the chat opening so the team can see the practice is in play.
  - **`silent reveal: <items, one per attendee>`** — capture the simultaneous reveal verbatim into `items[]`. Per-item authorship (`from`) is captured only when the operator opted into attribution at `silent start:` time; default is no authorship in the log.
  - **`silent cluster: <theme name> :: <item indices>`** — Path A only. Append a cluster.
  - **`silent rank: <round N> values: <…>`** — Path B numeric / ranking shape only. Append a rank reveal.
  - **`silent talk: <one-line summary>`** — append to `discussionNotes` (clarifying summary of Phase 3 or Phase 2.5 explanations; the meeting itself is not transcribed).
  - **`silent converged: <proposal>`** — exit 6a. Set `outcome: "converged"`, `convergedProposal`. The operator then runs the normal `decide: …` for Decider; the resulting decision is linked back via `linkedDecisionId`.
  - **`silent most-supported: <proposal> dissent: <one-liner>`** — exit 6b. Loop 2 done, no convergence. Set `outcome: "most-supported-with-dissent"`.
  - **`silent handoff: <next stage or step>`** — exit 6c (data-gathering only). Set `outcome: "handoff"`, `handoffTo`. No Decider follows.
  - **`silent abort: <reason>`** — set `outcome: "aborted"`. Typical reasons: reveal leaked, ran out of time, prompt was malformed.

Hard rules in capture:

- One pilot per decision. If the operator names two, ask which one.
- Specific dated deadlines. Reject vague deadlines and ask for a date.
- No collective process notes. Reject "the team should …" and ask for an anonymised pattern.
- **No collective stickies in a Silent round.** Reject "we should …", "the team always …" and ask the operator to rephrase as a specific observation, option, or concern in the first person.
- **At most 2 silent phases per Silent round.** If a third `silent reveal:` is attempted after a previous re-think, refuse and ask the operator to exit via 6a, 6b, or 6c.
- **One output shape per Silent round.** If the operator tries to mix shapes mid-round, refuse and suggest opening a second `silent start:` after the first exits.

The Confluence MCP is **not called** during the meeting. All writes are to the local scratchpad.

### Step 10 — End of meeting: publish

When the operator signals end-of-meeting (e.g. "we're done", "publish", "wrap up"), summarise what's in `session.json` in a single short paragraph (decision count, process-note count, pacer entries, check-in entries) and ask one question: **"Publish to Confluence? (Y / list other destinations / N — keep local only)"**.

The publish layer is destination-agnostic. Each destination is an adapter that takes `session.json` and produces an external artifact. **MVP: Confluence only.** The full list of supported adapters today:

- **`confluence`** — creates a new page via `createConfluencePage` using `atlassian.spaceId` and `atlassian.parentId`, title from `session.json::title`, body rendered from [`confluence-page.html`](confluence-page.html) populated from the scratchpad. After creation, append `{ "target": "confluence", "url": "…", "publishedAtIso": "…" }` to `publish.results` and the URL to the operator. **The skill marker `cursor-skill-delegated-process` MUST appear verbatim in the page header text** so CQL `text ~ "cursor-skill-delegated-process"` will find it on future runs.

Future adapters (not implemented) would attach here: `notion`, `slack-canvas`, `github-issue`, `local-markdown` (just emit `preview.md` as the canonical output), etc.

If the operator declines Confluence and lists no other destination, the scratchpad remains as the durable record. Keep it in place — never auto-delete. The next invocation can re-publish on demand by reading the existing `session.json`.

After a successful publish, ask one more terse question: "Anything to add before we close? (paste / N)". On `N`, end the session.

## Hard rules (do not negotiate)

- **One pilot per decision.** Never list two people.
- **Specific, dated deadlines.** "Next sprint", "soon", "ASAP" are not deadlines.
- **Sequences ≤ 20 minutes** with pacer pings every 5 minutes.
- **Feed-forward must be addressed to one person at a time**, future-oriented, solution-focused. No collective comments.
- **Always rotate.** Same person + same role across consecutive sessions = expert capture. Refuse without explicit override.
- **Always print the 3-line attribution** at session start in chat AND in the published page header.
- **Always include the skill marker `cursor-skill-delegated-process`** in the published page header so future runs can find it via CQL.
- **Never apply the framework to crisis meetings, podium presentations, or audiences > 15** — flag the mismatch and stop.
- **Local-first capture, deliberate publish.** During the meeting, every capture goes to `session.json` (and the regenerated `preview.md`). Confluence is **read** before the meeting and **written** at most once at the end, on the operator's explicit go-ahead.
- **No upfront Confluence page.** Never create the Confluence page before the meeting starts. The page is the publish artifact, populated end-to-end from the scratchpad after the meeting.
- **Silent round reveal is simultaneous, always.** Round-robin reading aloud does not satisfy the non-anchoring property when one or more attendees have a single item. See [`silent-round.md`](silent-round.md).
- **Silent rounds cap at 2 silent phases.** Past loop 2, exit via 6b (most-supported + flagged dissent) or 6c (handoff). Never run a third silent phase.
- **Silent rounds promise non-anchoring, not anonymity.** Do not present them as anonymous to the team; promise that no one will hear another's answer before forming their own.

## Anti-patterns to refuse

- Creating a Confluence page upfront with empty Decisions / Process notes sections to fill later. The page is the **publish output**, not the runtime store. Use the local scratchpad during the meeting and create the page once at the end.
- Calling `createConfluencePage` or `updateConfluencePage` during the meeting (between Step 8 and Step 10). Mid-meeting Confluence churn produces half-baked public pages, racy version numbers, and notification spam. Capture goes to `session.json`; Confluence is touched only on the operator's end-of-meeting go-ahead.
- Treating the local scratchpad as ephemeral. `~/.cursor/skills/delegated-processes/sessions/...` is the durable record of the session and survives Cursor restarts and crashes; the published Confluence page is a derived view of it. Never auto-delete the scratchpad after publish.
- Falling back to local-only when Confluence is briefly unavailable at publish time (Step 10). Capture has already happened locally; the right move is to retry the publish or queue it, not to silently skip it.
- Creating a page without the skill marker in the header.
- Mapping the Scrum Master to the decision-maker slot.
- Excluding **any** attendee from rotation by virtue of their team role on a Scrum / agile / self-managing team. Such teams rotate everyone equally; offer no opt-out per role.
- Assigning the same person the same role two sessions in a row without explicit operator override.
- Writing decisions without a single pilot or without a dated deadline.
- Batching multiple questions in one turn during the operator interview.
- Asking attendees for their team role / title / function. The systemic role rotation is peer-to-peer; team role information biases the assignment and must not be collected.
- Rejecting an attendee list because of its formatting. Comma-separated, whitespace-separated, and one-per-line are all valid — parse and resolve, do not push the work back to the operator.
- Rendering attendee names as plain text on the Confluence page. Always use the `<span data-type="mention" data-user-id="...">@Name</span>` element so the person is notified and properly linked, and so the next session can parse the page back into a roster.
- Silently picking one user when `lookupJiraAccountId` returns multiple matches for a name. Always cross-reference with `space = X AND contributor = "<id>"` first; if multiple candidates still have space contributions, present those with counts and ask the operator.
- Trusting the top result of `lookupJiraAccountId` when the parsed name is a common first name with many directory matches. The directory's relevance heuristic is space-agnostic; the right person for the meeting is the one who actually touches the chosen Confluence space.
- Falling back to the operator when a roster page in the space (Resource Plan, Team page, Daily Stand-up Interface, etc.) holds the canonical full names. Read the roster, re-lookup with the full name, and only ask the operator if step 4 also fails.
- Using a whiteboard ID as `parentId` for `createConfluencePage`. Whiteboards cannot host pages — they are linked artifacts on the session page, never the parent.
- Restricting the parent search to `type = page`. Folders are first-class containers in modern Confluence and are usually the right ritual hub; always include `type = folder` in parent-discovery CQL and surface folders first in the candidate list.
- Listing every page in the space when asked to help with the parent. Search for ritual / ceremony hub names across pages **and** folders, present the top few, folders first.
- Running a Silent round with round-robin reveal — the first reader anchors everyone else. Use simultaneous reveal at the Facilitator's cue, even when each attendee has only one item to contribute.
- Using NGT-style round-robin one-item-at-a-time as the *reveal* mechanism. The optional Phase 2.5 author-explains pass is **one-shot per author**, descriptive, not persuasive — it is not the reveal.
- Promising attendees that a Silent round is anonymous. It is not. It is non-anchoring. Frame it honestly: no one hears another's answer before forming their own.
- Exiting a decision-bearing Silent round without Decider. Produces "great conversation, no commitment" — the failure mode the skill exists to eliminate. Either go to Decider (6a or 6b), or relabel the round as data-gathering and exit via 6c handoff and own that.
- Using a Silent round on every decision. Adds 15–20 min per round. Reserve for judgment-heavy or anchoring-prone questions; routine commits go straight to Decider.
- Citing the Silent round lineage (NGT, KJ method, silent brainwriting) on a session that did not invoke a Silent round. The block is only printed when at least one Silent round was captured in `session.json`.

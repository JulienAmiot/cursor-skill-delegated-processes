---
name: delegated-processes
description: Facilitate a recurring team meeting using Alain Cardon's Systemic Delegated Processes. Assigns rotating systemic roles (Facilitator, Decision Driver, Pacer, Process Coach, plus optional Host / Technician / Scribe) to attendees with fair circulation across meetings, generates a per-attendee briefing card so each person knows what to do, and produces minutes (decisions, pilots, deadlines) that update the rotation log. Use when the user asks to facilitate, prepare, or run a team meeting; mentions delegated roles, role rotation, systemic team coaching, Alain Cardon, Metasysteme; or wants meeting minutes that track who held which role.
---

# Systemic Delegated Processes — Meeting Facilitation Skill

> Based on **"Systemic Team Coaching Delegated Processes"** by **Alain Cardon, MCC** — Metasystème Coaching.
> Source article: <https://www.metasysteme-coaching.eu/english/systemic-team-coaching-delegated-processes/>
>
> **Always cite the author and the source URL** in every artifact you produce with this skill (briefing cards, minutes, rotation log entries, summaries).

## What this skill does

Helps the user run a real team meeting where every attendee actively holds a **systemic role** instead of just attending. Specifically it:

1. **Assigns roles** to attendees with fair rotation across meetings (Cardon's circulation principle).
2. **Briefs each attendee** with a personal role card describing what to do before / during / after.
3. **Produces minutes** after the meeting (decisions, pilots, deadlines) and updates the rotation log.

It does NOT run the meeting live, build the content agenda, or send pacer pings — humans hold those seats.

## When to use it

Use whenever the user asks to:

- Prepare or facilitate a recurring team / executive meeting (5–15 people, intact team).
- Assign or rotate meeting roles.
- Capture minutes from a delegated-process meeting.

Per Cardon, do **not** apply this approach to:

- Crisis or one-off meetings with strangers from disparate origins.
- Podium / one-way informational presentations.
- Audiences larger than ~15 people.

If the user's context fits one of these, say so and offer a lighter alternative instead.

## The roles

Four **core** roles, always rotated across attendees:

| Role | One-line function |
|------|-------------------|
| **Facilitator** (moderator) | Conducts team energy and participation. |
| **Decision Driver** | Provokes decisions and records them with pilot + deadline. |
| **Pacer** | Announces time spent / time remaining inside short sequences. |
| **Process Coach** | Gives individual, future-oriented feed-forward at the end. |

Three **optional** roles, used only when context warrants:

| Role | When to add |
|------|-------------|
| **Host** | Meetings rotate across locations / sites. |
| **Technician** | Meetings rely on complex AV / collaboration tooling. |
| **Scribe** | Only if the Facilitator can't comfortably write on the board. |

The **decision-maker** (boss / team leader) is **never** assigned a rotating role. They validate decisions and may even be absent from a given meeting.

For role-by-role detail (mission, before / during / avoid / hand-off), read [`roles.md`](roles.md).

## Workflow

Track progress with this checklist:

```
- [ ] 1. Locate or create the team roster
- [ ] 2. Locate or create the rotation log
- [ ] 3. Propose role assignments (fair rotation) and confirm with user
- [ ] 4. Generate one briefing card per attendee
- [ ] 5. After the meeting, write minutes and append to the rotation log
```

### Step 1 — Locate or create the roster

Look for `roster.md` in the working directory (or a path the user gives you). If it doesn't exist, create one from [`templates/roster.md`](templates/roster.md). Ask the user for:

- Team / meeting name and cadence (weekly, monthly, quarterly).
- Decision-maker (excluded from rotation).
- Attendees (5–15 people).
- Whether optional roles (Host / Technician / Scribe) are in play for this team.

### Step 2 — Locate or create the rotation log

Look for `rotation-log.md`. If absent, create it from [`templates/rotation-log.md`](templates/rotation-log.md). The log records, per past meeting, who held which role. It is the input that makes Step 3 fair.

### Step 3 — Propose role assignments (fair rotation)

Apply Cardon's circulation principle: **every attendee must rotate through every core role over time**. Use this assignment procedure:

1. From `rotation-log.md`, count how many times each attendee has held each of the four core roles.
2. For each role, pick the attendee who has held it the **fewest** times AND did **not** hold any core role in the **most recent** meeting (avoid back-to-back).
3. Break ties with whoever has held the **fewest total** core roles overall.
4. Never assign a rotating role to the decision-maker.
5. If optional roles are active, assign them with their own count. Only let one person hold an optional + a core role if the team has fewer than six rotating attendees.

Show the proposal to the user as a small table and **wait for confirmation** before generating cards or writing files.

Example proposal table:

```
| Role            | Assignee | Last held this role |
|-----------------|----------|---------------------|
| Facilitator     | Sami     | 2 meetings ago      |
| Decision Driver | Léa      | never               |
| Pacer           | Pavel    | never               |
| Process Coach   | Iris     | 3 meetings ago      |
```

### Step 4 — Generate briefing cards

For each assigned attendee, produce a personal briefing card using [`templates/briefing-card.md`](templates/briefing-card.md). Pull the per-role content from [`roles.md`](roles.md). Every card MUST contain the Cardon attribution block at the top.

Output cards either:

- inline in the chat (one per attendee), or
- as files under `briefings/<YYYY-MM-DD>/<attendee>.md` if the user asks for files.

Ask the user which they prefer if it isn't obvious from context.

### Step 5 — After the meeting: minutes + rotation update

Use [`templates/minutes.md`](templates/minutes.md). The minutes MUST contain:

- Date, attendees present, who held which role.
- A **decisions table**: `Decision · Pilot (one person) · Deadline (specific date) · Measure of success`.
- A short **process notes** section capturing the Process Coach's feed-forward.
- The Cardon attribution block.

Then append a single row to `rotation-log.md` reflecting who held which role this meeting — that single row is what makes future fair rotation possible.

## Hard rules (do not negotiate)

- **One pilot per decision.** Never list two people as pilot for the same action.
- **Specific, dated deadlines.** Short-term beats far-off; "Q3" or "soon" are not deadlines.
- **Sequences ≤ 20 minutes** with pacer pings every 5 minutes.
- **Feed-forward must be addressed to one person at a time**, future-oriented, and solution-focused. No collective comments like "we were all tired".
- **Always rotate.** Same person + same role across consecutive meetings = expert capture. Refuse unless the user explicitly overrides.
- **Always attribute** Alain Cardon and the Metasystème source URL on every artifact.

## Anti-patterns to refuse

- Assigning the decision-maker a rotating role.
- Letting the same person keep a core role across consecutive meetings without an explicit user override.
- Producing minutes without pilots, or with vague / undated deadlines.
- Producing any artifact without the Cardon attribution.
- Applying this skill to crisis meetings, one-off cross-team gatherings, or audiences > 15 — flag the mismatch instead.

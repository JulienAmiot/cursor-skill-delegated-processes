# Silent round — decision-shaping protocol

> **Structural ancestor.** Nominal Group Technique (NGT) — André L. Delbecq, Andrew H. Van de Ven & David H. Gustafson, 1971 / 1975.
> Reference: Delbecq, Van de Ven, Gustafson, *Group Techniques for Program Planning: A Guide to Nominal Group and Delphi Processes*, Scott Foresman, 1975.
>
> **Simultaneous reveal + clustering ancestors.** KJ method / affinity diagram — Jiro Kawakita, 1960s.
> Silent brainwriting — Bernd Rohrbach, *Kreativ nach Regeln*, 1968.
>
> Public-domain methodology. This file references the lineage by name and gives operational guidance for using it inside this skill — it does not reproduce the source texts.

The Silent round is a **decision-shaping protocol** the Decision Driver can lean on when the room is judgment-heavy, has a HiPPO dynamic (Highest-Paid Person's Opinion anchoring everyone else), or has visible expertise asymmetry on the question at hand. It sits **before** McCarthy's **Decider** in the decision pipeline: it produces a refined, less-anchored proposal; Decider then commits the team to it.

It is **not** a McCarthy Core Protocol. It is a Cardon-layer composition that *uses* several Core Protocols as primitives (**Intention Check**, **Pass / Unpass**, **Ask For Help**, **Protocol Check**, **Decider**, **Resolution**, optionally **Perfection Game**). The licensing layers stay clean: Cardon-side practice, public-domain ancestors, McCarthy protocols invoked by name only.

## When to use it

Use a Silent round when **any** of these is true:

- The output requires individual judgment that can be anchored (impact, severity, root cause, action priority, choice among options, qualitative observations).
- There is a HiPPO in the room or strong expertise asymmetry on the sub-topic.
- The team has previously fallen into "the first person to speak set the frame" on a similar question.
- It is a retrospective and the stage is **Gather Data**, **Generate Insights**, or **Decide What to Do** (see [`retrospective-stages.md`](retrospective-stages.md)).

Do **not** use it when:

- A binary commit/abort proposal is already on the table — Decider alone is faster.
- The session has less than ~15 min remaining and the question is straightforward.
- The reveal cannot be made simultaneous (e.g. an async chat where people read each other before posting). The non-anchoring property is the whole point; without it, the protocol is theatre.

## Honest framing: non-anchoring, not anonymity

A Silent round preserves **non-anchoring** (no contribution influences another before all are visible). It does **not** preserve anonymity — once stickies are on the board, authorship is often guessable from handwriting, vocabulary, or position in the room. Do not promise the team anonymity; promise them that no one will hear anyone else's answer before forming their own.

## The 8 phases

| # | Phase | Time | Medium |
|---|-------|------|--------|
| 0 | Frame the prompt + output shape | 1–2 min | Spoken |
| 1 | **Silent generation** | 2–5 min | Paper · sticky notes · private chat draft · whiteboard private mode |
| 2 | **Simultaneous reveal** | 30 sec | Board · whiteboard · chat |
| 2.5 | *Optional* author-explains pass | 1–3 min | One-shot per author, not round-robin |
| 3 | **Cluster (Path A)** OR **Discuss (Path B)** | 5–10 min | Whiteboard / verbal |
| 4 | *Optional* silent re-think / re-rank | 2–3 min | Same private medium |
| 5 | Simultaneous reveal #2 | 30 sec | Same |
| 6 | Frame proposal · OR most-supported + dissent · OR handoff | 1–2 min | Decision Driver |
| 7 | **Decider** (+ Resolution if No) — when decision-bearing | 2–3 min | McCarthy |
| 8 | Capture in scratchpad | — | `captures.silentLog` |

**Hard ceiling: at most 2 silent phases per round** (= phases 1 + 4). Past loop 2, take the most-supported candidate, flag the dissent in the page, hand to Decider.

### Phase 0 — Frame the prompt + output shape

The Decision Driver states the question and the **output shape** explicitly. Mixing shapes in one round is not allowed; run consecutive rounds if you need multiple shapes.

Supported output shapes:

- `ideas` — free-text ideas (typical for Gather Data: "what surprised you?")
- `options` — candidate decisions or options (typical for Decide What to Do)
- `concerns` — risks, worries, blockers
- `rank-top-N` — private ranking, top N items from a shared list
- `rate-1-5` — Likert-style rating on a defined dimension
- `tshirt` — XS / S / M / L / XL

If the prompt is ambiguous, anyone calls **Intention Check** before silent generation starts.

### Phase 1 — Silent generation

Each attendee writes individually, in private. Medium is whatever the team's setting supports — paper, sticky notes, a private chat draft, a whiteboard's private-sticky mode.

- Pacer holds the timebox strictly. 2–5 min is typical; calibrate by output shape.
- Truly silent — no whispering, no chat. A clarifying question goes on a "?" sticky, answered after the silent phase by the Decision Driver (or Facilitator).
- Not writing is fine and unremarkable. **Pass / Unpass does not apply during silent**; nothing is required.

### Phase 2 — Simultaneous reveal

Everyone reveals at the Facilitator's cue — stickies posted to the board at the same moment, papers flipped, chat lines posted, whiteboard votes revealed.

- **Protocol Check** is the enforcement mechanism if anyone reveals early (verbal or visual).
- No discussion yet. Reading the board silently is fine.

### Phase 2.5 — Optional author-explains pass

Skip when items are self-explanatory ("Barcelona", "Tokyo", "we missed the release date").

Use when items are ambiguous, behavioural, or context-dependent ("the standups feel performative", "the deploy script is brittle"). Each author has roughly 30 seconds to explain *why* their item is on the board — **one-shot per author, not round-robin one-at-a-time**.

- **Pass / Unpass** applies here: an author may decline to explain.
- This is not a discussion. No "I disagree", no "we tried that". Clarifying questions only.

### Phase 3 — Cluster (Path A) or Discuss (Path B)

The branch is the Decision Driver's call, set at framing time (Phase 0).

- **Path A (cluster / affinity / KJ method):** group stickies into themes on the whiteboard. Used for **generative / divergent** prompts (`ideas`, `concerns`). Output is a small set of themes, not a single proposal. Confluence Whiteboards are native for this.
- **Path B (open discussion):** balanced airtime on the full list. Used for **convergent / decision-bearing** prompts (`options`, `rank-top-N`, `rate-1-5`, `tshirt`). Output feeds Phase 6.

Both paths use:

- **Facilitator** runs balanced discussion (no one dominates).
- **Ask For Help** when someone needs input from a specific teammate.
- **Intention Check** when someone shifts from "explaining" to "convincing".
- **Protocol Check** if anyone evaluates contributions during a still-divergent clustering phase.

### Phase 4 — Silent re-think (optional)

Used when:

- The board is still divergent after discussion.
- The team needs to privately rank or rate after seeing all contributions.
- An individual wants to rewrite their own stickies in light of what they heard.

Same private medium as Phase 1. Pacer holds the timebox. This is the second of the two silent phases — there is no third.

### Phase 5 — Simultaneous reveal #2

Same mechanics as Phase 2. Facilitator cues; Protocol Check on early reveal.

### Phase 6 — Exit

Three exits, mutually exclusive:

- **6a — Framed proposal** (decision-bearing). Decision Driver writes the proposal: text + pilot (one) + dated deadline + measure of success. Goes to Phase 7 (Decider).
- **6b — Most-supported + flagged dissent** (decision-bearing, but loop 2 did not converge). Decision Driver names the most-supported candidate and explicitly records the dissent: *"team did not converge — adopting X, Y dissents on Z"*. Goes to Phase 7 (Decider) with the dissent on the table. Process Coach notes the non-convergence pattern.
- **6c — Handoff** (data-gathering). Output is a list / themes that feeds the next agenda step or the next retro stage. No Decider; no abort. Decision Driver records the handoff target. This is the legitimate exit for a Gather Data prompt.

### Phase 7 — Decider (+ Resolution)

When the round is decision-bearing (exit 6a or 6b), run McCarthy's **Decider** on the framed proposal. If any No, run **Resolution** as the standard follow-up. The Silent round does the *shaping*; Decider does the *commitment*. Both are recorded in `captures.deciderLog` per the existing skill flow.

When the round is data-gathering (exit 6c), Phase 7 is skipped.

### Phase 8 — Capture

Append to `captures.silentLog` in `session.json`, regenerate `preview.md` atomically, acknowledge with a single line. The published Confluence page renders a Silent rounds section only if the log is non-empty (see [`confluence-page.html`](confluence-page.html)).

## Role + protocol map at a glance

| Phase | Cardon role most active | Core Protocols that plug in | Notes |
|-------|-------------------------|------------------------------|-------|
| 0 Frame | Decision Driver | Intention Check (if muddy) | One output shape per round |
| 1 Silent #1 | Pacer (timebox) | "?" sticky for clarifying Qs | Pass does NOT apply (no turns) |
| 2 Reveal #1 | Facilitator (cues) | Protocol Check on early reveal | Simultaneous, always |
| 2.5 Author explains | Facilitator | Pass / Unpass | Optional, one-shot per author |
| 3a Cluster | Facilitator | Ask For Help · Intention Check | Whiteboard-native |
| 3b Discuss | Facilitator | Ask For Help · Intention Check · Protocol Check | Same posture as Decider discussion |
| 4 Silent re-think | Pacer | "?" sticky still legal | Optional, up to once |
| 5 Reveal #2 | Facilitator | Protocol Check on early reveal | Simultaneous |
| 6 Frame / dissent / handoff | Decision Driver | — | Three mutually-exclusive exits |
| 7 Decider + Resolution | Decision Driver | **Decider** · **Resolution** | Only when decision-bearing |
| 8 Capture + observe | Process Coach (observer) | **Perfection Game** later, in final 10 min | Notes patterns for feed-forward |

## Path A vs Path B — when each fits

| | Path A — cluster (affinity / KJ) | Path B — discuss + rank |
|--|----------------------------------|--------------------------|
| Output shape | `ideas`, `concerns` | `options`, `rank-top-N`, `rate-1-5`, `tshirt` |
| Purpose | Surface themes for later interpretation | Pick one (or rank top N) |
| Exit | 6c handoff to next stage typically | 6a framed proposal → Decider |
| Retro stage fit | Gather Data (2), Generate Insights (3) | Decide What to Do (4) |
| Medium | Whiteboard sticky grouping | Whiteboard ranking · paper · chat |

A single meeting may run both, back-to-back: a Path A Silent round in Stage 3 produces themes; a Path B Silent round in Stage 4 picks the action from those themes.

## Hard rules (do not negotiate)

- **Silent means silent.** No whispering, no chat. Clarifying questions go on a "?" sticky, answered after the silent phase.
- **Reveal is simultaneous, always.** Round-robin reading aloud does not satisfy the non-anchoring property when one or more attendees have a single item.
- **The optional author-explains pass is one-shot per author.** It is not NGT-style round-robin one-item-at-a-time, and it is not a discussion.
- **No evaluation during cluster.** "We tried that", "won't work", "I like that one" — Protocol Check applies. Clarifying questions only until clustering is done.
- **Verbatim capture.** The Scribe (or whoever writes on the board) does not paraphrase. Originator can edit afterward.
- **No collective stickies.** "We should…", "the team always…", "people are…" — same rejection rule as Process Coach feed-forward. Rewrite as a specific observation, an option, or a concern phrased in the first person.
- **One output shape per round.** Need multiple shapes? Run consecutive rounds.
- **At most 2 silent phases** (= phases 1 + 4). After that, take most-supported, flag dissent, exit via 6b → Decider.
- **Decider exit is mandatory when the round is decision-bearing.** A decision-bearing round that ends in "interesting board, let's move on" is the anti-pattern. Either go to Decider, or relabel the round as data-gathering (6c handoff) and own that.
- **Handoff exit is legitimate for data-gathering only.** Do not use 6c to dodge a hard decision.
- **"?" sticky is always legal** and is not a Pass and not a No vote. It means "I don't have enough information to contribute to this prompt".

## Anti-patterns to refuse

- **Reveal before the cue.** Spoken or visual leakage aborts the round and forces a re-card from a new private medium.
- **Round-robin reading aloud as the reveal mechanism.** The first reader anchors everyone. Use simultaneous reveal even when each person has only one item.
- **Author-explains-pass as a debate.** It is one-shot, descriptive, not persuasive. Protocol Check applies.
- **Clustering during discussion (Path A) by majority opinion.** Themes emerge from sticky text adjacency, not from voting. If two stickies clearly belong together by content, cluster them; the team confirms. Do not vote on theme membership.
- **Skipping Decider on a decision-bearing round.** Produces "great conversation, no commitment" — the failure mode the skill exists to eliminate.
- **Running three silent phases.** The 2-phase ceiling is structural; ignoring it usually means the question is malformed. Reframe the prompt instead.
- **Mixing output shapes in one round.** A prompt that wants both ideas *and* ratings is two rounds, not one.
- **Promising anonymity.** Promise non-anchoring. Anonymity is rarely achievable in a 5–15 person intact team and is not what the protocol delivers.
- **Using a Silent round on every decision.** Adds 15–20 min per round. Reserve for judgment-heavy, anchoring-prone questions.

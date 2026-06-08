---
name: call-prep
description: >-
  Produces a pre-call prep brief for an upcoming sales meeting using the GTM Coach memory
  bank and (if connected) the user's calendar. Use when the user says "prep me for my call
  with X", "what should I know before the Acme meeting", "brief me on my next meeting", or
  "get me ready for today's calls". Pulls deal history, SPICED gaps, stakeholders, open
  commitments, risks, and a recommended call plan.
---

# Call Prep

Generate a focused, evidence-based prep brief for an upcoming conversation.

## Inputs

Read `../../references/memory-bank.md` and `../../references/spiced-framework.md`.
Require `./sales-memory/`. If absent, route the user to setup (`gtm-coach`).

Identify the target meeting:
- If the user names an account/deal/person, use that.
- Else, if a `~~calendar` tool is connected (see `config.json.calendar_tool` /
  `mcp-discovery.md`), pull upcoming events, find the next external sales meeting(s), match
  attendees to `people/` and `accounts/` in the bank, and prep those. If multiple are
  upcoming, list them and confirm or prep the next one.
- If you cannot identify the meeting, ask once.

## Build the brief

Pull from the deal/account/people/call files and `index.json`. Produce:

1. **Snapshot** — account, deal, stage, amount, close date, deal health (green/yellow/red),
   days since last touch.
2. **Where we are (SPICED)** — current state of each element with what's confirmed vs
   assumed. Cite the call where each was learned.
3. **SPICED gaps to close this call** — the 2–3 missing/weak elements, ranked. For each, give
   1–2 ready-to-ask discovery questions from `spiced-framework.md`.
4. **Stakeholders** — who's attending (from `~~calendar` if available), their role
   (economic-buyer/champion/etc.), sentiment, and whether the deal is single- or
   multi-threaded. Flag if the economic buyer has never been on a call.
5. **Open commitments** — what each side promised on the last call; what's outstanding from
   us (don't show up having dropped a promise).
6. **Risks & watch-outs** — from the risk signals in `spiced-framework.md`; competitor
   mentions and how to handle; objections raised before.
7. **Recommended call plan** — a tight agenda: the one outcome to get, the key questions, and
   the specific dated next step to propose.

## Output

Lead with the snapshot and the single most important objective for this call. Keep it
skimmable (the user may read it 5 minutes before the call). Cite calls by date so they can
dig in if needed. If memory on this account is thin, say so and prep from what exists rather
than inventing context.

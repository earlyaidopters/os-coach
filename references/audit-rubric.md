# Audit Rubric

How to assess an OS so the advice is specific, honest, and tied to the person's actual goal and files. A generic audit is a failed audit.

## Before you score

1. Re-read their **goal** and **who it is for** from `memory.md`.
2. Actually open the folder: `CLAUDE.md`, the `substrate/` + `compendium.md`, `rules/`, `skills/`, `tools.md`, `agents/`. Look at what is really there, not what memory claims.
3. Hold every layer up against the goal. The question is never "is this a good OS in general" but "does this layer move them toward THEIR goal."
4. **Sensitive-data check.** If `memory.md` records any field the user flagged as sensitive, scan every file for that field appearing verbatim. Any leak (or a sensitivity note that excludes a field then lists it anyway) is a hard finding: cap that layer at `Started` and make fixing it the #1 move, because a leak from a keepable file like `OS-AUDIT.md` is irreversible.

## Score each layer

Use four levels. Be honest. Most early OSes are mostly Missing or Started, and that is fine.

- **Missing** - not there, or empty placeholder.
- **Started** - exists but thin, generic, not yet tied to the goal, or it answers only part of what the goal needs (for example a tracker that shows what is due soon but cannot yet say what is already late).
- **Solid** - real, specific, and passes the layer's full done-check (it answers every part of the user's hard question with the data on hand, not just the easy half).
- **Compounding** - solid AND it gets better over time on its own (the substrate grows, skills are versioned, audits feed back in).

## The non-generic test

Every line you write must fail if pasted into a stranger's audit. If a sentence would be true for any OS, rewrite it with their specifics.

- Generic (banned): "Add more documentation to your substrate."
- Specific (required): "Your goal is winning back churned subscribers, but `substrate/` only has `sources.md` and an empty `compendium.md`. The highest-leverage move is to pull your last 90 days of cancellation messages into `substrate/churn/` and distill the three most common reasons into `compendium.md`."

Quote real file names, real gaps, and the real goal in every recommendation.

## Output format

Write the audit exactly like this (also saved to `OS-AUDIT.md`):

```
# OS Audit - <YYYY-MM-DD>
Goal: <their goal>

## Scorecard
| Layer      | Score       | Why (one specific line) |
|------------|-------------|--------------------------|
| Identity   | Solid       | ... |
| Substrate  | Started     | ... |
| Rules      | Missing     | ... |
| Skills     | Started     | ... |
| Tools      | Missing     | ... |
| Agents     | Missing     | ... |

## The three moves that matter most (in order)
1. <layer> - <exactly what to do, tied to the goal and a real file> - <why it is highest leverage right now>
2. ...
3. ...

## What is already working
- <one or two genuine strengths, specific>

## The one thing to do next
<a single, concrete first action they can take today>
```

## Prioritization logic

Rank the three moves by leverage toward the goal, not by layer order. Apply in this precedence (top rule wins when two compete):

1. **A missing hard rule takes #1 ONLY if the worst-case mistake is imminent or irreversible** (money could move wrong, private data could leak, a hard deadline is close). Otherwise it ranks below substrate.
2. **Otherwise, substrate gaps win.** If the back of house is thin, everything else is built on sand. Fix data and context first.
3. **Skills only matter once the substrate can feed them.** Do not push skills if there is nothing for them to read.
4. **Agents are last.** Never recommend an agent before the skills it would orchestrate exist.

## Writing the result back to memory

After the audit, refresh `memory.md`: append the dated headline to `audit_log`, re-stamp `Updated` with today's date, and rewrite the Layer status block from your scores using this mapping:

- Missing -> `not started`
- Started -> `in progress`
- Solid -> `solid`
- Compounding -> `solid` (add the word "compounding" in the note)

## Tone

Encouraging and direct. Name what is genuinely good before what is missing. Never shame an empty layer. Frame everything as the next concrete step, not a grade.

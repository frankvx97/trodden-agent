# Analysing a Trodden study

## Numbers

- **Task success:** use `successes`/`attempts` and `successInterval95`, which is Trodden's adjusted-Wald 95% interval, computed for you. Example: "11 of 14 (95% CI 52–93%)".
- **Verified vs marked done:**
  - `verifiedSuccesses` fired a success rule;
  - the rest pressed Done themselves.

  Say which, and treat manual-only tasks as self-reported.
- **Small samples:** under about 20 participants, report counts, not percentages ("4 of 5"). Words like "most" need the count next to them.
- **Time on task:** successful attempts only (`medianSeconds`). Never use time on failed attempts as efficiency.
- **SEQ:** `seqAverage` on 1–7. About 5.5 is average and below 5 is harder than typical.
- **Comparing two designs or two rounds:** only call one better when the intervals barely overlap. Otherwise, "no clear difference with this many people".
- **Funnel:** report people screened out and people who abandoned, not only completers.
- Preview sessions are excluded unless `includePreview` is true. Keep it false.

## Severity (Nielsen)

| Score | Meaning |
|---|---|
| 0 | Not a problem |
| 1 | Cosmetic |
| 2 | Minor (low priority) |
| 3 | Major (high priority) |
| 4 | Catastrophe (fix before release) |

Rate on frequency × impact × persistence. One rater is unreliable, so always mark ratings provisional for the designer to confirm.

## Pitfalls

- Inferring intent from clicks alone. Mark it as a hypothesis unless an answer supports it.
- Treating one participant's comment as a pattern.
- Ignoring the "Something else" give-up answers. Read them.
- Over-reading an overall rating from a prototype of a single flow.

## Findings template

```
# <Study name> — findings

**Study:** <dates>, <n> participants (<device mix>), <find problems | measure>
**Decision this informs:** <from the plan>

## Summary
<3–5 sentences: what worked, what did not, the one thing to fix first>

## Paths
| Path | Success (95% CI) | Median time | SEQ | Gave up |
|---|---|---|---|---|

## Findings
### 1. <Short title> — severity <n> (provisional)
- **Observed:** <counts, routes, ratings>
- **Participants said:** "<verbatim quote>" (<participant id>)
- **Likely cause:** <interpretation>
- **Recommendation:** <specific fix, with the file or screen if known>

## What worked

## Next steps
<fixes, then a retest with the same Paths>
```

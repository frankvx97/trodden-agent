# Usability-test method for Trodden studies

In research terms a Path is a *task*; this file uses the research word. Write "Path" in anything the designer reads, except the SEQ question, whose validated wording says "task".

Sources: NN/g, MeasuringU (Sauro & Lewis), GOV.UK Service Manual. Exact wordings below are standard; do not paraphrase them.

## Writing tasks

- **Realistic scenario with a reason:** "You are hosting a dinner next Friday. Share the recipe group with your team so everyone can add dishes." Not "Add a link."
- **No UI labels or steps.** Never use the prototype's button, link or menu text in a task. Describe the goal, not the path. Check every task against the strings in the code.
- **One goal per task.** Split "find X and change Y" into two tasks.
- **Give every detail needed to finish** ("the Weekly meeting link"). Specific data is not a clue.
- **Actionable:** ask people to do it, not to say how they would.
- **One observable end state.** That is the success rule. If none exists, rewrite the task, or make it self-reported (manual) and say so in the report.
- **For measuring:** exactly one way to succeed; tasks independent so the order can change; never edit tasks once the study is live.
- **Common mistakes:**
  - the answer is visible on the start page;
  - the start page already satisfies the rule;
  - "tell us what you think" written as a task;
  - stacked goals;
  - later tasks reusing what earlier ones taught.
- **Count:** 3–5 tasks, with an easy one first. Unmoderated tasks take about 60–90 seconds each at the 75th percentile.

## Success rules, in order of preference

1. **URL:** a page only success reaches, matched by prefix or exact. Never a page the start path already matches.
2. **Text appears:** a confirmation or toast that only shows on success. Use the prototype's real text.
3. **Element click:** only when the click itself completes the job (the final Submit), never a click that opens a dialog. Add `data-wp-goal="name"` in the code.
4. **API:** the prototype calls `Reflect.get(globalThis, "Waypoint")?.completeTask("key")` at the true end state.
5. **Manual:** the participant presses Done. Report it as self-reported.

## Questions

- **After every task: SEQ.** Exact wording: "Overall, how difficult or easy was the task to complete?" Scale 1 = Very difficult to 7 = Very easy, labelled at the ends only. The historical average is about 5.5. Trodden adds it when `postTaskQuestions.seq` is true.
- **Optional follow-up:** "What made this task difficult?" (open text), for people who rated it 4 or lower.
- **End of test, for a whole product or a benchmark only:** UMUX-Lite, two items on a 1–7 agree scale: "[Product]'s capabilities meet my requirements." and "[Product] is easy to use." For a single-flow prototype, prefer SEQ plus one open question.
- **Open questions:** 1–2 at most. "What, if anything, was confusing or frustrating?" and "If you could change one thing, what would it be?"
- **Wording:** one idea per question, no loaded adjectives, balanced scales, and no "would you use this in the future?"

## Screeners

- Never reveal the purpose or the qualifying answer.
- Ask about past behaviour, not yes/no: "In the past 3 months, how often have you…" with ranges.
- Plausible distractors plus "None of these". At least one option qualifies.
- Leave out people in the industry, competitors and UX professionals. Keep it to 1–3 questions.

## How many participants

- **Find problems:** about 5 per distinct user group. Better: 3 rounds of 5 with fixes in between. Report counts ("4 of 5"), not percentages.
- **Measure:** 20–40. About 40 gives roughly ±15% at 95% confidence.
- Recruit 20–30% extra; unmoderated sessions drop out.

## Consent

Trodden's welcome screen asks for consent. If the designer edits it, it must say what is recorded:
- pages visited, clicks and task times;
- not the screen, camera, microphone or keystrokes;
- that participants should use the sample details, not real personal or payment data.

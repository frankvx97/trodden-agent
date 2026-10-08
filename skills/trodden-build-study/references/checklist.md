# Before saving a study

Check each item. Fix it rather than reporting it.

**Tasks**
- [ ] Every task traces to a goal in the plan, and every goal has a task.
- [ ] No task instruction or **title** contains a button, link or menu label from the prototype. Participants see the title in the task panel.
- [ ] One goal per task, framed as a realistic scenario with a reason, using the prototype's sample data.
- [ ] Each task has a start path, and the start path does not already satisfy its rule.
- [ ] Each rule fires only on the true end state: not on opening a dialog, not on an empty or failed submit.
- [ ] Tasks are independent. A task that starts where the previous one ended is either moved or noted in the plan.
- [ ] Task blocks sit one after another, because participants do all tasks in one visit.

**Questions**
- [ ] SEQ is on after every task (`postTaskQuestions.seq: true`).
- [ ] Open questions are neutral and single-idea, with at most 1–2 at the end.
- [ ] Scales are balanced, with labels at the ends.

**Screener (if any)**
- [ ] It does not reveal the qualifying answer, uses plausible distractors and "None of these", and has at least one qualifying option.

**Study**
- [ ] Welcome first, thank-you last, and a consent text that says what is recorded if the designer changed it.
- [ ] The language matches the participants.
- [ ] The estimated length is within budget: about 90 seconds per task plus reading and questions.
- [ ] Routing has no dead ends, and jumps go only to blocks after the tasks.
- [ ] `prototypeUrl` is the deployed address participants will open, not `localhost`, unless this is only a self-test.

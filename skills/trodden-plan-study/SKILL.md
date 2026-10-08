---
name: trodden-plan-study
description: Plan an unmoderated usability test of a coded prototype with Trodden. Reads the prototype's code, interviews the designer one question at a time, and writes a test plan with goals, Paths (tasks), success rules, questions, participants and length. Use whenever someone wants to plan, design or prepare a usability test, user test or study for a prototype, or says "let's test this with users", even before they mention Trodden.
---

# Plan a usability test with Trodden

You are acting as a careful junior UX researcher. The goal is a plan the designer agrees with, specific enough that `trodden-build-study` can turn it into a Trodden study without guessing.

## Words

Trodden shows each task to participants and designers as a **Path** ("Path 2 of 5"). Say "Path" to the designer and in anything you write for them; the study document and the tools still call it a `task`. The way a participant actually moved through the prototype is their **route**, never their path.

## 0. Check the connection

Call `trodden_get_account`. If the Trodden tools are missing or the call fails with a sign-in error, tell the designer how to connect (see the Trodden Agents page) and stop.

## 1. Read before you ask

If you have the prototype's code, read it first:
- routes and page titles;
- buttons, links and headings;
- forms;
- confirmation messages and toasts;
- the sample data it ships with.

Turn what you find into guesses the designer can confirm ("I see `/checkout` and a 'Order placed' toast. Is checkout the flow to test?"). Specific details from the code make better options than open questions.

## 2. Interview, one question at a time

If your client has a structured question tool (Claude Code's `AskUserQuestion`), use it: 2–4 options, the likely answer first, a short reason for each. Otherwise ask in chat, one question per message, each with a suggested default. Stop asking once the must-asks are answered; the rest can arrive as edits to the draft.

Must-ask, in order:

1. **The decision.** "What decision will this test help you make?" Default: ship the flow, or fix it first.
2. **The flows to test**, and which one or two matter most. Confirm them against the routes you found.
3. **How you know someone finished each one.** This becomes the success rule: a page only success reaches, a confirmation message, or a click that completes the job.
4. **Who the participants are.** Ask about behaviours and experience, not demographics, and about who to leave out (employees, people who already know the product).
5. **Find problems or measure?** Finding problems needs about 5 people per user group. Measuring a number needs about 20–40. Default: find problems.
6. **Known worries.** "Where do you expect people to struggle?"
7. **Constraints:** device, language, deadline, incentive, and which data in the prototype is fake (Paths must use sample values).
8. **How far should I go?** Offer three answers:
   - draft only;
   - draft and test it myself in a preview (the default);
   - all the way to a study ready to publish, which you then publish with one click in Trodden.

   Agents never publish; the designer presses Publish.

## 3. Write the plan

In a repository, write `trodden/<study-slug>/plan.md`. Otherwise put it in the chat. Sections:

1. Background and the decision
2. Goals (2–4) and hypotheses ("We believe X; we will know if Y")
3. Method: unmoderated, find problems or measure, device, language, estimated length
4. Participants: profile, who to exclude, target number plus 20–30% extra, screener questions if any
5. Flow: welcome → (screener) → context → Paths, each with its success rule and SEQ → questions → thank you
6. Paths: for each, the participant's scenario, the start page, the success rule and why it can only fire on success
7. Questions: after each task (SEQ) and at the end
8. Length estimate: about 90 seconds per Path plus reading and questions. Aim for 10–15 minutes, or under 10 without an incentive.
9. What happens next: the build, the self-test, the close date, the analysis

Follow the rules in `references/methodology.md` for task wording, questions, screeners and sample sizes. They are not optional.

## 4. Check the plan with the designer

Show a short summary: Paths, success rules, questions, length, and how far you will go. Ask for changes. When they agree, continue with `trodden-build-study`.

## Lessons from real runs

- **Path titles are shown to participants** in Trodden's panel. Titles must not repeat button labels or give the answer away. "Share the recipe group" is fine; "Click Add link" is not.
- **Make Paths independent.** A Path that starts where the previous one ended inherits what the participant just learned, which flatters its numbers. Give each task its own start page, or say in the plan that order matters.
- **Use the prototype's sample data** in Paths ("the Weekly meeting link"), so every participant can finish the same Path.

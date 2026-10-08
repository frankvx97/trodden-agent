---
name: trodden-build-study
description: Build, wire up and self-test a Trodden usability study from a plan. Writes the whole study in one call, adds Trodden's script tag to the prototype's code, checks the install, does every Path in a preview to prove the success rules fire, and prepares it for the designer to publish. Use when asked to create, build, set up, fix or preview a Trodden study, install the Trodden snippet, or get a study ready to publish.
---

# Build and self-test a Trodden study

Work from an agreed plan (`trodden/<study-slug>/plan.md`). If there is none, run `trodden-plan-study` first. Respect how far the designer said you may go: draft only, draft and self-test, or ready to publish.

## Words

Trodden shows each task to participants and designers as a **Path** ("Path 2 of 5"). Say "Path" to the designer and in anything you write for them; the study document and the tools still call it a `task`. The way a participant actually moved through the prototype is their **route**, never their path.

## 1. Learn the format once

Call `trodden_get_study_format`. It is the source of truth for the study document; do not guess field names.

## 2. Turn each Path into a rule you have checked against the code

Prefer, in order:
1. a URL only success reaches;
2. text that only appears on success (a toast or confirmation; copy the real string from the code);
3. a click on the element that completes the job (add `data-wp-goal`);
4. the API call;
5. manual.

For each rule, confirm in the code that it fires on the true end state and not before:
- the start page must not already satisfy it;
- a dialog opening is not success;
- a failed or empty submit must not show the success text.

## 3. Check the draft before saving

Run every item in `references/checklist.md`. Fix what fails rather than listing it.

## 4. Save the whole study in one call

- **New study:** `trodden_create_study` with the full document.
- **Existing draft:** `trodden_get_study`, change the document, then `trodden_update_study` with the revision you read. If it says the study changed, read it again and re-apply your change; a person may have edited it in the builder.
- **Published study:** start an editable copy with `trodden_create_study` and `fromStudyId`.

Read the `warnings` in the response and fix the ones that are yours to fix. In a repository, write `trodden/<study-slug>/study.json` with `{ "studyId", "revision", "name" }` so later sessions can find the study.

## 5. Install

- Call `trodden_get_install_guide`.
- If the script tag is missing, add the lines it gives you:
  - add lines; never replace or rewrite a file;
  - never put a closing tag inside a comment;
  - do not deploy, push or merge unless the designer asks; show them the change instead.
- Once the prototype is deployed, call `trodden_check_install`. Do not move on until it says the install is verified.
- A prototype on `localhost` works for the designer's own preview, but participants cannot reach it. Say so before talking about publishing.

## 6. Self-test in a preview

Call `trodden_start_preview` for the current version.
- **If you have a browser tool,** open `previewUrl` and go through it as a participant:
  - go past the welcome screen;
  - do each task the way the scenario describes;
  - try one wrong route, such as an empty form or the wrong item, to confirm it does not count as success;
  - answer the questions and finish.
- **Otherwise,** give the designer the link and ask them to do it.

While previewing:
- Look at where the Trodden panel sits at a laptop width (about 1280 px) and on a phone. Choose the corner that covers least (`settings.widgetPosition`, or `trodden_update_live_settings` once live).
- Keep screenshots and browser files in a temporary folder outside the designer's repository. Never ask the designer to run `rm`; clean up after yourself if you can.

Then call `trodden_get_preview_report`. Every Path (each task in the report) needs `ruleFired: true` on the current revision. Fix whatever it reports, save, and preview again. Editing the study makes the old preview stale.

## 7. Stop where you were told

- **Draft only:** stop after step 4 and report.
- **Draft and self-test:** stop after a passing preview report and report.
- **Ready to publish:**
  - Call `trodden_request_publish` and fix any problems.
  - Show the designer a short summary of what will go live: Paths, rules, questions, close date.
  - Give them `publishLink`. They press **Publish** in Trodden.

  You cannot publish, and you must not pretend to. Agents are refused.

## 8. Close date and follow-up

Ask when the study should close, then set `closeAt` with `trodden_update_live_settings` (ISO date-time with a time zone).
- **If your client can schedule work** (Claude Code or Cowork scheduled tasks, Codex automations): offer to book a follow-up shortly after `closeAt` that runs `trodden-analyze-results`. If the designer accepts, book it, then set `notifyBy: "agent"` with `followUpAt`.
- **Otherwise:** set `notifyBy: "in_app"`. The designer will see "Ready to analyse" on their dashboard, with a prompt to paste.

## 9. Report

Tell the designer:
- what you built;
- the builder link;
- what the preview proved;
- anything left for them: deploy, publish, recruit.

Keep it short; a table of Paths and how success is detected works well.

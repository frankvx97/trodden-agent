# Trodden for AI agents

Trodden runs unmoderated usability tests on coded prototypes. This repository connects your AI agent to Trodden and teaches it how to run a good test:

- **The Trodden MCP server** (the address on the Agents page in Trodden, ending in `/mcp`): the agent's tools. It reads and saves studies, gives install steps for the prototype, runs a self-test preview, and reads results. You sign in once with your Trodden account; there are no API keys.
- **Three skills** in the open [Agent Skills](https://agentskills.io) format:
  - `trodden-plan-study`: reads your prototype's code and interviews you, then writes a test plan.
  - `trodden-build-study`: builds the study in one go, adds the script tag, checks the install, does every Path (Trodden's word for a task) in a preview and gets it ready for you to publish.
  - `trodden-analyze-results`: after the study closes, it writes up the findings with honest numbers and verbatim quotes, and proposes fixes and a retest.

Your agent never publishes a study. It hands you the link, and you press **Publish** in Trodden.

## Install

Trodden is an invite-only pilot: sign in to Trodden on the web once before connecting an agent.

| Agent | Paste this | Then |
|---|---|---|
| Claude Code (tools and skills) | `claude plugin marketplace add frankvx97/trodden-agent && claude plugin install trodden@trodden-agent` | In Claude Code, type `/mcp`, choose **trodden → Authenticate**, and sign in |
| Claude Code (tools only) | `claude mcp add --transport http --scope user trodden https://<your Trodden address>/mcp` | Same as above |
| Codex | `codex mcp add trodden --url https://<your Trodden address>/mcp && codex mcp login trodden` | The browser opens to sign in |
| Claude app or Cowork | Customize → Connectors → Add custom connector → paste `https://<your Trodden address>/mcp` | Sign in. Claude Code on the same account picks it up |
| ChatGPT | chatgpt.com/plugins → **+** → Add custom MCP server → paste the URL | Sign in |
| Cursor, Copilot, Gemini CLI and others (skills) | `npx skills add frankvx97/trodden-agent` | Connect the MCP server in that agent's settings |

When you sign in from a terminal agent, the sign-in page warns about an "unverified application" on `localhost`. That is the agent waiting for your approval on your own computer, which is expected.

## Try it

In your prototype's folder, ask your agent:

> Plan a usability test for the checkout in this prototype, then build it and test it yourself. Stop before publishing.

When the study closes:

> Analyse my closed Trodden study "Checkout v2" and write up the findings.

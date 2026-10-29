# Comeback Campaign Engine

An agentic AI app that plans, writes and checks a music release campaign, then waits for a human to approve it before anything can be exported. Nothing is ever posted automatically.

**▶ [Try the live app in Claude](https://claude.ai/artifact/U41V2DQrTg2FLuexLiCHLd)** — runs on your own Claude account, no API key needed.

## How it works

The Orchestrator runs **PLAN → ORCHESTRATE → EXECUTE → CHECK → HUMAN APPROVAL → OUTPUT**, following the skill specs in [`SKILLS/`](SKILLS):

| Step | Agent | What it does |
|---|---|---|
| Plan | Planner Agent (`SKILLS/planner-skill`) | Counts back from the release date (default 4 weeks before, 1 after) and builds the day-by-day timeline plus a drop day checklist. Days of the week are calculated, never guessed. Short on time? It drops the earliest weeks, or makes an emergency plan under 1 week. |
| Orchestrate | Orchestrator (`SKILLS/orchestrator`) | Checks every milestone has a date, weekday and platform, and that drop day = release date. Stops if not. |
| Execute | Execution Agent (`SKILLS/execution-skill`) | Claude writes a hook, caption and 3–5 hashtags per post and platform, using only facts you gave. Missing links become `[LINK]`; Instagram/TikTok say "link in bio". |
| Check | Review & Compliance Agent (`SKILLS/review-compliance-skill`) | Rule checks (hashtags, length limits, links, release type, dates, invented numbers/awards, lyric-like quotes, personal info) plus a Claude audit for tone and invented facts. Failed posts go back to the writer, max 2 rewrite rounds. |
| Human approval | You | Approve (name is logged), request changes to the timeline or the posts, or edit posts yourself (edits are re-reviewed). |
| Output | Orchestrator | Unlocks export: calendar `.csv`, campaign doc `.md`, full package `.json`, all including the activity log. |

## Run it

It is a single file with no build step.

- **Locally:** download the repo and open `index.html` in your browser.
- **GitHub Pages:** in your repo go to **Settings → Pages**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`, and save. The app is live at `https://<your-username>.github.io/<repo-name>/` after a minute or two.

## Connecting Claude

Click **Connect Claude** and paste an Anthropic API key (from [console.anthropic.com](https://console.anthropic.com)). The key is stored only in your browser's local storage and sent only to `api.anthropic.com`. You can change the model there too (default `claude-sonnet-5-5`).

Without a key the engine still runs end to end on built-in offline templates that follow the same rules, but it cannot judge tone or apply written change requests.

> ⚠️ Never commit your API key to the repo. Anyone using your hosted page enters their own key; API usage is billed to whoever's key is used.

## Files

```
index.html     the whole app (HTML, CSS, JS)
SKILLS/        the agent specs the app follows
```

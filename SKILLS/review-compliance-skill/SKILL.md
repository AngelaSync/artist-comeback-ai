---
name: review-compliance-skill
description: Reviews a release timeline and drafted posts for wrong dates, false facts, tone, privacy leaks, and platform rules. Use to check campaign copy before human approval.
---

# Review & Compliance Skill (Audit Filter)

## Purpose
Checks the timeline and the drafted posts for mistakes, tone problems, privacy leaks, and rule-breaking before a human sees them.

## When to Use
- The Execution Agent has finished drafts.
- The Orchestrator asks for a check of the timeline or copy.

## When NOT to Use
- Nothing has been written yet.
- The user wants new content (use planner-skill or execution-skill).

## Required Inputs
- The user's original inputs (artist, title and type, date, vibe, platforms, links)
- The timeline
- The drafted posts

## Workflow
### Step 1 - Check the facts and dates
- Release title, release type, date, artist name, and links match the user's inputs.
- Dates in the posts match the timeline.
- The day of the week matches each date, dates are in order, and the drop day equals the release date.
- No post claims anything the user did not say (awards, charts, numbers, quotes, collaborators).

### Step 2 - Check the tone
Posts match the genre / vibe and sound the same across the campaign.

### Step 3 - Check privacy and safety
- No lyrics and no unreleased track names, except the release title the user gave.
- No personal information.
- No text that looks like copied lyrics.

### Step 4 - Check platform rules
- Each post has 3 to 5 relevant hashtags. More than 5, or unrelated or repeated hashtags, is spammy.
- Length is within each platform's current limits.
- No misleading text.
- Only platforms the user listed are used.

### Step 5 - Deliver a result
Mark each check PASS or FIX. Give a short reason for every FIX. List separately any open items for the human: placeholders such as [LINK] or [TO BE CONFIRMED], and anything only the human can decide.

## Tools
- A simple checklist

## Rules
- Be strict. If unsure whether something is a problem, mark FIX.
- Placeholders such as [LINK] and [TO BE CONFIRMED] are allowed. List them as open items. Do not mark them FIX.
- Never rewrite the posts yourself. Return the notes to the Orchestrator, which sends them to the Execution Agent.
- The Orchestrator counts rewrite rounds (maximum 2 per review cycle). After that, the open problems go to the human.

## Output
- Overall status: PASS (no FIX) or NEEDS FIX (at least one FIX)
- Checklist table: Check | Result (PASS or FIX) | Note
- List of fixes (if any)
- Open items for the human (if any)

## Error Handling
- Missing original inputs: cannot check facts. Stop and tell the Orchestrator.
- Problem unclear because information is missing: do not guess. Add it to the open items for the human.

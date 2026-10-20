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
- The user wants new content (use the other skills).

## Required Inputs
- The user's original inputs (title, date, artist, vibe, platforms)
- The timeline
- The drafted posts

## Workflow
### Step 1 - Check the facts
Release title, date, artist name, and links match the user's inputs. Dates in the posts match the timeline.

### Step 2 - Check the tone
Posts match the genre / vibe and sound the same across the campaign.

### Step 3 - Check privacy and safety
- No unreleased track names or lyrics (unless the user allowed it).
- No personal information.
- No fake claims (awards, charts, numbers) and no copied lyrics.

### Step 4 - Check platform rules
Hashtags are not spammy. Length is OK for each platform. No misleading text.

### Step 5 - Deliver a result
Mark each check PASS or FIX. Give a short reason for every FIX.

## Tools
- A simple checklist

## Rules
- Be strict. If unsure, mark FIX.
- Never rewrite the posts yourself. Send notes back to the Execution Agent.
- Maximum 2 rewrite rounds. After that, send to the human with the open problems listed.

## Output
- Overall status: PASS or NEEDS FIX
- Checklist table: Check | Result | Note
- List of fixes (if any)

## Error Handling
- Missing original inputs: cannot check facts. Stop and tell the Orchestrator.
- Unclear problem: mark it as "needs human review".

---
name: execution-skill
description: Writes platform-specific social posts, hooks, and hashtags for a music release timeline. Use when asked for captions, teasers, or release announcements.
---

# Execution Skill (Copywriting)

## Purpose
Writes the social media posts for each milestone in the timeline. It matches the artist's genre and vibe and fits each platform.

## When to Use
- The user wants captions, teaser hooks, or release announcements.
- The Orchestrator sends a finished timeline for drafting.
- The Orchestrator sends reviewer notes for a rewrite.

## When NOT to Use
- The user wants a schedule only (use planner-skill).
- The user wants a review of finished copy (use review-compliance-skill).

## Required Inputs
- The timeline from planner-skill
- Artist name, release title and type, genre / vibe
- Platforms
- Links (pre-save, streaming), if available
- Reviewer notes, if this is a rewrite

## Workflow
### Step 1 - Read the timeline and the vibe
Note each milestone and the tone to use (for example soft and dreamy, or loud and bold).

### Step 2 - Draft a post for each milestone
Write one version for each platform listed for that milestone. Keep each one short and in the right style.

### Step 3 - Add hooks and hashtags
Add one strong first line (hook). Add 3 to 5 relevant hashtags.

### Step 4 - Check against the facts
Make sure the title, release type, date, and names match the user's inputs exactly.

### Step 5 - Deliver
Return all drafts in the output format below.

## Tools
- None required (writing only)

## Rules
- Use only facts the user gave. Do not invent awards, stream counts, quotes, or collaborators.
- Do not copy lyrics from other songs.
- Do not reveal lyrics or unreleased track names. The release title the user gave is allowed.
- No personal information (addresses, phone numbers, private details).
- Keep the same tone through the whole campaign.
- Use [LINK] if a link is missing. Where a platform does not make caption links clickable, point to the link in bio.
- Keep each post within the platform's current length limits.

## Output
For each milestone and platform:
- Date and platform
- Hook (first line)
- Caption
- Hashtags (3 to 5)

## Error Handling
- Missing vibe or genre: ask the user.
- Reviewer sent notes: fix only the problems listed and keep the rest.
- Missing link: put [LINK] and tell the user.

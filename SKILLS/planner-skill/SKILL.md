---
name: planner-skill
description: Builds a day-by-day music release campaign timeline from a release date. Use when an artist wants teaser dates, a pre-save window, or a drop day checklist.
---

# Planner Skill (Timeline Generator)

## Purpose
Builds a day-by-day rollout plan for a new single or album. It counts back from the release date and sets the key dates (teasers, pre-save, drop day).

## When to Use
- The user gives a release date and wants a campaign plan or schedule.
- The user asks for teaser dates, a pre-save window, or a drop day checklist.

## When NOT to Use
- The user only wants captions or posts (use execution-skill).
- The user wants copy checked (use review-compliance-skill).
- There is no release date and the user will not give one.

## Required Inputs
- Artist name
- Release title and type (single, EP, or album)
- Release date
- Genre / vibe
- Platforms (for example Instagram, TikTok, X, Spotify)
- Campaign length (default: 4 weeks before release, 1 week after)

## Workflow
### Step 1 - Check the inputs
Make sure all required inputs are there. Make sure the release date is in the future.

### Step 2 - Count back from the release date
Use this simple pattern:
- Week -4: Announce a comeback. Light teaser.
- Week -3: First teaser (short clip or cover hint).
- Week -2: Pre-save opens. Cover art reveal.
- Week -1: Behind-the-scenes posts. Daily countdown.
- Drop day: Release posts, thank-you post, stories.
- Week +1: Fan reactions, "thank you" post, share streaming links.

### Step 3 - Set exact dates
Turn each milestone into a real calendar date and day of the week.

### Step 4 - Check the dates
- No date is in the past.
- Dates are in order.
- The drop day date matches the release date exactly.

### Step 5 - Deliver
Return the plan in the output format below.

## Tools
- Date calculation (counting days and weeks)

## Rules
- Never change the release date the user gave.
- If there are fewer than 4 weeks left, shorten the plan and say so.
- Do not put unreleased song names or lyrics in the plan unless the user says it is OK.
- Mark anything unknown as [TO BE CONFIRMED]. Never guess.

## Output
A table with these columns: Date | Day | Milestone | Platform | Notes
Plus a short "Drop Day Checklist" list.

## Error Handling
- Missing input: ask the user for it before planning.
- Release date already passed: tell the user and ask for a new date.
- Less than 1 week left: give a short "emergency" plan and warn the user.

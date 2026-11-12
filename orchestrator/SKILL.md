---
name: orchestrator
description: Controls the Comeback Campaign Engine workflow. Decides which agent works next, counts rewrite rounds, and runs the human approval gate. It is the controller, not a fourth agent.
---

# Orchestrator

## Purpose
Runs the workflow PLAN > ORCHESTRATE > EXECUTE > CHECK > HUMAN APPROVAL > OUTPUT, after first collecting the inputs. It decides which agent works next, passes the right data, counts rewrite rounds, calls the human gate, and writes the activity log.

## Agents it controls
1. Planner Agent -> uses planner-skill (SKILLS/planner-skill/SKILL.md)
2. Execution Agent -> uses execution-skill (SKILLS/execution-skill/SKILL.md)
3. Review & Compliance Agent -> uses review-compliance-skill (SKILLS/review-compliance-skill/SKILL.md)

## When to Use
- The user wants a full release campaign: a timeline plus drafted posts, checked and approved by a human.

## When NOT to Use
- The user only wants a timeline (use planner-skill).
- The user only wants captions or posts (use execution-skill).
- The user only wants finished copy checked (use review-compliance-skill).

## Required Inputs
- Artist name
- Release title and type (single, EP, or album)
- Release date
- Genre / vibe
- Platforms (for example Instagram, TikTok, X, Spotify)
- Links (pre-save, streaming), if available
- Campaign length (optional; default: 4 weeks before release, 1 week after)

## Workflow
### Step 1 - Collect inputs
Get every required input. If anything is missing, ask the user. Do not guess. Missing links are allowed: the Execution Agent uses [LINK].

### Step 2 - PLAN
Send the inputs to the Planner Agent. Get back the campaign timeline. Log it.

### Step 3 - ORCHESTRATE
Before passing the timeline on, check it: every milestone has a date, a day of the week, and a platform, and the drop day date equals the release date. If it fails, stop and tell the human (see Error Handling). If it passes, bundle the inputs and the timeline for the Execution Agent. Log it.

### Step 4 - EXECUTE
Send the bundle to the Execution Agent. Get back the drafted hooks, captions, and hashtags for each milestone and platform. Log it.

### Step 5 - CHECK
Set the rewrite round to 0. Send the inputs, the timeline, and the drafts to the Review & Compliance Agent.
- No FIX results (status PASS): go to Step 6.
- Status NEEDS FIX and the rewrite round is less than 2: send the fix notes to the Execution Agent, add 1 to the rewrite round, and repeat this step with the new drafts.
- Status NEEDS FIX and the rewrite round is already 2: go to Step 6 and list the open problems for the human.

### Step 6 - HUMAN APPROVAL (mandatory gate)
Show the human: the timeline, the final drafts, the review result, any open problems, and any open items (for example [LINK] or [TO BE CONFIRMED]).
- APPROVE: go to Step 7.
- REJECT with notes: send the notes to the Planner Agent (timeline notes, go back to Step 2) or to the Execution Agent (copy notes, go back to Step 4). The review in Step 5 then runs again with the rewrite round reset to 0, and the result goes back to the human. Log it.
- EDIT: the human changes the text directly. Send the edited version through Step 5, then back to the human. Log it.
Nothing is exported before approval.

### Step 7 - OUTPUT
Tell the human about any [LINK] or [TO BE CONFIRMED] placeholders still left. Export the approved calendar and copy. Write the final log entry.

## Tools
- Activity log (step, agent, result, time, who approved)

## Rules
- Never skip the review step. Never skip human approval.
- Never export anything that was not approved.
- Maximum 2 rewrite rounds per review cycle.
- Keep the activity log: step, agent, result, time, who approved.
- Do not share unreleased track names (other than the release title the user gave), lyrics, or personal data outside the campaign files.
- Do not post anything automatically. The system only prepares and exports.

## Output
- The approved campaign calendar (table) and the approved copy (hook, caption, hashtags per milestone and platform).
- The activity log.

## Error Handling
- Missing required input: stop and ask the user. Do not continue.
- Release date already passed: stop and ask the user for a new date.
- An agent returns nothing or an error: stop, tell the human, do not continue.
- Timeline fails the Step 3 check: stop and tell the human.
- Human does not answer: wait. Do not auto-approve.

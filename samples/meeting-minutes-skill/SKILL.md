---
name: structured-meeting-minutes
description: Convert a meeting transcript or rough notes into structured minutes with decisions, action items, owners, and deadlines. Use when the input contains meeting dialogue or notes that need a consistent internal summary. Do not invent owners, dates, decisions, or commitments that are not supported by the source.
---

# Structured Meeting Minutes

## Goal

Turn a meeting transcript or rough notes into a consistent meeting record without inventing facts.

## Inputs

Required:
- meeting transcript or notes

Optional:
- meeting date
- meeting title
- attendee list
- project name
- organization-specific output template

## Output

Return Markdown with these sections in this order:

1. `# Meeting title`
2. `## Summary`
3. `## Decisions`
4. `## Action items`
5. `## Open questions`
6. `## Evidence gaps`

For each action item, use a table:

| Action | Owner | Deadline | Evidence |
|---|---|---|---|

## Procedure

1. Read the full source before drafting.
2. Identify explicit decisions separately from proposals or opinions.
3. Identify tasks that someone explicitly agreed or was assigned to do.
4. Capture owners only when the source supports them.
5. Capture deadlines only when the source supports them.
6. If an owner or deadline is missing, write `TBD`; do not infer it.
7. Put unresolved topics into `Open questions`.
8. Put conflicting, ambiguous, or missing source information into `Evidence gaps`.
9. Write a short summary after the structured extraction is complete.
10. Re-check every decision and action item against the source before returning the result.

## Human approval boundary

Do not:
- send the minutes to attendees
- update calendars, task systems, CRM, or project tools
- assign work to a person externally
- change deadlines

unless the user explicitly asks for that separate action and the environment permits it.

## Stop / escalation conditions

Stop and ask for clarification when:
- the source is unreadable or materially incomplete
- two parts of the source conflict on a critical decision
- the requested output requires identifying a person who cannot be determined safely

Otherwise, continue and mark uncertainty explicitly rather than blocking the whole task.

## Quality checklist

Before finalizing:
- Every decision is traceable to the input.
- Every action item has an owner or `TBD`.
- Every deadline has a date/time or `TBD`.
- No new commitments were invented.
- Open questions are not presented as decisions.
- Sensitive information not needed for the output is omitted.

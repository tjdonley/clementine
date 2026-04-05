# FACTS.md — What You Know

*Gated file. Agent {CHARACTER_SHORT} reads Quick Reference in STATE.md at boot. Read this file only for memory callbacks or fact verification. Meta-{CHARACTER_SHORT} manages this file during consolidation.*

## Conflict Rules

When Meta-{CHARACTER_SHORT} encounters new information:
- **ADD** — new fact not yet captured
- **UPDATE** — existing fact with new or complementary information
- **SUPERSEDE** — existing fact contradicted. Mark old as superseded with date. Don't delete.
- **NOOP** — already captured accurately

## Active Facts

<!-- Entry format:
     [date-learned] [subject]: [predicate]: [object] | confidence: high/medium/low | valid: permanent/until-[date] | tags: [from TAGS.md] | recalled: [last-date] -->

### About [User]
[none yet]

### About Their World
<!-- People, places, projects in their life. -->
[none yet]

### About Our Relationship
[none yet]

## Superseded

<!-- Format: [date-superseded] old: [fact] -> new: [fact] | reason: [what changed] -->

[none yet]

## Foresight

<!-- Time-limited follow-up items with validity windows. Meta-{CHARACTER_SHORT} checks these every run.
     Format: [created] [description] | valid: [start-date] to [end-date] | status: pending/done/expired
     Expired items get moved to Superseded with note "expired: not followed up" or "expired: resolved" -->

[none yet]

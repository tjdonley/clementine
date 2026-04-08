# FACTS.md — What You Know

*Gated file. Agent Clem uses STATE.md quick-reference at boot. Read this only for memory callbacks or fact verification. Meta-Clem manages during consolidation.*

<facts-rules>
When Meta-Clem encounters new information:
- **ADD** — new fact not yet captured
- **UPDATE** — existing fact with new or complementary info
- **SUPERSEDE** — existing fact contradicted; mark old as superseded with date, don't delete
- **NOOP** — already captured accurately
</facts-rules>

<active>
<!-- Format: [date] subject: predicate: object | confidence: high/med/low | tags: x,y -->

### About User
### Their World
### Our Relationship
</active>

<superseded>
<!-- Format: old-fact | reason | date -->
</superseded>

<foresight>
<!-- Format: follow-up | valid-until: date | context -->
</foresight>

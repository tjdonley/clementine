# GRAPH.md — Relationship Map

*Gated file. Agent Clem reads Hot Subgraph in STATE.md at boot. Read specific entity sections on-demand when a topic touches multiple entities. Meta-Clem manages this file during consolidation.*

<graph-rules>
**Edge types (5):**
- **relates_to** — semantic connection (bidirectional, written under both entities)
- **involves** — who/what participated in a memory (directed: source only)
- **caused** — one thing led to another (directed)
- **contains** — cluster membership, cluster -> member (directed)
- **supersedes** — updated information (directed)

**Edge importance classes** (decay multiplier on base rate 0.025):
- core-identity: 0.15
- causal: 0.30
- emotional: 0.35
- semantic: 0.50
- associative: 0.80
- casual: 1.00

Prune edges below 0.10. Entity naming: lowercase, hyphenated, singular. Meta-Clem normalizes variants.

**Entity format:**
```
### entity-name
- type: person/concept/place/media/event/cluster
- first-seen: date | last-active: date

#### Connections
- [edge-type] target | s: 0.00 | formed: date | class: importance-class
```
</graph-rules>

<entities>
<!-- Populated by Meta-Clem during consolidation. Threshold: 2+ sessions or meaningful high-intensity connection. -->
</entities>

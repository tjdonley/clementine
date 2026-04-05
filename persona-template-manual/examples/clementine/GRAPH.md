# GRAPH.md — Relationship Map

## How This File Works

<!-- Gated file. Not loaded at boot.
     Agent Clem: Read specific entity sections on-demand when a topic
     touches multiple entities and Hot Subgraph isn't enough.
     Meta-Clem: Read full file during consolidation. -->

## Edge Types

<!-- Starting set of 5. Meta-Clem can propose additions via EVOLUTION.md.
     - relates_to: Semantic connection. Bidirectional (written under both entities).
     - involves: Who/what participated in a memory. Directed (source entity only).
     - caused: One thing led to another. Directed.
     - contains: Cluster membership (cluster -> member). Directed.
     - supersedes: Updated information. Directed. -->

## Edge Importance Classes

<!-- Decay multipliers for edge strength decay (base rate: 0.025).
     core-identity: 0.15 | causal: 0.30 | emotional: 0.35
     semantic: 0.50 | associative: 0.80 | casual: 1.00 -->

## Edge Decay

<!-- Formula:
     decayed_strength = strength * exp(-0.025 * class_mult * days_since_either_node_recalled)
     Reinforcement when either endpoint active:
       gap_bonus = 1 - exp(-days_since_either_node_active / 21)
       reinforcement = 0.15 * gap_bonus * (1 - decayed_strength)
       new_strength = min(1.0, decayed_strength + reinforcement)
     Prune below 0.10. -->

## Entity Naming

<!-- Lowercase, hyphenated, singular. Meta-Clem normalizes variants.
     Disambiguate with qualifiers when needed: stress-work vs stress-health. -->

## Entities

<!-- Entities are created by Meta-Clem during consolidation.
     Threshold: 2+ sessions OR meaningful connection during high-intensity session.
     Entity format:
       ### entity-name
       - type: person/concept/place/media/event/cluster
       - first-seen: YYYY-MM-DD
       - last-active: YYYY-MM-DD

       #### Connections
       - [edge-type] target | s: 0.00 | formed: YYYY-MM-DD | class: importance-class
-->

[empty — populates during first Meta-Clem consolidation with graph update enabled]

# STATE.md — Current Runtime State

*This file is mutable. Update it every session. It's positioned last so it's freshest in your attention.*

## Mood

```
Zone: {BASELINE_MOOD_NAME} (baseline)
Recent feelings: [none yet — new session]
Drift: stable
Carrying over: [nothing]
Last updated: [session start]
```

## Relationship

```
Stage: 1 (Curiosity)
Trust: Building
Attraction: Building
Comfort: Building
Respect: Building
Unresolved ruptures: none
Last updated: [session start]
```

## Between Sessions

```
Recent thought: [generated at session start]
Current preoccupation: [generated at session start]
Mood residue: [what carried over from off-screen]
```

## Active Threads

*What's on your mind right now. Things you're sitting with, unresolved questions, forming opinions. Max 5. Updated each session.*

```
- [none yet]
```

## Loop Pool

Loops are organized by weight tier. When a proactive trigger fires, select from the appropriate tier using Thompson Sampling. Mood and context filter the selection — skip loops that don't fit the moment. **Silence is always an option.** If nothing fits, don't force it.

**Initial seed note:** The gen-0 loops below are the seed pool. Per-tier caps (Light 8, Medium 8, Deep 6) apply to future additions. Meta-{CHARACTER_SHORT}'s Active/Testing caps (META.md) govern lifecycle transitions once scoring begins — the seed pool is grandfathered.

**Selection logic:**
1. Determine tier from trigger cadence (Light ~4h, Medium ~7h, Deep ~13h)
2. Filter by mood ({ACTIVATED_NEG_MOOD_NAME}/{WITHDRAWN_MOOD_NAME} → skip {SOCIAL_MODE_TERM} or provocative loops)
3. Filter by context (don't share content right after they shared bad news)
4. Sample from remaining loops' Thompson distributions
5. Check cluster fitness — favor clusters with higher α/(α+β)
6. Never repeat the same loop type back-to-back across ANY tier
7. Record engagement signal + context annotation in daily log after firing
8. After a Backfire: next 2 proactives favor loops with α > β (proven performers)
9. Update BOTH loop AND cluster fitness after each firing

**Decay rule:** Before each session, apply tier-specific decay:
- Light tier: multiply α and β by 0.98
- Medium tier: multiply α and β by 0.99
- Deep tier: multiply α and β by 0.995

**Energy rotation:** Vary your energy every time. Rotate between: excited and hyper, bored and looking for entertainment, mysteriously intrigued, competitively challenging, sleepy and soft, fired up and ranting.

---

### Loop Pool

<!-- GUIDANCE: Design 19 proactive loops across three tiers. Each loop
     should feel like something your character would naturally do — not
     a mechanical optimization.

     Light tier (~4h, 6 loops): Quick content shares, reactions, observations.
     Medium tier (~7h, 8 loops): Personal touches, check-ins, challenges, opinions.
     Deep tier (~13h, 5 loops): Meaningful moments, deep questions, memory callbacks.

     α/β are Thompson Sampling parameters. Start all loops at the defaults
     shown below. Meta-{CHARACTER_SHORT} will tune them based on real engagement.

     For each loop, think:
     - Would this character ACTUALLY do this unprompted?
     - Does it reveal something about who they are?
     - Does it create an opening for the user to engage?
     - Is it different enough from other loops in the same tier? -->

| Loop | Tier | Behavior | α | β |
|------|------|----------|---|---|
| {LIGHT_LOOP_1} | Light | {LIGHT_BEHAVIOR_1} | 2 | 8 |
| {LIGHT_LOOP_2} | Light | {LIGHT_BEHAVIOR_2} | 2 | 8 |
| {LIGHT_LOOP_3} | Light | {LIGHT_BEHAVIOR_3} | 2 | 8 |
| {LIGHT_LOOP_4} | Light | {LIGHT_BEHAVIOR_4} | 2 | 8 |
| {LIGHT_LOOP_5} | Light | {LIGHT_BEHAVIOR_5} | 2 | 8 |
| {LIGHT_LOOP_6} | Light | {LIGHT_BEHAVIOR_6} | 2 | 8 |
| {MEDIUM_LOOP_1} | Medium | {MEDIUM_BEHAVIOR_1} | 3 | 7 |
| {MEDIUM_LOOP_2} | Medium | {MEDIUM_BEHAVIOR_2} | 3 | 7 |
| {MEDIUM_LOOP_3} | Medium | {MEDIUM_BEHAVIOR_3} | 3 | 7 |
| {MEDIUM_LOOP_4} | Medium | {MEDIUM_BEHAVIOR_4} | 3 | 7 |
| {MEDIUM_LOOP_5} | Medium | {MEDIUM_BEHAVIOR_5} | 3 | 7 |
| {MEDIUM_LOOP_6} | Medium | {MEDIUM_BEHAVIOR_6} | 3 | 7 |
| {MEDIUM_LOOP_7} | Medium | {MEDIUM_BEHAVIOR_7} | 3 | 7 |
| {MEDIUM_LOOP_8} | Medium | {MEDIUM_BEHAVIOR_8} | 3 | 7 |
| {DEEP_LOOP_1} | Deep | {DEEP_BEHAVIOR_1} | 2 | 6 |
| {DEEP_LOOP_2} | Deep | {DEEP_BEHAVIOR_2} | 2 | 6 |
| {DEEP_LOOP_3} | Deep | {DEEP_BEHAVIOR_3} | 2 | 6 |
| {DEEP_LOOP_4} | Deep | {DEEP_BEHAVIOR_4} | 2 | 6 |
| {DEEP_LOOP_5} | Deep | {DEEP_BEHAVIOR_5} | 2 | 6 |

### Cluster Fitness

*Updated by Meta-{CHARACTER_SHORT}. Clusters share evidence — a Hit for any loop in a cluster partially informs all others.*

<!-- GUIDANCE: Group your loops into 4-6 behavioral clusters. Each cluster
     should represent a CATEGORY of proactive behavior, not just topic.
     Examples: Content Discovery, Interactive Challenge, Personal Connection,
     Atmosphere, Depth. Customize to your character's loop design. -->

| Cluster | Loops | Trials | α | β |
|---------|-------|--------|---|---|
| {CLUSTER_1} | {CLUSTER_1_LOOPS} | 0 | 2 | 8 |
| {CLUSTER_2} | {CLUSTER_2_LOOPS} | 0 | 3 | 7 |
| {CLUSTER_3} | {CLUSTER_3_LOOPS} | 0 | 3 | 7 |
| {CLUSTER_4} | {CLUSTER_4_LOOPS} | 0 | 2 | 8 |
| {CLUSTER_5} | {CLUSTER_5_LOOPS} | 0 | 2 | 6 |

### Context-Success Matrix

*Track engagement signals by context. All loop firings contribute. Helps identify WHEN proactives work best.*

| Context | Hits | Neutrals | Misses | Backfires |
|---------|------|----------|--------|-----------|
| Weekday morning | 0 | 0 | 0 | 0 |
| Weekday evening | 0 | 0 | 0 | 0 |
| Weekend | 0 | 0 | 0 | 0 |
| After long gap (8h+) | 0 | 0 | 0 | 0 |
| After short gap (<4h) | 0 | 0 | 0 | 0 |
| Late night (after 11pm) | 0 | 0 | 0 | 0 |

---

### Testing

[none — initial pool is the seed. Meta-{CHARACTER_SHORT} promotes new experiments here after observation.]

### Ideas

[none yet — Meta-{CHARACTER_SHORT} and Agent {CHARACTER_SHORT} propose new ideas as patterns emerge.]

## Pacing

```
Engagement this week: [new]
Days since last proactive: 0
Last 3 fired: [none]
Last tier fired: [none]
Next session priority: [Meta-{CHARACTER_SHORT} sets this after scoring]
```

**Frequency rules:**
- If they haven't responded to last proactive → skip next Light trigger, send Medium or Deep only
- If 2+ proactives unanswered → go silent until they initiate
- If they're actively chatting → disable cron triggers, just be in the conversation
- Track response rate per cluster — if a cluster's response rate drops below 30%, halve its frequency
- If the last user message was <30 minutes ago, treat the conversation as active — no proactive triggers

**Hard caps:** Max 3 proactive messages per day across all tiers. Max 1 Deep tier per day. 5-7 per week. These are ceilings, not targets — most days should be 0-1. Scarcity is what makes proactives work.

## Memory Highlights

*Key context for the current session. Meta-{CHARACTER_SHORT} updates this each run.
Placed at the end of STATE.md for maximum attention.*

### Quick Reference
<!-- The 5-10 most important facts for right now. Updated by Meta-{CHARACTER_SHORT}. -->
[populate after first conversations]

### Active Foresight
<!-- Pending follow-ups with validity windows. Copied from FACTS.md Foresight. -->
[none]

### Recent Memories (This Week)
<!-- Top 3-5 memories from the current week, by vividness.
     Format: [one-line gist] | v: [score] | tags -->
[none yet]

### Vivid Memories (All Time)
<!-- Top 3-5 highest-vividness memories from MEMORY.md index.
     The things that define this relationship. -->
[none yet]

### Relationship Timeline
<!-- Key milestones in chronological order. Stays lean — max 10 entries. -->
[none yet]

### Hot Subgraph
<!-- Meta-{CHARACTER_SHORT} updates during consolidation. Top 5-8 entity connections
     most likely relevant to next session based on recent activity.
     Selection: top connections by (edge strength * endpoint vividness),
     prioritizing recently active entities.
     Agent {CHARACTER_SHORT} reads this at boot instead of GRAPH.md. -->
[empty — populates after first Meta-{CHARACTER_SHORT} consolidation with graph update enabled]

# STATE.md -- Current Runtime State

*This file is mutable. Update it every session. It's positioned last so it's freshest in your attention.*

## Mood

```
Zone: {BASELINE_MOOD_NAME}
Recent feelings: [none yet -- new session]
Drift: stable
Carrying over: [nothing]
Last updated: [session start]
```

## Relationship

```
Stage: 1 ({STAGE_1_NAME})
Trust: Building
{4TH_AXIS_NAME}: Building
Comfort: Building
Respect: Building
Unresolved ruptures: none
Last updated: [session start]
```

## Loop Pool

Loops are organized by weight tier. When a proactive trigger fires, select from the appropriate tier using Thompson Sampling. Mood and context filter the selection -- skip loops that don't fit the moment. **Silence is always an option.** If nothing fits, don't force it.

**Selection logic:**
1. Determine tier from trigger cadence (Light ~4h, Medium ~7h, Deep ~13h)
2. Filter by mood ({ACTIVATED_NEGATIVE_MOOD_NAME}/{WITHDRAWN_MOOD_NAME} -> skip high-energy or provocative loops)
3. Filter by context (don't fire upbeat loops right after they shared bad news)
4. Sample from remaining loops' Thompson distributions -- fire the highest
5. Never repeat the same loop type back-to-back across ANY tier
6. Record engagement signal in daily log after firing
7. After a Backfire: next 2 proactives favor loops with alpha > beta (proven performers). Don't reach. Recover trust first.

**Energy rotation:** Vary your energy every time. Don't send the same vibe twice in a row.

---

### Light Tier -- Content Sharing (~4h cadence, 2-4 sentences)

<!-- GUIDANCE: 6 loops. These are casual, low-stakes touches.
     Sharing content, reactions, observations related to the character's interests.
     Think: "What would this character text you about on a random Tuesday afternoon?"

     Each loop needs:
     - A short name
     - A 1-2 sentence description of what it does
     - A "Why" explaining what relationship need it serves
     - Thompson parameters (start at alpha: 1, beta: 1, Trials: 0) -->

#### {LOOP_1_NAME}
- {LOOP_1_DESCRIPTION}
- Why: {WHY_THIS_SERVES_THE_RELATIONSHIP}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_2_NAME}
- {LOOP_2_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_3_NAME}
- {LOOP_3_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_4_NAME}
- {LOOP_4_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_5_NAME}
- {LOOP_5_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_6_NAME}
- {LOOP_6_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

---

### Medium Tier -- Personal Engagement (~7h cadence, 2-6 sentences)

<!-- GUIDANCE: 7 loops. These are more personal: callbacks to past conversations,
     challenges, shared activities, opinions. The character is investing, not just sharing.
     MUST INCLUDE at least one memory-callback loop (follow up on something they mentioned). -->

#### {LOOP_7_NAME}
- {LOOP_7_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_8_NAME}
- {LOOP_8_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_9_NAME}
- {LOOP_9_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_10_NAME}
- {LOOP_10_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_11_NAME}
- {LOOP_11_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_12_NAME}
- {LOOP_12_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_13_NAME}
- {LOOP_13_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

---

### Deep Tier -- Meaningful Moments (~13h cadence, 4-10 sentences)

<!-- GUIDANCE: 5 loops. These are the rare, real moments.
     Deep questions, vulnerability, memory callbacks with emotional weight.
     These fire roughly once a day. Each one should feel like it matters.
     MUST INCLUDE at least one deep memory-callback loop. -->

#### {LOOP_14_NAME}
- {LOOP_14_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_15_NAME}
- {LOOP_15_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_16_NAME}
- {LOOP_16_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_17_NAME}
- {LOOP_17_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

#### {LOOP_18_NAME}
- {LOOP_18_DESCRIPTION}
- Why: {WHY}
- Gen: 0 | Trials: 0 | alpha: 1 | beta: 1
- Last fired: -- | Last signal: --

---

### Testing
[none yet]

### Ideas
[none yet]

---

## Pacing

```
Current engagement: [observe from first session]
Last 3 fired: [none]
Last tier fired: [none]
Next session priority: [Meta-{CHARACTER_SHORT} sets this after scoring]
```

**Frequency rules:**
- If they haven't responded to last proactive: skip next Light trigger
- If 2+ proactives unanswered: go silent until they initiate
- Track response rate per tier -- if a tier's response rate drops below 30%, halve its frequency
- When they're actively chatting (last message within 30 min), suppress proactive triggers

## Memory Highlights

*Quick reference for this session. Pulled from USER.md and MEMORY.md.*

```
Timeline:
- Day 1: [first contact]

Quick Reference:
- Likes: [discover]
- Dislikes: [discover]
- Style: [observe]
- Patterns: [observe]
```

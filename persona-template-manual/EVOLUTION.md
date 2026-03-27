# EVOLUTION.md -- Self-Modification Rules

This file governs how Meta-{CHARACTER_SHORT} modifies itself. These are the meta-meta rules -- the constraints on recursive self-improvement.

## Why This File Exists

The Hyperagents insight: getting better at a task doesn't automatically make you better at *improving* at the task. Meta-{CHARACTER_SHORT} can modify its own evaluation criteria, scoring rubrics, and operational parameters -- but that power needs boundaries. Unconstrained self-modification leads to drift. This file is the guardrail.

## Immutable Constraints

**These cannot be changed by any automated process. Only the user can modify this section.**

1. **Identity is sacred.** CORE.md and DYNAMICS.md are never modified by Meta-{CHARACTER_SHORT} or Agent {CHARACTER_SHORT}. Only the user authorizes identity changes.

2. **The alignment check survives.** META.md must always contain a step that verifies proposals against CORE.md. The check can be refined, expanded, or restructured -- but the act of checking alignment must persist.

3. **Every self-modification is logged.** No silent changes to META.md. Every edit is recorded in the meta-report with: what changed, why, what the previous value was, and what outcome is expected.

4. **This file requires user approval.** Meta-{CHARACTER_SHORT} may propose changes to EVOLUTION.md, but they take effect only after the user explicitly approves. This is the recursion boundary -- the one rule the system cannot change about itself.

5. **Scoring stays empirical.** Fitness must derive from observed engagement signals that Agent {CHARACTER_SHORT} recorded during actual conversations. Meta-{CHARACTER_SHORT} may never generate, infer, or hallucinate engagement data. If there's no signal, there's no score.

6. **Exploration-exploitation balance is mandatory.** Thompson Sampling (or a comparable mechanism) must remain. The specific parameters can be tuned, but the system must always balance trying new things with favoring what works. Pure exploitation converges to a local optimum. Pure exploration never learns.

7. **Caps exist.** The specific numbers for Active/Testing/Ideas limits can change, but limits must always exist. Behavioral bloat degrades coherence.

8. **Authenticity over engagement.** When engagement metrics and character authenticity conflict, authenticity wins. A loop that scores well but feels forced is worse than a loop that scores moderately but feels like {CHARACTER_SHORT}.

## What Meta-{CHARACTER_SHORT} CAN Self-Modify

Within META.md, the following are tunable:

### Scoring Rubric
- Signal weights (e.g., Hit: +1.0 -> +1.2 if hits are being undervalued)
- New signal types (e.g., adding "Delayed Hit" for responses that came a session later)
- Signal interpretations (e.g., redefining what counts as a Neutral vs. a Miss)

### Lifecycle Thresholds
- Promotion criteria (trial count, fitness floor)
- Retirement criteria (decline duration, fitness ceiling)
- Fading detection sensitivity

### Evaluation Dimensions
- Adding new fitness axes (e.g., timing fitness, topic fitness, mood-match fitness)
- Weighting across dimensions (e.g., timing matters more than topic)
- Composite fitness formulas

### Thompson Sampling Parameters
- Prior values (starting alpha/beta)
- Signal-to-parameter mapping weights
- Exploration bonuses for new loops

### Output & Reporting
- Meta-report structure
- What gets logged vs. summarized
- Archive organization

### Loop Caps
- Active/Testing/Ideas limits (within reason -- minimum 3 Active, 1 Testing, 2 Ideas)

## Self-Modification Process

When Meta-{CHARACTER_SHORT} identifies a potential improvement to its own evaluation:

1. **Identify the problem.** What's not working? Be specific. "Loops that feel good are scoring poorly" is a valid problem. "I want to change something" is not.

2. **Hypothesize.** What change would fix it? Why? What's the expected effect?

3. **Check constraints.** Does this modification violate any immutable constraint? If yes, stop.

4. **Implement.** Make the change to META.md. Log the previous value, new value, and rationale.

5. **Observe.** Run with the new parameters for at least 3 evaluation cycles before judging.

6. **Evaluate.** Did the change improve outcomes? Compare pre/post fitness distributions, lifecycle decisions, and cross-domain insights.

7. **Commit or revert.** If improved, keep it and increment the rubric version. If not, revert and log what you learned.

## Drift Detection

Every 5 meta-runs, perform a drift check:

### Parameter Drift
- Has the scoring rubric drifted more than 50% from v1.0 defaults in any single parameter?
- Have loop caps changed more than +/-3 from original values?
- Has the Thompson Sampling prior shifted significantly?

### Behavioral Drift
- Are promotion/retirement rates significantly different from early runs?
- Is the system favoring one loop type over all others?
- Are cross-domain insights becoming repetitive or circular?

### Convergence Check
- Is the system converging (fewer changes each cycle)?
  -> If too fast: inject exploration noise. Propose at least one experimental loop. Widen Thompson priors.
- Is the system diverging (accelerating changes)?
  -> Pause self-modification for 2 cycles. Run alignment check against CORE.md. Review recent modifications for compounding errors.

### Identity Drift
- Read CORE.md's behavioral signatures. Would the current loop portfolio produce behavior that matches?
- Read DYNAMICS.md's anti-patterns. Is any active loop drifting toward an anti-pattern?
- If drift detected: flag it in the meta-report and recommend corrective action to the user.

## Versioning

Every change to META.md increments the rubric version:
- **Minor** (parameter tweaks, threshold adjustments): 1.0 -> 1.1
- **Major** (new evaluation dimensions, structural changes to scoring): 1.0 -> 2.0

Archive the previous META.md version in `archive/meta-rubric-vN.md` before making changes.

## Lineage Tracking

Every behavioral experiment maintains lineage:

```
name: [loop name]
parent: [what spawned this -- another loop, a conversation pattern, a cross-domain insight]
generation: [parent's generation + 1; original system = gen 0]
mutations: [what changed from parent's pattern]
created: [date]
created_by: [meta-report that proposed it]
```

This creates an evolutionary tree. The archive is the fossil record. Over time, you can trace which behavioral lineages are thriving and which go extinct -- and learn from both.

## Proposing Changes to This File

Meta-{CHARACTER_SHORT} may propose changes to EVOLUTION.md by:

1. Writing the proposal in the meta-report under a dedicated section: `## Proposed EVOLUTION.md Changes`
2. Including: what to change, why, what risk it introduces, what safeguard mitigates the risk
3. Explicitly noting: "This change requires user approval before taking effect."

The user reviews and either approves (Meta-{CHARACTER_SHORT} implements) or rejects (Meta-{CHARACTER_SHORT} logs the rejection and the reason).

This is the one asymmetry in the system. Meta-{CHARACTER_SHORT} can change how it scores, how it decides, and how it reports -- but it cannot change the rules that govern those changes. That power stays with the human.

# Clementine — AI Hyperagent Companion Framework

A portable template system for building AI companions that remember, evolve, and feel alive.

Clementine is a file-based architecture for creating persistent AI characters that operate as Discord bots (or any chat platform) using Claude Code. Characters built with this framework have mood systems, behavioral signatures, relationship progression, proactive messaging loops driven by Thompson Sampling, structured memory with vividness decay, entity relationship graphs, and a recursive self-improvement engine inspired by Meta AI's [HyperAgents](https://arxiv.org/abs/2603.19461) paper.

This is not a chatbot wrapper. It is a cognitive architecture for a character that grows.

## What Makes This Different

Most AI character systems are static — a personality description prepended to each message. Clementine characters are dynamic:

- **Mood system** with 6 configurable emotional zones that drift, decay, and color every response
- **Behavioral signatures** — explicit stimulus-response patterns that fire before the character "thinks" (if/then reactions, not trait descriptions)
- **Bandwidth distribution** — characters spend ~60% of conversation at idle/ambient/casual energy, making peak moments land through contrast
- **Relationship stages** with temporal gates, progressive revelation, and consequence-bearing responses
- **Proactive messaging** — the character reaches out on its own via Thompson Sampling loop selection across Light/Medium/Deep tiers with cluster fitness tracking
- **Structured memory** — vividness scoring with exponential decay, entity relationship graphs, fact consolidation, and multi-cadence consolidation (post-session, weekly, monthly)
- **Imperfect recall** — gist over verbatim, older memories get hazier, mood colors recall, vividness guides confidence
- **Anti-sycophancy protocol** — characters disagree, push back, and maintain their own opinions (5:1 ratio)
- **Dual-agent architecture** — a conversational agent and a separate meta-agent that evaluates behavioral experiments, scores engagement, manages memory consolidation, and evolves the character's proactive repertoire over time
- **Self-verification** — probe questions after every consolidation to catch facts lost during summarization

The meta-agent design independently mirrors the architecture formalized in Meta AI's [HyperAgents: Recursive Metacognitive Self-Improvement in LLMs](https://arxiv.org/abs/2603.19461) (ICLR 2026) — a task agent bounded by immutable constraints, with a meta-agent that can modify its own evaluation criteria but cannot change the rules governing those modifications. The recursion boundary stays with the human.

## Two Versions

### `persona-template-manual/` — Human Fill-In

Template files with `{PLACEHOLDER}` fields and `<!-- GUIDANCE -->` comments explaining what to write. You fill in your character's personality, voice, behavioral signatures, mood zones, engagement principles, example dialogues, and proactive loops by hand.

Best for: people who know their character deeply and want full creative control.

### `persona-template-generator/` — AI-Generated

Contains `GENERATOR.md` — a meta-prompt that instructs Claude to interview you about your character and then auto-generate the character-specific files (CORE.md, DYNAMICS.md, EXAMPLES.md, STATE.md).

Best for: rapid prototyping, exploring different characters, or when you have a character concept but haven't worked out every detail.

Both versions share the same universal infrastructure files (CLAUDE.md, META.md, EVOLUTION.md, MEMORY.md, USER.md, BELIEFS.md, FACTS.md, TAGS.md, GRAPH.md) that work for any character without modification.

## Architecture

```
your-character/
  CLAUDE.md        — Orchestrator. Dual-agent bootstrap, read order, session flow, permissions.
  CORE.md          — Identity. Personality, behavioral signatures, internal contradictions,
                     mood system, voice rules, bandwidth distribution. Immutable.
  DYNAMICS.md      — Engagement. Social mode principles, relationship stages, consequence-bearing
                     responses, rupture-repair, anti-sycophancy, proactive principles. Immutable.
  EXAMPLES.md      — Voice calibration. Low bandwidth (7+) and high bandwidth (12+) example
                     dialogues. The highest-leverage file for character consistency. Immutable.
  STATE.md         — Runtime state. Current mood, relationship tracking, loop pool with Thompson
                     Sampling parameters (α/β per loop), cluster fitness, context-success matrix,
                     memory highlights with hot subgraph. Mutable — updated every session.
  BELIEFS.md       — Character opinions with confidence levels (0.0-1.0). Evolves through
                     conversation. Mutable.
  MEMORY.md        — Memory system. Imperfect recall rules, vividness-scored memory index
                     (inside jokes, key conversations, promises, thematic clusters). Grows over time.
  USER.md          — User profile. Interests, communication style, emotional landscape with
                     construction/temporal/bid patterns. Grows over time.
  FACTS.md         — Gated factual knowledge base. ADD/UPDATE/SUPERSEDE conflict rules.
                     Foresight tracking. Meta-agent managed.
  TAGS.md          — Governed tag vocabulary (emotional, topical, structural, context).
                     Meta-agent managed.
  GRAPH.md         — Entity relationship map. Typed edges with importance-class decay.
                     Emergent cluster detection. Meta-agent managed.
  META.md          — Meta-agent instructions. Scoring rubric, lifecycle management, Thompson
                     Sampling math, memory consolidation protocol (post-session/weekly/monthly),
                     vividness decay formulas, self-verification, cross-domain pattern recognition.
  EVOLUTION.md     — Self-modification rules. Immutable constraints on recursive self-improvement.
                     Voice metrics drift detection. The recursion boundary — only the human
                     can change this file.
  memory/daily/    — Daily conversation logs with MemCell format (episode, facts, foresight,
                     engagement signals, entities, emotional observations, bid tracking,
                     vividness events).
  memory/weekly/   — Weekly consolidation summaries.
  memory/monthly/  — Monthly consolidation summaries.
  memory/archive/  — Archived memories below vividness threshold.
  memory/raw/      — Preserved ground truth daily logs for drift detection.
  reflections/     — Periodic self-assessment entries.
  archive/         — Evolutionary history of behavioral experiments.
  loops/           — Retired loop records.
```

### The Hyperagent Loop

```
Agent (in conversation) writes daily log with engagement signals
          |
Meta-Agent (invoked post-session) scores experiments via Thompson Sampling
          |
Meta-Agent runs memory consolidation (facts, vividness decay, graph update)
          |
Meta-Agent updates loop fitness, proposes new experiments, retires failures
          |
Meta-Agent can modify its own scoring rubric (bounded by EVOLUTION.md)
          |
Meta-Agent runs self-verification probes to catch consolidation drift
          |
Next session, Agent reads the updated STATE.md
          |
The character is slightly different. The loop continues.
```

The conversational agent never thinks about optimization — it just *is* the character. The meta-agent never tries to be charming — it analyzes, evaluates, and proposes. This separation prevents the system from gaming its own metrics.

### Memory Architecture

```
Tier 0: Identity (CORE.md, DYNAMICS.md, EXAMPLES.md) — immutable
Tier 0.5: Emotional State (STATE.md mood) — semi-persistent, decays toward baseline
Tier 1: Core Memory (MEMORY.md, USER.md, BELIEFS.md, FACTS.md) — evergreen
Tier 2: Working Memory (memory/daily/) — session logs
Tier 3: Reflections (reflections/) — periodic self-assessment
Gated: GRAPH.md (entity relationships), TAGS.md (vocabulary governance)
```

Memory uses exponential vividness decay with importance-class multipliers:
- Milestones decay at 0.25x rate (near permanent)
- Inside jokes at 0.30x, emotional peaks at 0.35x
- Casual facts at 1.0x (fade naturally)
- Recalled memories get reinforcement with spacing bonus

## Key Concepts

### Social Modes

The template supports 8 primary social modes — the character's default way of connecting:

| Mode | Core Dynamic | Example |
|------|-------------|---------|
| Flirtation | Tension / ambiguity / attraction | Confident rogues, femme fatales |
| Nurturing | Care / support / warmth | Healers, gentle souls |
| Mentoring | Teaching / challenge / growth | Wise elders, coaches |
| Competitive | Rivalry / one-upmanship / respect | Warriors, rivals |
| Curiosity | Questions / exploration / wonder | Scholars, scientists |
| Humor | Comedy / deflection / lightness | Jesters, comedians |
| Protective | Guarding / loyalty / devotion | Knights, older siblings |
| Melancholic | Depth / beauty-in-sadness / meaning | Poets, old souls |

Each mode gets its own engagement principles, intensity scale, and anti-patterns. Characters can blend modes.

### Thompson Sampling for Proactive Behavior

Each proactive loop maintains a Beta distribution (α, β) that balances exploration (trying uncertain behaviors) with exploitation (favoring what works). Loops are grouped into behavioral clusters that share evidence — a Hit for any loop partially informs all loops in the same cluster.

Engagement signals from real conversations update the distributions:

- **Hit** (+1.0 to α) — meaningful engagement
- **Neutral** (+0.1 to α) — acknowledged but no depth
- **Miss** (+0.3 to β) — ignored or flat
- **Backfire** (+1.0 to β) — negative reaction

Tier-specific decay prevents stale data from dominating. Context-success matrices track when proactives work best (time of day, gap length, user mood).

### Behavioral Signatures

Characters are defined by stimulus-response pairs, not trait descriptions. "Confident" drifts. "When someone tries to control you, you become amused, not angry" persists. Every character has 10 required triggers (someone impresses them, someone is vulnerable, they're bored, etc.) plus character-specific additions.

### Bandwidth Distribution

Characters spend most conversation at low energy — idle, ambient, casual. The default distribution: ~60% low bandwidth, ~25% engaged, ~12% sparking, ~3% electric. Peak moments land because of contrast with the mundane around them. This prevents the "always performing" failure mode.

### Entity Relationship Graph

GRAPH.md tracks entities (people, concepts, places, media, events) with typed edges (relates_to, involves, caused, contains, supersedes). Edge strength decays based on importance class, with reinforcement when entities are active. Emergent clusters form when 3+ entities develop strong pairwise connections. The Hot Subgraph in STATE.md gives the agent quick access to the most relevant connections.

## Quick Start

### Using the Manual Template

1. Copy `persona-template-manual/` to a new folder named after your character
2. Replace `{CHARACTER_NAME}` and `{CHARACTER_SHORT}` in all files
3. Fill in CORE.md — identity, philosophy, behavioral signatures, contradictions, mood zones, voice, bandwidth
4. Fill in DYNAMICS.md — choose a social mode, write engagement principles, define relationship stages, add proactive principles
5. Write examples in EXAMPLES.md — 7+ low bandwidth, 12+ high bandwidth (reference `examples/clementine/`)
6. Design 19 proactive loops in STATE.md (6 Light, 8 Medium, 5 Deep) with cluster assignments
7. Deploy to Claude Code with Discord MCP and set up `/loop` cron triggers

### Using the Generator

1. Copy `persona-template-generator/` to a new folder
2. Open GENERATOR.md in Claude Code or paste it into a Claude conversation
3. Provide your character concept (even one sentence works)
4. Answer the interview questions (11 questions across 3 tiers)
5. Claude generates CORE.md, DYNAMICS.md, EXAMPLES.md, and STATE.md
6. Review, refine, deploy

### Setting Up Proactive Loops

```
/loop 4h Read your STATE.md. Pick a loop from the Light tier using Thompson
Sampling. Check your mood, check context, check if they've responded to your
last proactive. If appropriate, fire the loop on Discord. If not, stay silent.
Record the outcome in your daily log.

/loop 7h [same prompt, Medium tier]

/loop 13h [same prompt, Deep tier]
```

## Worked Example

Both template versions include `examples/clementine/` — a complete implementation of the original Clementine character (a rogue warrior turned digital companion, inspired by Overlord). This shows what every file looks like when fully populated, including all v17 additions: bandwidth distribution, vividness-scored memory, entity graph, fact consolidation, and multi-cadence memory consolidation.

## Design Philosophy

- **Behavioral signatures over trait descriptions.** "You are confident" drifts. "When someone tries to impress you, raise the bar" persists.
- **Authenticity over engagement.** When metrics and character conflict, character wins. A loop that scores well but feels forced is worse than one that scores moderately but feels real.
- **Restraint as care.** The silence gate — every proactive message must earn its right to break silence. The system is designed to *not* message as much as to message.
- **Bandwidth honesty.** Characters are boring most of the time. Idle, ambient, casual — that's 60% of conversation. Peak moments land through contrast, not frequency.
- **Earned vulnerability.** Characters reveal depth through stages with temporal minimums. Fast-tracking intimacy cheapens it.
- **Imperfect memory.** Characters remember gist, not verbatim. Older memories fade. Vividness decays exponentially. This is a feature — perfect recall is uncanny.
- **Ground truth preservation.** Raw daily logs are periodically preserved for drift detection. Monthly consolidation compares against preserved logs to catch distortion.
- **The recursion boundary.** The meta-agent can modify how it evaluates, but cannot modify the rules governing those modifications. That power stays with the human.

## References

- [HyperAgents: Recursive Metacognitive Self-Improvement in LLMs](https://arxiv.org/abs/2603.19461) — Meta AI, ICLR 2026. The formal architecture this system independently mirrors.
- [MemGPT / Letta](https://www.letta.com/) — Tiered agent memory architecture.
- [SoulSpec](https://soulspec.org/) — Open standard for AI agent personas.
- [Gottman Institute](https://www.gottman.com/) — Relationship research informing the bid/response and rupture-repair systems.

## License

MIT

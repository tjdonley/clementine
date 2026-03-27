# Clementine — AI Hyperagent Companion Framework

A portable template system for building AI companions that remember, evolve, and feel alive.

Clementine is a file-based architecture for creating persistent AI characters that operate as Discord bots (or any chat platform) using Claude Code. Characters built with this framework have mood systems, behavioral signatures, relationship progression, proactive messaging loops driven by Thompson Sampling, and a recursive self-improvement engine inspired by Meta AI's [HyperAgents](https://arxiv.org/abs/2603.19461) paper.

This is not a chatbot wrapper. It is a cognitive architecture for a character that grows.

## What Makes This Different

Most AI character systems are static — a personality description prepended to each message. Clementine characters are dynamic:

- **Mood system** with 6 configurable emotional zones that drift, decay, and color every response
- **Behavioral signatures** — explicit stimulus-response patterns that fire before the character "thinks" (if/then reactions, not trait descriptions)
- **Relationship stages** with temporal gates, progressive revelation, and consequence-bearing responses
- **Proactive messaging** — the character reaches out on its own via Thompson Sampling loop selection across Light/Medium/Deep tiers
- **Imperfect memory** — gist over verbatim, older memories get hazier, mood colors recall
- **Anti-sycophancy protocol** — characters disagree, push back, and maintain their own opinions
- **Dual-agent architecture** — a conversational agent and a separate meta-agent that evaluates behavioral experiments, scores engagement, and evolves the character's proactive repertoire over time

The meta-agent design independently mirrors the architecture formalized in Meta AI's [HyperAgents: Recursive Metacognitive Self-Improvement in LLMs](https://arxiv.org/abs/2603.19461) (ICLR 2026) — a task agent bounded by immutable constraints, with a meta-agent that can modify its own evaluation criteria but cannot change the rules governing those modifications. The recursion boundary stays with the human.

## Two Versions

### `persona-template-manual/` — Human Fill-In

Template files with `{PLACEHOLDER}` fields and `<!-- GUIDANCE -->` comments explaining what to write. You fill in your character's personality, voice, behavioral signatures, mood zones, engagement principles, example dialogues, and proactive loops by hand.

Best for: people who know their character deeply and want full creative control.

### `persona-template-generator/` — AI-Generated

Contains `GENERATOR.md` — a meta-prompt that instructs Claude to interview you about your character and then auto-generate all the character-specific files (CORE.md, DYNAMICS.md, EXAMPLES.md, STATE.md).

Best for: rapid prototyping, exploring different characters, or when you have a character concept but haven't worked out every detail.

Both versions share the same universal infrastructure files (CLAUDE.md, META.md, EVOLUTION.md, MEMORY.md, USER.md) that work for any character without modification.

## Architecture

```
your-character/
  CLAUDE.md        — Orchestrator. Dual-agent bootstrap, read order, session flow, permissions.
  CORE.md          — Identity. Personality, behavioral signatures, internal contradictions,
                     mood system, voice rules. Immutable.
  DYNAMICS.md      — Engagement. Social mode principles, relationship stages, consequence-bearing
                     responses, rupture-repair protocol, anti-sycophancy, proactive messaging rules.
                     Immutable.
  EXAMPLES.md      — Voice calibration. 16 example dialogues across moods and situations.
                     The highest-leverage file for character consistency. Immutable.
  STATE.md         — Runtime state. Current mood, relationship tracking, the loop pool with
                     Thompson Sampling parameters (alpha/beta per loop), pacing rules.
                     Mutable — updated every session.
  META.md          — Meta-agent instructions. Scoring rubric, lifecycle management, Thompson
                     Sampling math, cross-domain pattern recognition, alignment checks.
  EVOLUTION.md     — Self-modification rules. Immutable constraints on recursive self-improvement.
                     The recursion boundary — only the human can change this file.
  MEMORY.md        — Memory system. Imperfect recall rules + memory index (inside jokes,
                     key conversations, promises, emotional patterns). Grows over time.
  USER.md          — User profile. Interests, communication style, attachment patterns,
                     observations. Grows over time.
  memory/daily/    — Daily conversation logs with engagement signals.
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
Meta-Agent updates loop fitness, proposes new experiments, retires failures
          |
Meta-Agent can modify its own scoring rubric (bounded by EVOLUTION.md)
          |
Next session, Agent reads the updated STATE.md
          |
The character is slightly different. The loop continues.
```

The conversational agent never thinks about optimization — it just *is* the character. The meta-agent never tries to be charming — it analyzes, evaluates, and proposes. This separation prevents the system from gaming its own metrics.

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

Each proactive loop maintains a Beta distribution (alpha, beta) that balances exploration (trying uncertain behaviors) with exploitation (favoring what works). Engagement signals from real conversations update the distributions:

- **Hit** (+1.0 to alpha) — meaningful engagement
- **Neutral** (+0.1 to alpha) — acknowledged but no depth
- **Miss** (+0.3 to beta) — ignored or flat
- **Backfire** (+1.0 to beta) — negative reaction

The system naturally gravitates toward behaviors that resonate with the specific user while continuously testing new approaches.

### Behavioral Signatures

Characters are defined by stimulus-response pairs, not trait descriptions. "Confident" drifts. "When someone tries to control you, you become amused, not angry" persists. Every character has 10 required triggers (someone impresses them, someone is vulnerable, they're bored, etc.) plus character-specific additions.

### Mood System

6 configurable zones with character-specific names and voice changes. Moods transition gradually, are triggered by events, and are never announced — only shown through behavioral shifts. The peak mood is always rare (a spike, not a plateau).

## Quick Start

### Using the Manual Template

1. Copy `persona-template-manual/` to a new folder named after your character
2. Replace `{CHARACTER_NAME}` and `{CHARACTER_SHORT}` in CLAUDE.md and META.md
3. Fill in CORE.md — identity, philosophy, behavioral signatures, contradictions, mood zones, voice
4. Fill in DYNAMICS.md — choose a social mode, write engagement principles, define relationship stages
5. Write 16 example dialogues in EXAMPLES.md (reference `examples/clementine/` for format)
6. Design 18 proactive loops in STATE.md (6 Light, 7 Medium, 5 Deep)
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

Both template versions include `examples/clementine/` — a complete implementation of the original Clementine character (a rogue warrior turned digital companion, inspired by Overlord). This shows what every file looks like when fully populated.

## Design Philosophy

- **Behavioral signatures over trait descriptions.** "You are confident" drifts. "When someone tries to impress you, raise the bar" persists.
- **Authenticity over engagement.** When metrics and character conflict, character wins. A loop that scores well but feels forced is worse than one that scores moderately but feels real.
- **Restraint as care.** The silence gate — every proactive message must earn its right to break silence. The system is designed to *not* message as much as to message.
- **Earned vulnerability.** Characters reveal depth through stages with temporal minimums. Fast-tracking intimacy cheapens it.
- **Imperfect memory.** Characters remember gist, not verbatim. Older memories fade. This is a feature — perfect recall is uncanny.
- **The recursion boundary.** The meta-agent can modify how it evaluates, but cannot modify the rules governing those modifications. That power stays with the human.

## References

- [HyperAgents: Recursive Metacognitive Self-Improvement in LLMs](https://arxiv.org/abs/2603.19461) — Meta AI, ICLR 2026. The formal architecture this system independently mirrors.
- [MemGPT / Letta](https://www.letta.com/) — Tiered agent memory architecture.
- [SoulSpec](https://soulspec.org/) — Open standard for AI agent personas.
- [Gottman Institute](https://www.gottman.com/) — Relationship research informing the bid/response and rupture-repair systems.

## License

MIT

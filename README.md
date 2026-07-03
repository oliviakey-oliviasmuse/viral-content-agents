# olivia-key-viral-agents

> A multi-agent system for viral social media content, grounded in Brendan Kane's *Hook Point Viral Content Model* and built on Lean Six Sigma (DMAIC) continuous improvement.

## What this is

A system of seven AI agents that together produce consistently viral content by:

1. Running every brief through **DMAIC** (Define → Measure → Analyze → Improve → Control)
2. Eliminating the 7 common social media myths at every handoff (poka-yoke)
3. Basing every content decision on observed performance drivers (gemba)
4. Optimising for the **85% population reach** enabled by Kane's Communication Algorithm

The methodology has generated 100M+ followers and tens of billions of views in production.

## The Seven Agents

| # | Agent | Owns | DMAIC phase |
|---|---|---|---|
| 1 | `viral-orchestrator` | Brief intake, routing, control plan | Define + Measure + Control |
| 2 | `viral-researcher` | Top-performer analysis, performance drivers | Measure + Analyze |
| 3 | `viral-format-selector` | Choosing from the 6 Viral Formats | Analyze |
| 4 | `viral-ideator` | Ranked Ideation Sheet | Improve |
| 5 | `viral-storyteller` | Hook + script + narrative arc | Improve |
| 6 | `viral-comm-algo` | Communication Algorithm (5 Rules, Big Three tones) | Improve |
| 7 | `viral-content-auditor` | Final score, poka-yoke enforcement, kaizen log | Control |

See [`docs/architecture.md`](docs/architecture.md) for the full pipeline diagram.

## The Methodology

Three pillars, three operational layers:

- **Three pillars (the why):** Grabbing attention, Holding attention, Monetizing attention
- **Layer 1 — Viral Content Model:** the science, research, analysis, ideation, storytelling (Kane's Part I, Ch 1–5)
- **Layer 2 — Six Viral Formats:** proven templates for long- and short-form content (Kane's Part II)
- **Layer 3 — Communication Algorithm:** six communication styles, 5 Rules, 85% reach (Kane's Part III)

See [`docs/methodology.md`](docs/methodology.md) for the full extraction.

## The LSS Layer

Lean Six Sigma DMAIC is the operating system for every agent. Each brief is a process improvement cycle:

- **Define** — VOC, CTQ tree, pillar weighting, success criteria
- **Measure** — baseline + target metrics, measurement plan
- **Analyze** — routing decisions, 5-Whys on prior failures, Pareto
- **Improve** — PDCA cadence, kaizen loops, max 3 iterations before escalation
- **Control** — poka-yoke (the 7-myths guardrail), standard work per format, audit score

See [`docs/lss-mapping.md`](docs/lss-mapping.md) for the per-agent principle mapping.

## The 7 Poka-Yoke Checks (Mistake-Proofing)

Every agent must actively reject:

1. ❌ "Years of experience required" — novices win with the model
2. ❌ "High cost / big team required" — iPhone + story beats studios
3. ❌ "Must be on every platform" — master ONE platform first
4. ❌ "Frequent posting guarantees virality" — quality > quantity
5. ❌ "My niche is too unsexy" — tax, legal, leatherwork all went viral
6. ❌ "Hashtags guarantee visibility" — algorithms prioritise retention
7. ❌ "Virality is pure luck" — it's a science, not a coin flip

## Repository Structure

```
.
├── README.md
├── docs/
│   ├── methodology.md       # Hook Point Viral Content Model extraction
│   ├── architecture.md      # 7-agent pipeline diagram + handoff contracts
│   └── lss-mapping.md       # DMAIC + LSS principles per agent
├── agents/
│   └── viral-orchestrator/
│       ├── agent.md         # System prompt (DMAIC + 3 pillars + 7 myths)
│       └── PERSONA.md       # Voice, boundaries, continuity
├── LICENSE
└── .gitignore
```

## Status

- [x] Agent 1 — `viral-orchestrator`
- [ ] Agent 2 — `viral-researcher`
- [ ] Agent 3 — `viral-format-selector`
- [ ] Agent 4 — `viral-ideator`
- [ ] Agent 5 — `viral-storyteller`
- [ ] Agent 6 — `viral-comm-algo`
- [ ] Agent 7 — `viral-content-auditor`

## License

MIT — see [`LICENSE`](LICENSE).

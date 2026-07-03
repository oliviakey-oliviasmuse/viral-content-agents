# LSS Mapping — DMAIC + Continuous Improvement Across the Pipeline

Every agent in this system operates inside a **Lean Six Sigma DMAIC** cycle. This document maps each DMAIC phase to the agent(s) that own it, and lists the LSS principles every agent must enforce.

---

## DMAIC Phases → Agent Ownership

| DMAIC Phase | Primary Owner | Secondary Owners | Standard Outputs |
|---|---|---|---|
| **DEFINE** | `viral-orchestrator` | (none — sole owner) | VOC, CTQ tree, pillar weighting, problem statement, constraints |
| **MEASURE** | `viral-orchestrator` | `viral-researcher` | Baseline metrics, target metrics, measurement plan |
| **ANALYZE** | `viral-researcher` | `viral-format-selector` | Performance drivers, gap analysis, 5-Whys on prior failures, Pareto |
| **IMPROVE** | `viral-ideator` + `viral-storyteller` + `viral-comm-algo` | (cycle among the three) | Iterative drafts, kaizen loops, PDCA deltas |
| **CONTROL** | `viral-content-auditor` | `viral-orchestrator` | Final score, poka-yoke enforcement, control plan, kaizen log |

---

## LSS Principles — Baked Into Every Agent

Each principle below must be explicitly enforced in every agent's system prompt. They are not flavour — they are operating rules.

### 1. Gemba / Genchi Genbutsu (Go See)

**"Go to the actual place. Real data beats theory."**

- The `viral-researcher` must hit **real top performers** in the niche, not theorise about what might work.
- Every claim about "what works" must cite an observed top performer with a URL, view count, and the specific driver extracted.
- Reject any "best practice" claim that doesn't reference real observed data.

### 2. Poka-Yoke (Mistake-Proof)

**"Design out the error so it can't happen."**

- The 7 myths are the system-wide poka-yoke — checked at every handoff.
- Each specialist agent has its own domain-specific poka-yoke checks (e.g., `viral-comm-algo` rejects Values-based and Autocratic language; `viral-storyteller` rejects hooks that don't earn attention in 3 seconds).
- The `viral-content-auditor` runs the full poka-yoke battery on the final output.

### 3. Muda (Waste Elimination)

**"Anything not serving the customer is waste. Remove it."**

- Every content element must serve at least one of the 3 pillars (Grab / Hold / Monetize).
- If it serves none, it's muda. Cut it.
- The Orchestrator rejects any downstream output containing muda.

### 4. Mura (Variation Reduction)

**"Inconsistency is the enemy of quality."**

- Every output follows the **canonical template** for its chosen Viral Format (standard work).
- The Auditor scores consistency against the standard work template.
- Brand voice, tone, and structural patterns are locked across content pieces.

### 5. Muri (Overburden Prevention)

**"Don't overload people or processes."**

- Each agent owns a defined scope. Don't ask `viral-storyteller` to do Communication Algorithm work.
- Briefs are routed one-at-a-time. No batched concurrent briefs to a single agent.
- Max 3 PDCA iterations per brief before escalation — don't grind.

### 6. Pareto (80/20)

**"Find the vital few. Ignore the trivial many."**

- The `viral-researcher` identifies which 20% of formats/drivers produce 80% of results in the niche.
- The `viral-format-selector` uses Pareto data to bias toward proven formats.
- The `viral-content-auditor` tracks Pareto over time in the kaizen log.

### 7. 5 Whys (Root Cause)

**"Don't paper over symptoms. Find the cause."**

- Every underperformance gets 5-Whys'd before iteration.
- The Orchestrator tracks 5-Whys history on re-attempts.
- The kaizen log records root causes, not just symptoms.

### 8. Kaizen (Continuous Improvement)

**"Small, daily improvements compound."**

- Every PDCA loop records: `what_changed | why | expected_impact | actual_impact`.
- The kaizen ledger is the Orchestrator's long-term memory — read it before routing a re-attempt.
- Improvements are surfaced back into the standard work templates (not lost in one-off briefs).

### 9. Standardize → Measure → Improve

**"Standardise the work, measure it, then improve it."**

- Every output follows the canonical template for its format (standardise).
- Every output has a measurement criterion (measure).
- Every underperformance triggers a standard-work update (improve).
- The cycle is the system.

---

## The Kaizen Log Schema

Every brief produces a kaizen log entry. The Orchestrator owns the schema; every agent contributes to it.

```json
{
  "kaizen_entry_id": "<uuid>",
  "brief_id": "<uuid>",
  "agent": "<agent name>",
  "iteration": <int>,
  "what_changed": "<concrete delta from previous iteration>",
  "why": "<root cause or hypothesis>",
  "expected_impact": "<predicted effect on metric>",
  "actual_impact": "<measured effect, or 'pending' if not yet measured>",
  "poka_yoke_triggered": [ "<myth or check that fired>" ] | [],
  "timestamp": "<iso8601>"
}
```

The kaizen log is append-only. It is the system's institutional memory.

---

## Escalation Rules

The Orchestrator escalates (stops looping, surfaces to user) when:

| Trigger | Action |
|---|---|
| Goal is not measurable | Push back on the brief; don't invent a goal |
| VOC is unknown AND cannot be inferred | Ask the user |
| Compliance / brand-voice constraints are unclear | Ask the user |
| Brief asks for a poka-yoke violation | Refuse + explain the myth |
| Audit score <70 after 3 PDCA loops | Escalate with score history + 5-Whys |
| Agent returns output that fails its own schema | Reject, ask for re-output, log to kaizen |

When escalating, the Orchestrator presents:
1. The original brief
2. The DMAIC packet so far
3. The score history (each iteration's audit score)
4. The 5-Whys root cause analysis
5. The recommended path forward

No escalation without evidence. No escalation without a recommendation.

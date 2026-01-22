# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

Personal "awesome list" curating research papers on **Medical World Models** - AI systems that learn environment dynamics for healthcare applications.

## L1-L4 Capability Framework

| Level | Name | Criteria |
|-------|------|----------|
| **L1** | Temporal Prediction | Predicts future states without action conditioning |
| **L2** | Action-Conditioned | Predictions depend on input actions/treatments |
| **L3** | Counterfactual Rollouts | Supports "what-if" analysis |
| **L4** | Planning & Control | Autonomous planning or real-time control |

## Adding a New Paper

Format in README.md:

```markdown
**Paper Title.** [Month Year] [Venue, Year]<br>
*Author1, Author2, et al.*<br>
`L{1-4}` `Domain` `Architecture`<br>
[[PDF](link)] [[Github](link)]

> One sentence description (optional)
```

## Inclusion Criteria

✅ Papers that **explicitly claim to be "World Models"**

❌ Papers not explicitly claiming to be world models

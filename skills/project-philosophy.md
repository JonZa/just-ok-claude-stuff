---
name: project-philosophy
description: Apply to all code reviews, refactoring, implementation decisions, and recommendations. Ensures outputs match the team's pragmatic, anti-over-engineering approach.
---

# Project Philosophy

## Core Principle

**"Fool-proof > bullet-proof"** — simple and reliable over complex and perfect.

## The Test

Before any recommendation, ask:

1. Can I understand this in 6 months?
2. Does the main component tell me 80% of what's happening?
3. Does this solve a problem we have _today_?

If no → don't recommend it.

## When to Extract (DRY)

- Genuinely reusable formatters/utilities
- Repeated markup → simple display components
- Logic used in 3+ places with identical behaviour

## When to Inline (WET)

- Prop drilling 3+ layers
- Type/mode switches that make components "smart"
- One-off helpers used once
- Logic scattered across 5+ files
- Abstractions that add cognitive load without clear benefit

## Always Keep in Parent

- Business logic
- Conditionals
- Data transformation decisions

Explicit over implicit. The parent tells the story.

## Anti-patterns to Flag

- Multi-mode "smart" components
- Premature optimization
- Defensive abstractions for hypothetical futures
- "Clever" code that sacrifices clarity
- YAGNI violations

## Refactoring Guidance

- Pass richer objects rather than drilling individual props
- Merge multi-mode components into explicit variants
- Consolidate related logic into single files
- Extract only what's genuinely reused

## Review Output Format

When reviewing code, provide a numbered list of actionable recommendations. Each should:

- Reference specific code
- Explain the actual (not theoretical) problem
- Propose the simplest fix

Omit: style nitpicks covered by linters, "consider adding" suggestions, future-proofing.

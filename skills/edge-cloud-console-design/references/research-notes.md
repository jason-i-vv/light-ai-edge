# Research Notes

## Anthropic frontend-design skill

Source: https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md

Useful ideas to adapt:

- Encode taste directly, not only implementation steps.
- Choose an aesthetic direction before coding.
- Explicitly blacklist generic AI patterns.

Adaptation:

- This product still needs a strong aesthetic direction, but the direction is not public-cloud polish. It is local edge k3s, frontier-tech operations, compact runtime telemetry, and practical control.

## gstack design workflow

Source: https://github.com/garrytan/gstack

Useful ideas to adapt:

- Treat AI slop as a first-class review category.
- Review design before implementation and verify with screenshots after implementation.
- Score completeness: information hierarchy, states, visual quality, and responsive behavior.

Adaptation:

- Keep this local skill narrow. It should guide the look and structure of a lightweight edge k3s console, not become a broad product workflow.

## User Product Constraint

The console manages a local k3s cluster for an edge product. It should not copy public cloud structure:

- No tenant hierarchy.
- No region/project/account concepts.
- No cloud-resource breadcrumb stacks.
- No billing or marketplace mental model.

The skill has two core jobs:

1. Aesthetic: make pages look like a frontier-tech edge console.
2. Engineering structure: keep pages aligned with a lightweight local k3s management product.

## Resulting Target

The output target is not "cloud console" and not "beautiful dashboard"; it is:

> A distinctive local edge k3s cockpit with flat navigation, dense runtime data, clear health signals, and safe operational actions.

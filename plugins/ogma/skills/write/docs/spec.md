# Specifications

Reference for [`write`](../SKILL.md).

A Specification records what a feature must do and why. Tests and implementation derive from it.

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md).

---

## Acceptance criteria

Number each acceptance criterion so Slices can cite it and tests can prove it.

Keep numbers stable while Slices are open. Add new criteria at the end rather than renumbering existing ones.

---

## Keep one document by default

Keep feature-specific technical decisions in **Constraints and decisions**.

Use an [ADR](adr-log.md) only when a rule binds work beyond the feature.

---

## Skeleton

```markdown
# <Feature name>

## Intent
<What problem this solves, for whom, and why now.>

## Behavior
<What the user or system can do, including edge cases.>

## Non-goals
- <what this leaves alone> — <where it will be handled>

## Constraints and decisions
- <constraint or decision> — <why> — <rejected alternative and why>

## Acceptance criteria
1. <observable outcome>
2. <observable outcome>

## Open questions
- <what remains unresolved> — <what would settle it>
```

Omit empty sections.

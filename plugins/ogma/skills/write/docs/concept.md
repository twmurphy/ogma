# Concept documents

Reference for [`write`](../SKILL.md).

A concept document explains how part of the system works when that explanation spans more than one feature. An [ADR](adr-log.md) records a rule.

**Read first:** [level set](../refs/level-set.md).

---

## When to write one

Keep the explanation in the [Specification](spec.md) until several features need it.

Write a concept document when a reader would otherwise need several Specifications to understand the same subsystem.

A concept document:

> Sessions are issued at sign-in, held server side, and checked on every request.

Not a concept document:

> This feature adds session revocation, so that support can sign a user out.

---

## Write what the code cannot show

Explain how the parts fit together, what must stay true, and why.

Do not restate functions, signatures, or call graphs.

Use one document per concept rather than per module. Crosscutting behavior such as authentication, retries, or error handling belongs in one place.

Describe the system as it works now.

---

## Filing

Store concept documents in `.ogma/docs/concept/` per [filing in the repository](../../file/refs/repository.md).

---

## Skeleton

```markdown
# <Concept name>

**Covers:** <paths, symbols, or routes this document explains>

## How it works
<how the parts fit together and why>

## Invariants
- <what must stay true> — <what breaks when it does not>

## In the code
<stable locators for the implementation>
```

Keep **Covers:** current as the code moves.

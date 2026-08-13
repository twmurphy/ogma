# Architecture decision records

Reference for [`write`](../SKILL.md).

An ADR records a rule that outlives the feature that produced it. Most decisions belong in the [Specification](spec.md).

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md).

**Lifecycle:** normative. The log states the rules in force.

---

## When to write one

Write an ADR when a decision binds future work beyond the feature that prompted it.

An ADR:

> All asynchronous jobs use mechanism X.

Not an ADR:

> This feature uses mechanism X because its workload requires Y.

Keep feature specific decisions in the Specification.

---

## Which form

Default to a log entry. The rule gets read on every plan. The argument behind it gets read once.

Write a full ADR when someone will need to reconstruct why the rule won without opening the issue that argued it.

---

## Skeleton: log entry

Each entry states one rule.

```markdown
## <Rule, stated so future work can follow it>

**Applies to:** <where the rule applies, and where it does not>
**Origin:** <issue or PR that argued it>
```

Replace an entry when its rule changes. Git holds the previous version.

---

## Skeleton: full ADR

```markdown
# ADR-<nn>: <Decision>

**Origin:** <Specification, issue, or PR, or "standalone">

## Context
<Why a decision was needed.>

## Decision
<State the rule so future work can follow it.>

## Applies to
<Where the rule applies. Where it does not.>

## Consequences
**Easier:** <what this enables>
**Harder:** <what this costs>

## Alternatives
| Option | Why it lost |
| --- | --- |
| <Alternative> | <Reason> |
```

Give the rule a log entry too, so planning finds it without reading the ADR. The log entry is the rule in force.

Update the ADR with its entry so both state the current rule.

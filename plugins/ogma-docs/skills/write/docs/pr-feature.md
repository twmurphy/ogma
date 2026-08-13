# Feature integration pull requests

Reference for [`write`](../SKILL.md).

A Feature PR merges a feature branch into the default branch. It asks whether the collected work is safe to ship. When a Specification governs the branch, it also asks whether the criteria were met.

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md).

**Lifecycle:** normative while open, historical once merged.

---

## Account for every criterion

When a Specification governs the branch, check every acceptance criterion in it.

Each criterion either passes or appears under **Deviations** with a reason. Write accepted deviations back to the Specification before merge.

Slice progress already shows what landed. Do not repeat it here.

## Closing keywords

Closing keywords belong here because this PR targets the default branch.

---

## Skeleton

````markdown
# <Feature name>

**Specification:** #100

## Outcome
<What the product can now do.>

## Validation
```bash
<command run against the assembled branch>
```

<result>

**Not checked:** <what remains unverified>

## Deviations
- <difference from the Specification> — <why>

## Limitations and follow-up
- <what remains, its cost, and where it will be handled>

## Release
<migration, deployment, or operational concerns; omit when none>

Closes #101
Closes #102
````

Omit the Specification line when none governs the branch.

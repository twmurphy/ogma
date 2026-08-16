# Bugs

Reference for [`write`](../SKILL.md).

A Bug records a defect, the evidence for it, and the proof it is fixed.

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md), [writing tests](../refs/writing-tests.md).

---

## Regression test

The reproduction is the criterion.

Check existing test coverage before adding the regression test. Prove the reported failure without duplicating what nearby tests already cover.

## Suspected scope

Write it as **Proposed**. The implementing agent may discard it when the evidence points elsewhere.

---

## Skeleton

````markdown
# <Defect summary>

**Integrates into:** `feature/<name>` or the default branch

## Impact
<Who is affected, how badly, and how often.>

## Defect
**Reproduction**
1. <Step>
2. <Step>

**Actual:** <what happens now> — `path/to/file.ts`, `SymbolName()`
**Expected:** <what should happen> — <criterion or requirement>
**Environment:** <version, platform, configuration>
**Last worked:** <known good state and what changed since>

```text
<log, trace, or failing output>
```

## Suspected scope
<Proposed location of the defect and the evidence behind the hypothesis.>

## Scope
**Change:** <what may change>
**Leave alone:** <what stays untouched and where it will be handled>

## Test contract
| Criterion | Proof | Level | Why this test exists |
| --- | --- | --- | --- |
| <the failure must not recur> | <how the test proves it> | <Unit / Integration> | <what this proves that nearby tests do not> |

## Verification
```bash
<command>
```
````

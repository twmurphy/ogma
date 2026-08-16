# Slices

Reference for [`write`](../SKILL.md).

A Slice is one vertical increment of a Specification that a fresh agent can implement, test, verify, and hand back in one session.

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md), [writing tests](../refs/writing-tests.md).

---

## Slice vertically

A Slice delivers one observable capability and crosses technical layers as needed.

Prefer:

> User can rename a project and see the new name after refresh.

Over:

> Add project rename database method.

Split by technical layer only when necessary. Say why.

---

## Size it for one session

A fresh agent should be able to implement, test, and verify the Slice in one session.

If it separates cleanly into two reviewable outcomes, make two Slices.

---

## Cite criteria

The Specification owns acceptance criteria. Keep its numbering and cite the criteria this Slice satisfies.

If the Slice needs a criterion that does not exist, add it to the Specification first.

---

## Link it to its Specification

Make the Slice a sub-issue of its Specification, and use issue dependencies for blocking Slices. Keep both out of the body.

Put the target branch in the body. The issue has no branch field.

---

## Skeleton

````markdown
# <Slice name>

**Integrates into:** `feature/<name>`

## Outcome
<What becomes possible once this lands, in observable terms.>

## Context
<Only what the agent needs beyond the Specification.>

## Scope
**Change:** <what may change>
**Leave alone:** <what stays untouched and where it will be handled>

## Touchpoints
- `path/to/file.ts` — <what it does today and its role here>
- `SymbolName()` — <role>

## Test contract
| Criterion | Proof | Level | Why this test exists |
| --- | --- | --- | --- |
| AC 2 — <criterion text from the Specification> | <how it is proven> | <Unit / Integration> | <what it proves> |

## Verification
```bash
<command to run before handing back>
```
````

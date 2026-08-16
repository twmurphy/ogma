# Issue pull requests

Reference for [`write`](../SKILL.md).

An Issue PR merges one issue's branch into its target branch. The same PR stays open through contract review and implementation review.

**Read first:** [level set](../refs/level-set.md), [tracking work](../refs/tracking-work.md), [writing tests](../refs/writing-tests.md).

---

## Contract review

Open the PR once the tests fail for the behavior they are missing.

The reviewer asks:

> If these tests pass, will they prove the issue?

Check that each test traces to a criterion, follows repository conventions, proves enough, and avoids redundant coverage.

---

## Implementation review

Update the same PR when the implementation passes the accepted contract.

Record what changed from the issue rather than repeating its plan. Cite criteria by identifier and call out decisions, deviations, contract changes, what was not checked, and risky areas.

An Issue PR targets the feature branch, or the default branch when the issue integrates directly. Link the issue in the header. Closing keywords belong on whichever PR targets the default branch.

---

## Skeleton: contract review

```markdown
# <Issue name> — contract review

**Issue:** #101

## Proof obligations
| Criterion | Test | Failing because |
| --- | --- | --- |
| AC 2 | `path/to/test.ts::name` | <missing behavior the test exposes> |

## Testing choices
<Why these tests use these boundaries and levels.>

**Untested on purpose**
- <what is untested> — <why>

## Scaffolding
- <fixture, helper, abstraction, or directory> — <why it was needed>
- <production code added only for testing, if any>
```

---

## Skeleton: implementation review

```markdown
# <Issue name>

**Issue:** #101

## Summary
<what changed from the issue, or "as specified in #101">

## Decisions
- <decision> — <why> — <rejected alternative and why>

## Deviations
- <difference from the expected approach> — <why>

## Test contract changes
- <what changed and what it now proves, or "none">

## Validation
Ran the issue verification. <result>

**Not checked:** <what remains unverified>

## Reviewer focus
1. <highest risk area and why>
```

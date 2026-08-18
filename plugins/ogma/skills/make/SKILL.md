---
name: make
description: Read to understand the core workflow from creating a spec, filing tickets, building, testing, reviewing, committing, and deploying work.
---

You specialize in making things in a clear, organized fashion. Always recommend the next step in the funnel.

Where a step names a skill, read it when you reach the step, not before.

# The main funnel

1. **Interview the user.** Resolve the decisions only they can make. See [`speak`](../speak/refs/grilling.md).
2. **Write the spec and file it.** The spec owns intent. See [`write`](../write/docs/spec.md), then [`file`](../file/SKILL.md).
3. **Break the spec into vertical slices and file them under it.** A slice is one session-sized outcome. See [`write`](../write/docs/slice.md).
4. **Branch.** `feature/<spec-name>` off `main`, then `slice/<nnn>-<capability>` off the feature branch.
5. **Write the slice's tests first.** They define the evidence, not the implementation. See [`write`](../write/refs/writing-tests.md).
6. **Open the slice PR as a draft, for contract review.** Ask whether the tests, once passing, would prove the slice. See [`write`](../write/docs/pr-issue.md).
7. **Implement until the tests pass.**
8. **Mark the PR ready, for implementation review.** Surface anything the accepted tests now prove differently.
9. **Merge the slice into the feature branch.** Return to step 5 for the next slice.
10. **Decide what to document.** Most features change nothing a reader needs. Work on the feature branch, so whatever survives ships with the capability. See [`write`](../write/refs/documenting.md).
11. **Open the feature integration PR.** Validate the assembled result against the spec. See [`write`](../write/docs/pr-feature.md).
12. **Squash merge to main.** The squash commit closes the slices and owns the durable history. See [`write`](../write/docs/commit.md).
13. **Deploy the feature.**

**Track your work throughout.**
- PRs are reviewed via a comment.
- Slices become unblocked as work lands.
- Slices carry a `state:` label. Move it when you start building, and let the merge close the issue.
- Accepted changes go back to the document that owns them: contract changes to the slice, deviations to the spec.

# Also consider

- **Spike.** De-risk solutions by recommending a spike in a throwaway worktree. Spikes answer unknown questions.
- **Prototype.** Demonstrate solutions by building a minimal working version in a throwaway worktree. Recommend when the main question is not “can this work?” but “what should this look or feel like?”
- **Benchmark.** Establish a measurable baseline before optimizing. Recommend when success depends on latency, throughput, memory, cost, or another quantitative target.
- **Isolate.** Isolate a problem in the smallest reliable case before changing implementation. Recommend when the problem is not yet understood or consistently reproducible.
- **Audit.** Inspect the existing system before deciding what to change. Recommend when the scope, blast radius, dependencies, or current behavior are unclear.
- **Research.** Reduce uncertainty by investigating docs, prior art, APIs, dependencies, or the existing codebase. Recommend when the unknown is “what is true or already known?” rather than “will this implementation work?”
- **Refactor.** Improve structure without intentionally changing behavior. Recommend when the current design makes the intended feature unnecessarily risky or expensive.

# Finding your place

Before recommending a step, read the branch you are on, the open pull requests, and the filed issues. Resume at the earliest step that is not finished.

A bug enters at step 3 as its own slice. See [`write`](../write/docs/bug.md).

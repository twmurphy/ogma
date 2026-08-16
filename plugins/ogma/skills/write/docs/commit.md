# Commits

Reference for [`write`](../SKILL.md).

Working commits and squash commits serve different readers.

---

## Working commits

Use working commits for review and debugging on issue and feature branches.

Follow the repository convention. Keep each commit logical and name what changed.

Keep the explanation in the Issue PR.

---

## Squash commits

The squash commit into the default branch records what entered the product and why.

Write for someone reading `git log` with no other document open. Name the capability in product terms and describe only what actually shipped.

Mention deferred, removed, or gated behavior when it changes what the commit delivered.

---

## Skeleton

```text
<capability, one line>

<What the user or system can now do.>

<Implementation detail a future reader needs, if any.>

BREAKING CHANGE: <what breaks and what to do about it>
```

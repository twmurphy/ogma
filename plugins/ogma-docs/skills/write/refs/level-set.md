# Level set

Shared reference for [`write`](../SKILL.md).

Use this when the reader starts without prior context and must be able to verify what they read.

---

## Write for a cold start

The writer may know things the reader does not.

Assume the reader has only the repository and this document. Assume no prior chat, agent memory, or undocumented discussion.

---

## Ground every claim

Separate what is required, what exists, and what is planned.

* **Required.** What must be true. Trace it to the document, issue, or decision that requires it.
* **Observed.** What is true now. Cite where you found it.
* **Proposed.** What will change. Write it as planned work.

Inspect the repository before describing existing code. Write planned files, interfaces, behavior, and architecture in the future tense so the reader can tell what exists from what will change.

Cite existing code with the most stable locator available: file path, symbol, interface, route, schema, test, or configuration key.

```text
src/auth/session.ts
SessionStore.revoke()
POST /sessions/:id/revoke
UserSession model
```

Line numbers change as code changes. Include them only when they make something easier to find.

If a decision is unresolved, say so. Do not fill the gap with a guess.


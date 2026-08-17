# Documenting a feature

Shared reference for [`write`](../SKILL.md).

Use this once the slices have merged and before the feature pull request. Read the feature branch against the default branch and decide what, if anything, a reader now needs.

---

## Start from no change

Most features change nothing a reader needs. Expect to write nothing, and let the exceptions argue for themselves.

Documentation earns its place when a reader needs something the repository cannot give them cheaply. Everything else is a second copy of the repository, written in prose, going stale on its own schedule.

---

## The test

Take each thing the feature changed and ask two questions in order.

**Who needs this?** Name the reader and what they are trying to do. When you cannot name one, there is nothing to write.

**Can they get it from the code?** Signatures, routes, config keys, directory layout — the repository answers these already, and stays right for longer. Write what the code cannot show: how the parts fit together, what must stay true, and why a choice binds later work.

A third question shapes what you write rather than whether to write it. **Will this still be true next month?** A detail that moves with every feature belongs in an abstraction, or nowhere.

---

## Four outcomes

Give every affected document one.

| Outcome | When |
| --- | --- |
| **Nothing** | the usual answer |
| **Update** | a document you already have now states something false |
| **Delete** | its subject is gone and no reader is looking for it |
| **Create** | knowledge passed the test and no document owns it |

Delete is the one that gets skipped. A document describing a capability the feature removed is worse than no document, because a reader trusts it.

---

## Where it goes

| What the feature changed | Where it goes |
| --- | --- |
| A rule that binds future work | an [ADR](../docs/adr-log.md) |
| An explanation several features need | a [concept document](../docs/concept.md) |
| What the project is, or how to try it | the [README](../docs/readme.md) |
| Why this feature works the way it does | its [Specification](../docs/spec.md), already filed |
| Anything else | nothing |

The README goes under the test like everything else. Most features leave what the project is untouched.

---

## Say what you passed over

Report the decision, not only the edits. Name what you changed, and say how much you read and left alone. A reader who sees only the edits cannot tell a careful pass from a skipped one.

When knowledge passes the test but the repository holds no reason for it — a dependency swapped with no recorded argument — say so and ask. A reason you invent reads exactly like one you were told.

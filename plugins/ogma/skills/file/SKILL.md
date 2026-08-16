---
name: file
description: Filing documents and tickets. Use when creating a GitHub issue or pull request, labeling or linking work, deciding where a document belongs, or organizing documents in a repository.
---

Use this to put a document where it belongs and keep it findable. The [`write`](../write/SKILL.md) skill governs what the document says. This one governs where it lands, what carries its state, and how it connects to the work around it.

A document nobody can find is a document nobody reads. File it as you finish it, not later.

## Routing

Read the reference for where the document lives.

| Where it lives | Read |
|---|---|
| An issue or a pull request, on GitHub | [refs/github.md](refs/github.md) |
| A document in the repository | [refs/repository.md](refs/repository.md) |

---

## File it where the next reader will look

Check for an existing home before you invent one. A convention already in the repository, a path a tool expects, an issue that already tracks the work — each beats a new location, even a tidier one.

When nothing exists, follow the reference for that destination. One home per kind of document, named after the kind.

---

## Let the platform own what the platform tracks

Status, assignee, labels, type, milestone, dependencies, and parent and child links belong to whatever system tracks them. Record each one there, once.

Keep the same state out of the body. Two copies drift, and the reader cannot tell which one is current. The body carries meaning, reasoning, scope, and acceptance — the things the platform has no field for.

[Filing on GitHub](refs/github.md) names what the platform carries for an issue.

---

## Link to what it came from

Every document names what it derives from, using the identifier the platform already assigned. `#100` beats a name you made up, because it resolves.

A document with no link back is an orphan. Someone will rewrite it rather than find it.

---

## Normative or historical

Every document is one or the other, and it decides what you do when reality moves.

* A **normative** document governs current work. Update it in place when intended behavior changes, so it keeps stating what is true now.
* A **historical** document records what was decided at the time. Supersede it with a new document rather than rewriting it.

Each document reference declares which one it is. Check it before you edit anything already filed.

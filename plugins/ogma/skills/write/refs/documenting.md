# Documenting a feature

Reference for [`write`](../SKILL.md).

Use this after the Slices merge and before the Feature PR. Compare the feature branch with the default branch and decide whether any documentation must change.

---

## Start with nothing

Most features need no documentation change.

Write only what a reader cannot recover cheaply from the repository: how parts fit together, what must stay true, or why a choice matters later.

---

## Test each change

Ask:

1. **Who needs this?** Name the reader and what they need to do. If no reader needs it, stop.
2. **Can the repository show it?** Leave signatures, routes, config keys, and directory layout to the code.
3. **Will it stay true?** Do not document details that change with every feature.

---

## Choose an outcome

For each affected document, choose one:

| Outcome     | Use when                                               |
| ----------- | ------------------------------------------------------ |
| **Nothing** | No reader needs a documentation change                 |
| **Update**  | The document now says something false                  |
| **Delete**  | The document describes something that no longer exists |
| **Create**  | Readers need durable knowledge that no document owns   |

---

## Put it in the right place

| What changed                         | Where it belongs                       |
| ------------------------------------ | -------------------------------------- |
| A rule that binds future work        | [ADR](../docs/adr-log.md)              |
| An explanation several features need | [Concept document](../docs/concept.md) |
| What the project is or how to try it | [README](../docs/readme.md)            |
| Anything else                        | Nowhere                                |

A feature's own reasoning already sits in its [Specification](../docs/spec.md). Deviations go back to it at the Feature PR, not here.

A document a reader cannot find is a document they do not have. When you create one, check that the [README](../docs/readme.md) points at the documentation it lives in, and update the README when nothing does.

---

## Report what you checked

Say what you updated, deleted, created, and left unchanged.

If documentation needs a reason the repository does not contain, ask for it. Do not invent one.

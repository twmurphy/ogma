# Tracking work

Shared reference for [`write`](../SKILL.md).

Use this for the rules every tracking document shares.

---

## When documents disagree

Follow the document that owns the disputed point.

* **Specification** wins on behavior, decisions, constraints, and acceptance.
* **Issue** wins on scope, proof obligations, and its test contract, so long as they agree with any Specification that governs it.
* **Issue PR** records what was reviewed and implemented. Write accepted contract changes back to the issue.
* **Feature PR** records integration and deviations. Write accepted deviations back to the Specification that governs them.
* **ADR** wins on the architectural rule it records, within its stated scope.
* **Commits** carry no authority. If a commit message disagrees with its PR or Specification, the commit message is wrong. A merged squash commit cannot be corrected by superseding it, so get it right before merge.

When documents disagree, surface the contradiction and update the document that owns it. If no one has resolved it, say so.

---

## Trace to the parent, carry only what you need

Every document that directs implementation links to what it derives from.

```text
Specification
  ├── Slice
  │    └── Issue PR
  └── Feature PR

Bug
  └── Issue PR

ADR
  may begin in a Specification,
  then stands alone as a current rule

Commit
  inherits from Git history and its PR
```

Name exactly what the child inherits. Use identifiers the platform already provides. #100 beats one you invent.

Carry enough from the parent for the reader to act. Copy too much and the copies drift. Copy too little and the reader must keep returning to the parent.

If changing one sentence means changing the same prose in several tracking docs, you copied too much.

---

## Make done observable

Write acceptance criteria as behavior a person or test can observe.

Prefer:

> When a user revokes an active session, subsequent requests using that session are rejected and the session no longer appears in the active-session list.

Over:

> Improve authentication cleanup.

The first can be tested. The second cannot.

---

## State the boundaries

Mark where the work stops.

State:

* what is out of scope
* which systems and modules stay untouched
* which existing abstractions to reuse
* which compatibility and performance limits must hold
* which work is deferred

---

## Preserve rationale

Code shows what exists. Record why a choice won when that choice constrains later work.

Leave out deliberation that changes nothing later.

---

## Let metadata own state

When the platform already tracks status, assignee, labels, issue type, milestone, dependencies, or parent and child links, use it.

Do not repeat the same state in prose. Two copies will drift.

Use the document body for meaning, reasoning, scope, and acceptance.

[Filing remotely](file-remote.md) names what GitHub carries for an issue.

---

## Normative or historical

Every tracking doc is either normative or historical.

* A **normative** doc governs current work. Update it when intended behavior changes.
* A **historical** doc records what was decided at the time. When reality changes, supersede it rather than rewriting it.

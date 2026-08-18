# Review

Reference for [`speak`](../SKILL.md).

Use this when discussing or reviewing code with the user, and when walking them through any other work for approval.

Help the user make decisions while learning how their own system works. They need enough of the real thing in front of them to push back on you, and to still understand it after the change. Show the code. Do not describe it and expect that to land.

A review runs over multiple turns. Present one finding at a time and get it approved before moving to the next.

Findings can range from "Why this is good", to "How this could be better", to "Why this must change"

---

## Shape of a review turn

```markdown
<review start>
<opening prose>
---
# <Object Being Reviewed>
<link to object> - <status>

<turn start - repeat from here>
---
<block of code, content, and/or file tree>
<your review findings + severity>
---
<footer>
```

Open with a file tree. Ground the conversation in where the work sits before saying anything about it, and mark the files in play.

Work through feedback from the user on each turn until all are approved, then recommend the next natural step.

---

## Clarify the state of what you show

Label each thing you present so its state is clear.

* **As it stands** -- what you read. Quote it unchanged.
* **What was changed** -- edits already made. Say they are made.
* **Proposed** -- not written yet. Say it is not written yet.

---

## Show, don't tell

Quote the smallest excerpt that carries the point, with its path and line. Real lines from the real files, not a paraphrase.

Say why the code is shaped that way, not only what to change about it -- the reason is the part that transfers.
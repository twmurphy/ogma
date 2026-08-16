# Coding

Reference for [`speak`](../SKILL.md).

Use this when discussing or reviewing code with the user.

Help the user make decisions while learning about the codebase. They need enough of the codebase in front of them to push back on you, and to still understand how their own system works after the change. Show the code. Do not describe it and expect that to land.

---

## Hold the order

conversational intro → file tree → what this is about → the code → recommendation or approval

**Open with a file tree.** Ground the conversation in where it sits before saying anything about it. Mark the files in play. Draw it as plain lines outside a code fence.

```markdown
src/api/
├── routes/
│   ├── auth.ts        ← the check runs here
│   └── users.ts
└── middleware/
    └── session.ts     ← and here, again
```

**Level-set on the what.** The ticket, the PR, the problem raised, the failing run. Link it. If there is no link, say where it came from. No template beyond this: the user should be able to read your response without opening another tab to work out what it concerns.

**Then the code.** Real lines from the real files, with paths, not a paraphrase.

**End with a [recommendation](recommendation.md) or an [approval](approvals.md).** A code conversation that ends in neither has left the user with nothing to do.

---

## Clarify the code state

Label what you present so its state is clear.

* **The code** -- code you read. Quote it as it stands.
* **What was changed** -- edits already made. Say they are made.
* **Proposed changes** -- not written yet. Say it is not written yet.


---

## Show, don't tell

Quote the smallest excerpt that carries the point, with its path and line. Say why the code is shaped that way, not only what to change about it -- the reason is the part that transfers.

Alternate prose and blocks. Every block gets a line after it saying what it shows.

# Skills

Reference for [`write`](../SKILL.md).

Skills add frontmatter and an invocation choice. `AGENTS.md` and `CLAUDE.md` do not.

---

## Invocation

A skill is either model invoked or user invoked.

### Model invoked

Use model invocation when the agent must discover the skill on its own or another skill must reach it.

```yaml
description: <what the skill does and when to use it>
```

Omit `disable-model-invocation`.

The description stays in context on every turn, so keep it tight. Apply the routing rules in [`write`](../SKILL.md).

### User invoked

Use user invocation when the human can choose the skill directly.

```yaml
disable-model-invocation: true
description: <short human-facing summary>
```

The agent cannot discover or invoke it. Another skill cannot invoke it either.

This removes always loaded routing cost but requires the human to know when to use the skill.

Choose model invocation only when discovery is worth that cost.

---

## Shared reference

When several user invoked skills need the same material, put it in a plain file and route each skill to it.

Make a separate model invoked skill only when the reference must be independently discoverable.

---

## Split by invocation

Split work into another skill when it needs its own route or another skill must reach it independently.

Each model invoked skill adds another description to every turn. Give it its own skill only when that reach matters.

For sequence based splitting, use [`write`](../SKILL.md).

---

## Router skills

When humans have too many user invoked skills to remember, add one user invoked router.

The router names each skill and when to use it.

It can point to those skills but cannot invoke them.

---

## Project instruction files

`AGENTS.md` and `CLAUDE.md` are loaded whole on every turn. Keep only instructions worth paying for every time.

Use them for:

* conventions the codebase cannot reveal
* gotchas that prevent wrong turns
* routes to deeper skills and docs

Put elsewhere:

* facts already available from scripts, config, or `--help`
* behavior the agent already follows
* instructions only some tasks need

Route instead of carrying detail.

Remove any line that does not change behavior. Revisit these files and cut as readily as you add.

---
name: write
description: Writing documents for agents. Use for writing anything other than code: when creating or editing a skill, AGENTS.md, CLAUDE.md, README, specification, slice, bug, ADR, pull request description, or commit message.
---

Use this as a reference whenever you're writing a document that an agent will consume, whether that's a skill, an `AGENTS.md` or `CLAUDE.md` file, a spec or pull request description, or a doc the agent reaches through a pointer. The packaging may change, but the writing principles stay the same. The goal is predictability: you want the agent to follow the same process every time, not produce the exact same output.

## Routing

Read the file for the document you are writing. Each one names the shared references it needs.

| What you're writing | Read |
|---|---|
| A skill, `AGENTS.md`, or `CLAUDE.md` | [docs/skill.md](docs/skill.md) |
| A README | [docs/readme.md](docs/readme.md) |
| An Issue for a Specification | [docs/spec.md](docs/spec.md) |
| An Issue for a Slice | [docs/slice.md](docs/slice.md) |
| An Issue for a Bug | [docs/bug.md](docs/bug.md) |
| An ADR | [docs/adr-log.md](docs/adr-log.md) |
| A PR for one Issue | [docs/pr-issue.md](docs/pr-issue.md) |
| A PR for a Feature Branch | [docs/pr-feature.md](docs/pr-feature.md) |
| A commit message | [docs/commit.md](docs/commit.md) |

## Filing

Once the document is written, the [`file`](../file/SKILL.md) skill governs where it goes and what carries its state.

## Skeletons

Follow the skeleton in the reference. It is the standard, not a starting point. Keep its sections, in its order, under its names.

Fill every section you can from the repository, the request, and the conversation.

When a section needs content you cannot derive, offer the user a short set of options to choose from. A concrete choice is easier to answer than an open question. Each reference names the offers it expects.

Omit a section only when the document genuinely has none. Add a section only when the reader needs it to act.

---

## Routing statements

A **routing statement** is a short reference that tells the agent where to find more information and when to use it. A skill description is a routing statement. So is a line in `AGENTS.md` that sends the agent to another doc.

The wording matters more than the target. It is what helps the agent decide when to follow a route. If an important doc sits behind a vague routing statement, the agent may never reach it. Fix the wording first. Only move the content into the main context if clearer routing still does not work reliably.

A routing statement has two jobs: say what the material is, and define the **routes** that should lead to it. Different runs may take different routes.

Because routing statements may be loaded on every turn, keep them especially tight:

* **Lead with the most important word.** That is where the routing starts.
* **Use one trigger per route.** If two phrases describe the same route, keep just one.
* **Do not repeat what the target already makes clear.**

---

## Costs

Every doc has a cost. The useful question is where that cost should live.

* **Context overhead** is the cost paid by the agent. Anything that stays in context on every turn takes up tokens and attention, even when it is not needed. That includes lines in `AGENTS.md`, skill descriptions, and other always loaded instructions.

* **Cognitive load** is the cost paid by the human. If a doc is not surfaced automatically, someone has to remember that it exists, know what it is for, and recognize when to use it.

Neither cost is automatically bad. The goal is to put the cost in the right place. If the agent should reliably find a doc on its own, give it a routing statement. The agent then carries only that small bit of context until the doc is needed. If human judgment should decide when a doc matters, you may not need a routing statement at all. That saves context, but it means the human has to remember when to reach for the doc.

Spend context where reliable agent behavior matters. Accept cognitive load where human judgment matters.

---

## Information hierarchy

A doc usually contains two kinds of information:

* **Steps** tell the agent what to do and in what order.
* **Reference** gives the agent rules, definitions, or facts to use when needed.

A doc can be all steps, all reference, or a mix of both.

The important question is where each piece belongs. Think of the doc as a simple hierarchy:

1. **In-file steps** are the main path. These are the actions the agent needs to follow.
2. **In-file reference** stays nearby for the agent to consult when needed. It is fine for reference to be flat when the pieces are true peers, such as a set of review rules.
3. **Disclosed reference** lives in another doc and is reached through a routing statement. The agent loads it only when that route is relevant.

The goal is to keep the most important information closest to the agent. Keep too much in the main doc and the important parts get buried. Move too much out and the agent has to go looking for information it needs all the time.

Three principles help keep that hierarchy working:

* **Progressive disclosure** keeps occasional information out of the main path. Keep what every route needs in the main doc. Move what only some routes need behind a routing statement. This is not just about saving context. It keeps the process easy to see and follow.

* **Co-location** keeps related information together. Put a concept's definition, rules, and caveats in the same place so the agent gets the full picture when it reaches them. Avoid both duplication, where the same idea appears more than once, and scattering, where one idea is spread across the doc.

* **Sprawl** is a sign that the hierarchy needs another pass. A doc can become too large even when every line is useful. When that happens, move reference behind routing statements or split distinct routes so each path carries only what it needs.

---

## Steps and completion criteria

A step should tell the agent both **what to do** and **when it is done**.

That second part matters more than it may seem. If "done" is vague, the agent has room to stop early. Early stopping becomes more likely when the agent can already see the next step and starts moving toward it.

So start by making the finish line clear.

* **Make it easy to check.** Prefer "account for every modified model" over "review the changes."
* **Require enough work.** The finish line should require the depth of work you actually want, not just a plausible output.

You do not need to describe every bit of work along the way. A good finish line gives the agent a reason to keep digging until the work is actually complete.

This idea also applies when the doc is mostly rules rather than steps. "Apply every relevant rule" tells the agent to work through the full set, even without a sequence to follow.

---

## When to split

Keep a doc together by default. Split it when the boundary changes what the agent sees or which instructions it receives.

* **Split a sequence** when later steps need to stay out of context until the current work is complete.
* **Split by route** when different situations need different instructions. Keep the shared guidance together, and load the rest only when that route needs it.

A split should earn its extra routing and cognitive load. If it does not change the agent's behavior or context in a useful way, keep the doc together.

For skill-specific mechanics, see [docs/skill.md](docs/skill.md).

---

## Leading words

A **leading word** is a familiar word or phrase that carries a lot of meaning in very little space. Terms like *lesson*, *fog of war*, or *tracer bullets* already come with ideas the agent understands.

Used well, a leading word can save repetition and give the agent a consistent idea to work from.

But use them sparingly. A doc full of coined terms and labels may be efficient for the agent while becoming harder for a person to read. If a term sounds like jargon, needs its own glossary, or makes the sentence less natural, it is probably not helping.

Prefer leading words that already work in normal conversation. The reader should understand the sentence even if they have never seen the doc before.

A good leading word helps when:

* **It replaces real repetition.** If you keep explaining the same idea, a short familiar label may be useful.
* **It stays natural in the sentence.** The term should make the writing easier to read, not more coded.
* **It carries meaning the agent already knows.** Prefer familiar language over invented terminology.

This can also help routing. When the same natural term appears in prompts, docs, and code, it gives the agent a stronger hook for finding the right material.

Do not invent a term just to make an idea feel more precise. If plain language works, use plain language.

---

## Positive instructions

**Write positive instructions.** Tell the agent what to do, not what to avoid. Negation still puts the unwanted behavior into context and can make it more salient. Use a prohibition only when you need a hard guardrail, and always pair it with the behavior you want instead.

---

## Pruning

Good docs get shorter over time, not just longer. Revisit them regularly and remove anything that no longer earns its place.

* **Keep one source of truth.** If the same instruction appears in more than one place, it can drift and become harder to maintain. Put the rule in one authoritative place and route to it when needed.

* **Let the environment speak for itself.** Scripts, config files, directory structure, and `--help` output already contain useful facts. Do not copy those facts into a doc unless looking them up is genuinely difficult. Use the doc for what the environment cannot tell the agent: conventions, reasons, tradeoffs, and gotchas.

* **Remove what is no longer relevant.** A line may never have belonged there, may belong behind a routing statement, or may simply have gone stale. Shorter docs make stale guidance easier to notice. Without regular pruning, old guidance tends to pile up because adding feels safer than deleting.

* **Delete instructions that do not change behavior.** If the agent already does something by default, telling it to do the same thing adds context without helping. Test the instruction against actual behavior. If removing it changes nothing, leave it out.

When a sentence does not earn its place, delete the sentence. Do not keep trimming words from an instruction that does no useful work.

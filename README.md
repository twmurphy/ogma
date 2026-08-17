# O.G.M.A.

Ogma's Guide to Making Anything.

Ogma is a Claude Code marketplace for the work that surrounds the code. Its plugins give an agent a repeatable process for writing documents, tracking work, and handing it off, so the output holds up whoever prompts it and whenever they do.

## Quick start

Add the marketplace and install the plugin:

```bash
/plugin marketplace add twmurphy/ogma && /plugin install ogma@ogma
```

Name what you want to build. The `make` skill walks the funnel and recommends each step:

```text
Let's build session revocation.
```

## Features

* Sequences a feature from interview to spec, slices, tests, review, and merge, so the agent always knows the next step
* Routes each document type to its own reference, so only the rules that apply reach the agent's context
* Covers skills, `AGENTS.md`, `CLAUDE.md`, READMEs, specifications, slices, bugs, ADRs, pull requests, and commit messages
* Gives each document a skeleton to follow, and names what to ask you when a section needs content the repository cannot supply
* Settles authority between documents, so a spec, an issue, and a commit that disagree have a defined winner
* Files each document where it belongs, in the repository or on GitHub, and lets the platform carry its state
* Gives replies in conversation their own shape — grounded in a diagram or the real code, and ending in something for you to decide

## Usage

### Work through a feature end to end

`make` owns the order the others run in, from interview to spec, slices, tests,
review, and merge. It recommends the next step rather than waiting to be told,
and it hands each one to the skill that governs it.

You can also join a feature already in progress. It reads the branch, the open
pull requests, and the filed issues to work out where you are:

```text
What's next here?
```

### Write a new document

Name the document and the agent routes itself:

```text
Write an ADR for the decision to keep issue state in GitHub metadata.
```

### Edit an existing document

The same skill covers revision. It applies the reference for that document type to what is already written:

```text
Review this slice against the acceptance criteria and tighten the test contract.
```

### Write the docs your agents read

`write` covers its own medium. Use it on the files that steer the agent itself:

```text
Turn these notes into a skill.
```

### File it where it belongs

`file` takes over once the document exists. It picks the destination, sets the labels and links, and leaves the state to the platform:

```text
File this spec as an issue with its slices underneath it.
```

### Shape the conversation, not just the documents

`speak` covers replies rather than files. It holds a response to one main point,
grounds it in a diagram or the real code, and closes on an approval or a
recommendation, so every turn leaves you something to answer:

```text
/ogma:speak
```

## Documentation

* [`make` skill](plugins/ogma/skills/make/SKILL.md) — the order the work happens in, and which skill governs each step
* [`write` skill](plugins/ogma/skills/write/SKILL.md) — routing, information hierarchy, and the principles behind the references
* [Document references](plugins/ogma/skills/write/docs) — one per document type
* [Shared references](plugins/ogma/skills/write/refs) — cold-start writing, tracking work, and test proof
* [`file` skill](plugins/ogma/skills/file/SKILL.md) — where a document goes, on GitHub or in the repository
* [`speak` skill](plugins/ogma/skills/speak/SKILL.md) — the rules the agent applies to its own replies

## Requirements

Claude Code.

## License

[MIT](LICENSE)

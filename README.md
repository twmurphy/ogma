# O.G.M.A.

Ogma's Guide to Making Anything.

Ogma is a Claude Code marketplace for the work that surrounds the code. Its plugins give an agent a repeatable process for writing documents, tracking work, and handing it off, so the output holds up whoever prompts it and whenever they do.

## Quick start

Add the marketplace and install the plugin:

```bash
/plugin marketplace add twmurphy/ogma && /plugin install ogma@ogma
```

Ask for a document. The `write` skill loads itself and routes to the right reference:

```text
Write a spec for the session revocation feature.
```

## Features

* Routes each document type to its own reference, so only the rules that apply reach the agent's context
* Covers skills, `AGENTS.md`, `CLAUDE.md`, READMEs, specifications, slices, bugs, ADRs, pull requests, and commit messages
* Gives each document a skeleton to follow, and names what to ask you when a section needs content the repository cannot supply
* Settles authority between documents, so a spec, an issue, and a commit that disagree have a defined winner
* Files each document where it belongs, in the repository or on GitHub
* Carries the same rules into how the agent talks to you, not just what it writes down

## Usage

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

### Hold the agent to the same rules out loud

`speak` applies the writing rules to the agent's replies, so a chat answer reads
like the documents it produces:

```text
/ogma:speak
```

## Documentation

* [`write` skill](plugins/ogma/skills/write/SKILL.md) — routing, information hierarchy, and the principles behind the references
* [Document references](plugins/ogma/skills/write/docs) — one per document type
* [Shared references](plugins/ogma/skills/write/refs) — cold-start writing, tracking work, test proof, and filing
* [`speak` skill](plugins/ogma/skills/speak/SKILL.md) — the rules the agent applies to its own replies

## Requirements

Claude Code.

## License

[MIT](LICENSE)

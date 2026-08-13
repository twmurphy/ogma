# Filing remotely

Shared reference for [`write`](../SKILL.md).

Use this to file an issue or a pull request. Both live on GitHub, so this covers what the platform carries, what stays in the body, and the commands that put them there.

The body follows [tracking work](tracking-work.md) and the reference for the document you are writing.

---

## Check the floor first

`--parent` and `--blocked-by` arrived in `gh` 2.96. Run this once before the first issue you file:

```bash
gh --version && gh auth status && gh repo view --json nameWithOwner -q .nameWithOwner
```

Below the floor, say which check failed and stop. An older `gh` does not error on the sub-issue flags — the relationships go missing silently, and every later reader takes absent for empty. A Specification with Slices looks like a plain issue. Blocked work looks ready. Each is a wrong answer in the shape of a right one, so upgrade rather than filing without the links.

---

## What an issue carries

| What | Where it goes |
| --- | --- |
| Title | the issue title, not a heading in the body |
| Type | a `type:` label |
| State | a `state:` label |
| Parent | `--parent`, the Specification's issue number |
| Blockers | `--blocked-by` |
| Identifier | the number GitHub assigns |

Everything else stays in the body: intent, scope, acceptance, test contract. Write the body from its document reference and drop whatever the metadata now carries.

---

## Labels

GitHub's native issue type is an org-level field most repositories cannot use, so type is a label here. Labels filter too, which is what makes `gh issue list --label "type:bug"` work.

Namespace both axes so they cluster in the label list rather than scattering alphabetically.

### type — which document governs it

| Label | The issue holds |
| --- | --- |
| `type:spec` | a [Specification](../docs/spec.md) |
| `type:bug` | a [Bug](../docs/bug.md) |

A [Slice](../docs/slice.md) carries no type label. Being a sub-issue of a `type:spec` issue is what identifies it.

A repository tracks work this skill has no document for, such as upkeep or a small adjustment to existing behavior. Add a label for that lane when the project needs to filter on it.

### state — where it is

One per **buildable** issue, meaning one with no sub-issues. A Specification wears none, because its state is the roll-up of its Slices.

| Label | Meaning |
| --- | --- |
| `state:backlog` | filed, not planned |
| `state:ready` | buildable now, subject to its blockers |
| `state:in-progress` | being built |

File at `state:backlog` unless the work is planned and can start now. Whoever builds it moves the label on. The terminal states are GitHub's own close reasons, completed or not planned, rather than labels.

An issue is buildable only when it is `state:ready` and unblocked, so read the dependency rather than the label alone.

### Creating them

`--force` updates an existing label instead of erroring, which is what makes a re-run safe. One color per axis, so the grouping is visible rather than only alphabetical.

```bash
gh label create "type:spec" --color 1D76DB --description "A capability, its decisions, and its acceptance criteria" --force
gh label create "type:bug"  --color 1D76DB --description "A defect, its evidence, and its regression test" --force

gh label create "state:backlog"     --color 0E8A16 --description "Filed, not planned" --force
gh label create "state:ready"       --color 0E8A16 --description "Buildable now, subject to its blockers" --force
gh label create "state:in-progress" --color 0E8A16 --description "Being built" --force
```

---

## Filing an issue

Write the body to a file and pass `--body-file`. Markdown through `--body` gets mangled by shell quoting, and bash and PowerShell mangle it differently.

```bash
gh issue create --title "Session revocation" --body-file spec.md --label "type:spec"
gh issue create --title "Revoke endpoint" --body-file slice-01.md --label "state:ready" --parent 100 --blocked-by 99
```

Add relationships to an issue that already exists:

```bash
gh issue edit 102 --parent 100 --add-blocked-by 101
```

Update a normative issue in place, so the issue keeps stating current intent:

```bash
gh issue edit 100 --body-file spec.md
```

---

## Reading issue structure

Cite the numbers GitHub assigned rather than inventing your own. Read them with `gh`'s own `-q`, not a piped `jq`: `jq` is not guaranteed on the machine, and `-q` behaves the same under bash and PowerShell because `gh` is the interpreter.

| Want | Command |
| --- | --- |
| Sub-issue numbers | `gh issue view <n> --json subIssues -q '.subIssues.nodes[].number'` |
| Blockers | `gh issue view <n> --json blockedBy -q '.blockedBy.nodes[].number'` |
| Parent | `gh issue view <n> --json parent -q '.parent.number'` |
| Completed sub-issues | `gh issue view <n> --json subIssuesSummary -q '.subIssuesSummary.completed'` |

`parent` is a flat object. The connection fields nest under `.nodes`, so a wrong path reads empty and empty reads as none.

---

## Filing a pull request

| What | Where it goes |
| --- | --- |
| Title | the PR title |
| Target | `--base`, so the body never restates it |
| Review phase | draft while the contract is under review, ready once implementation lands |
| Issue link | the body, as `**Issue:** #101` |

An [Issue PR](../docs/pr-issue.md) bases on its feature branch. A [Feature PR](../docs/pr-feature.md) bases on the default branch. `--head` defaults to the current branch.

Open an Issue PR as a draft, because contract review asks a different question than implementation review:

```bash
gh pr create --base feature/session-revocation --title "Revoke endpoint — contract review" --body-file pr.md --draft
```

One PR carries both reviews, so replace the body when the implementation passes the accepted contract rather than opening a second PR:

```bash
gh pr edit 42 --title "Revoke endpoint" --body-file pr.md
gh pr ready 42
```

`--body-file` for the same reason it applies to issues.

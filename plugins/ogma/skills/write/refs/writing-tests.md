# Writing tests

Shared reference for [`write`](../SKILL.md).

Use this to define what tests must prove and how to record that proof.

Read it when writing a Slice, Bug, or Issue PR.

---

## Tests prove code

A test is code that runs against the code being changed. The test contract covers that code and nothing else.

Prove prose and documentation by reading them. A skill, `AGENTS.md`, README, ADR, Specification, or any other document earns its proof through acceptance criteria and review.

When one Slice or Bug changes both, write the contract for the code and leave the documents to review. When it changes only documents, say so in place of the contract and let verification be the review.

---

## Where proof sits

```text
Specification defines truth
        ↓
Slice selects what must be proven
        ↓
Test contract defines the proof
        ↓
Tests provide the proof
        ↓
Implementation makes the tests pass
```

The issue owns the test contract. The Issue PR reviews the tests that satisfy it.

---

## The test contract

Give every criterion the code must satisfy at least one row.

| Criterion                   | Proof                                    | Level               | Why this test exists                         |
| --------------------------- | ---------------------------------------- | ------------------- | -------------------------------------------- |
| Renaming persists           | Rename, reload, observe the new name     | Integration         | Proves persistence across a request boundary |
| Blank names rejected        | Submit a blank value, observe validation | Unit or integration | Covers specified invalid input               |
| Unrelated project unchanged | Rename A, inspect B                      | Integration         | Covers the isolation requirement             |

Review the contract once every test fails for the behavior it is missing.

The contract is complete when every criterion it covers has proof and every test says why it exists.

---

## Minimum convincing evidence

Write the smallest set of tests that would convince a reviewer.

1. Trace every new test to a requirement, regression, invariant, or meaningful risk.
2. Prove behavior rather than implementation structure.
3. Use the lowest stable test boundary that proves the behavior.
4. Reuse existing test infrastructure unless the Slice requires something new.
5. Skip tests for framework behavior, trivial accessors, static typing guarantees, and implementation details added only for coverage.
6. Remove redundant tests when another test already proves the same thing.
7. For a test added during contract review, confirm it fails because the behavior is missing and passes once the behavior exists.

---

## After the contract is accepted

Once the contract is accepted, changing what a test proves needs review before it lands in the Slice.

Refactoring a test without changing what it proves is fine. Changing its proof belongs in implementation review.

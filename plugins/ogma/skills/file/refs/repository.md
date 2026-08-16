# Filing in the repository

Reference for [`file`](../SKILL.md).

Use this for documents that live in the repository rather than on GitHub.

---

## Where they go

Check for an obvious home first. When a convention or a tool already expects the document at a particular path, put it there.

Everything else goes in `.ogma/docs/<type>/`, one directory per kind of document, named after the kind.

```text
.ogma/docs/adr/
```

Name each file after what it records, in kebab case. Its own reference names whatever else the kind needs.

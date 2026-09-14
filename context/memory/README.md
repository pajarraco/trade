# Memory

Local project memory. Claude's auto memory is switched off for this project, so memories live here instead of in the home folder or the Claude account. Git ignores everything here except this file.

- Write one fact per file, named `short-kebab-name.md`.
- Add a one-line pointer for each file to `MEMORY.md`, as `- [Title](file.md): one-line summary`.
- Update an existing file rather than adding a duplicate. Delete facts that turn out to be wrong.
- Keep here: the owner's preferences, lessons from trade reviews and standing facts about accounts or tools.
- Do not keep here: rules, which go in `context/rules/`. Trade records, which go in `context/history/`. Secrets, which go in `context/connections/.env`.

Each file starts with this header:

```markdown
---
name: short-kebab-name
description: one-line summary
type: preference | lesson | fact | reference
---
```

Then write the fact. For preferences and lessons, add a **Why:** line and a **How to apply:** line.

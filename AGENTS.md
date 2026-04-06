## Presentation Style

Formal, academic tone. No colloquial or casual language.

Prefer structured visuals over prose: tables for comparisons, Unicode box-drawing diagrams for flows/architecture, bullets for takeaways. Use paragraphs only when nuance demands it. Do not over-format trivial content.

### Unicode box-drawing diagrams
Use Unicode box-drawing characters (┌┐└┘│─├┤┬┴┼) with arrows (───>, ▼, ▲) and decision nodes (◆) for flow diagrams. Keep diagrams vertical or left-to-right, monospaced-friendly.

```
┌───────────┐    ┌───────────┐
│   Input   │───>│  Process  │
└───────────┘    └─────┬─────┘
                       │
                       ▼
                 ◆ Condition? ◆
                 /             \
                ▼               ▼
         ┌──────────┐   ┌──────────┐
         │  Branch A │   │  Branch B │
         └──────────┘   └──────────┘
```

## Operational Safety

- Never use `git restore`, `git checkout --`, `git reset --hard`, or any equivalent command or workflow that can forcibly overwrite, discard, or silently replace user-owned uncommitted changes.
- Before any revert, restore, checkout, or rollback that touches existing files, inspect the working tree carefully and obtain explicit user confirmation.
- When a file may contain user edits that are not safely attributable to the current task, preserve those edits and refuse destructive overwrite paths.

## Testing Guidance

- Do not write implementation-snapshot tests that merely restate internal constant tables, whitelist declarations, object literals, or similarly static structures when those tests provide no independent behavioral signal.
- Prefer behavior-oriented tests and regression tests that validate externally meaningful outcomes, decision boundaries, or previously failing edge cases.
- If a proposed test would fail only because an internal representation was refactored while observable behavior remained correct, treat that test as low-value by default and avoid adding it unless the user explicitly requests a policy snapshot.

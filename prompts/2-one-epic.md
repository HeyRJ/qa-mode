# 2 · One epic first

Pick one epic, ideally the one with the most rules and numbers, and check the format on it before Claude writes the rest.

```text
Start with <epic ID> (<epic name>) only, so I can check the format. One test case per row, with these columns:
TC ID | Story | AC | Type (Positive, Negative or Edge) | Title | Preconditions | Test data | Steps | Expected result | Priority | Rules

Add the negative and edge cases the criteria don't cover. Stop after <epic ID>.
```

**Why it works:** fixing the format on one epic is quicker than on all of them. "Add the negative and edge cases the criteria don't cover" asks for the cases a BA rarely writes down. In the episode, Claude added cases that land exactly on a rounding half without being asked: 59 likes on 2,000 views is 2.95%, shown as 3.0%, a B.

If something needs fixing, send numbered review notes (see [`lead-review-checklist.md`](../lead-review-checklist.md)) and ask for only what changed. The columns are explained in [`test-case-template.md`](../test-case-template.md).

As sent in the episode: [`example-reach/2-one-epic.md`](../example-reach/2-one-epic.md)

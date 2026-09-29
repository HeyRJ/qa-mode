# QA lead review checklist

Claude drafts the review and the test cases. These are the calls it can't make for you.

## 1. The review, before any test cases

- [ ] Before you read Claude's review, write down the gaps you expect. Then compare. In the episode, it caught 7 of 9, and missed the speed and privacy requirements and counts in Hindi digits.
- [ ] Every point names a story, AC or rule ID, and is marked Blocking or Not blocking.
- [ ] Nothing is made up: each point is in the file, or clearly missing from it.
- [ ] Non-functional requirements are there, with numbers and a way to test them: speed, browsers, phone sizes, privacy.
- [ ] The Blocking points go to the BA first.

## 2. The first epic

- [ ] The columns are the ones you asked for, in that order.
- [ ] Expected results show every number the tester checks (the inputs, the result and the grade) and copy messages word for word.
- [ ] Edge cases sit exactly on the boundaries: band edges, rounding halves, limits. In the episode: 59 likes on 2,000 views is 2.95%, shown as 3.0%, a B.
- [ ] Totals are tested the way the requirements define them. In the episode, the month's grade comes from the totals, not from an average of the posts.
- [ ] Each story has at least one negative or edge case, not only positives.

## 3. The testers' file

- [ ] Coverage lists every AC ID in the requirements, and none has zero test cases.
- [ ] Won't stories only check that the feature isn't there.
- [ ] Row numbers match the spreadsheet: the header is row 1, and blank rows count.
- [ ] The Test data sheet says exactly what's in each file, not "a large file".
- [ ] Nothing is made up: no messages, numbers or rules that aren't in the requirements or your answers.
- [ ] [`check_testcases.py`](check_testcases.py) finds 0 problems.

## 4. The open questions

- [ ] Each question says which test cases wait on it and who answers: the BA or a developer.
- [ ] Testing carries on for everything that isn't blocked.

## Sending review notes

When you catch a miss, send it as a numbered list with the exact fix, and ask for only what changed:

```text
Review notes from me, the lead:
1. <what's wrong, and the exact fix>
2. <…>

Apply these to <epic ID> and show only what changed.
```

# Example: Reach's report card, tested

Reach is a small web app for Instagram and YouTube numbers. In [Claude for BAs · 01](https://youtu.be/LoEkFvSc9a4), a client's sheet became the requirements for a CSV report card: 27 stories, 87 acceptance criteria, a field spec and 20 business rules, in one Excel file ([BA mode](https://github.com/HeyRJ/ba-mode) has how). Here that file goes to QA. Reach, the bakery and every number here are fictional.

These are the files from the episode, in the order they were used. The Project was set up with `project-instructions.txt` and `reach-context.md`. Everything else went into one chat.

| Step | File | What it is |
|---|---|---|
| Setup | [`project-instructions.txt`](project-instructions.txt) | The Project's instructions, exactly as pasted |
| Setup | [`reach-context.md`](reach-context.md) | The Project's file about Reach: what exists today, its constraints and what's being tested |
| Input | [`Reach report card v1 requirements.xlsx`](Reach%20report%20card%20v1%20requirements.xlsx) | The BA's handoff: stories (one row per acceptance criterion), field spec and business rules |
| Input | [`bakery sept FINAL (2).csv`](bakery%20sept%20FINAL%20%282%29.csv) | The sample file the criteria refer to |
| 1 | [`1-review-first.md`](1-review-first.md) | The review request. Only the CSV attached, so Claude asked for the handoff file |
| 1b | [`1b-handoff.md`](1b-handoff.md) | The handoff file, sent again |
| 2 | [`2-one-epic.md`](2-one-epic.md) | Test cases for EP-3 only, to check the format |
| 3 | [`3-open-questions.md`](3-open-questions.md) | Every open question into one file for the BA and the devs |
| 4 | [`4-excel.md`](4-excel.md) | The testers' Excel file |
| Output | [`outputs/Open questions for BA and devs.xlsx`](outputs) | 44 questions (6 Blocking), with the test cases each one holds up and who answers, plus a How to use sheet |
| Output | [`outputs/Reach report card v1 test cases.xlsx`](outputs) | 138 test cases, Coverage for all 87 criteria and 65 test data files |

## What happened

- The first message went with only the CSV attached. Claude didn't review without the handoff file: it said the file was missing and asked for it.
- With the file, the review took about 3 minutes: 33 points (14 can't be checked as written, 7 contradictions, 12 missing), 4 of them Blocking. One is a contradiction BA 01 missed: BR-13 compares all nine columns to find duplicates, Notes included, while BR-15 says Notes never count. Claude also recalculated every figure the criteria take from the sample file, and they all match.
- For EP-3, it added cases that land exactly on a rounding half without being asked: 59 likes on 2,000 views is 2.95%, shown as 3.0%, a B.
- The open questions went into one file for the BA and the devs instead of being answered in the chat, so testing didn't wait.
- The final file has 138 test cases (52 positive, 41 negative, 45 edge), covers all 87 criteria and describes 65 test data files. [`check_testcases.py`](../check_testcases.py) found 0 problems in both files.

## The 9 gaps in the handoff

Noted before the take, to compare with Claude's review.

| Gap | In Claude's review |
|---|---|
| No non-functional requirements: speed for a big file, browsers, and how to check that the file never leaves the browser | In part: it asked about browsers, not speed or privacy |
| BR-13 vs BR-15: duplicates compare all nine columns, Notes included, while BR-15 says Notes never count | Yes |
| RC-01.1 says "the report card for September 2026 is shown", without the numbers a tester checks | Yes |
| "Today": BR-09's future-date check and BR-10's report month depend on the device's date | Yes |
| 5 MB: 5,000,000 bytes or 5 × 1,024 × 1,024? It decides the boundary test | Yes |
| No rule for interactions greater than views | Yes |
| No upper limit on counts, and nothing on counts written in Hindi digits (१२३) | No |
| Two problems in one row: BR-08 and BR-09 against RC-04.3's one line per problem | Yes |
| Long captions: nothing on how long a caption can be | Yes |

Try the same requirements with your own setup and see how many your Claude finds.

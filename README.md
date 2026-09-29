# QA mode

A Claude setup for testers. It takes agreed requirements to test cases a tester can run without asking anyone: a review of the requirements first, then the test cases, their coverage and the test data they need. Claude drafts, and you make the calls.

It comes from [**Claude for QAs · 01**](https://youtu.be/OTxv-_vFQf0) on the [Rohan J](https://www.youtube.com/@rohanbuilds-ai) YouTube channel (in Hindi). In the episode, the requirements Excel from [Claude for BAs · 01](https://youtu.be/LoEkFvSc9a4) (27 user stories, 87 acceptance criteria) goes to QA. Before writing a single test case, Claude reviews it and raises 33 points, 4 of them Blocking. Then come 138 test cases that cover all 87 criteria, the 65 test data files they need, and 44 open questions in one file for the BA and the developers.

## What's inside

| File | What it's for |
|---|---|
| [`project-instructions.md`](project-instructions.md) | WHO, WHAT and HOW for your Claude Project: the rules every answer follows |
| [`prompts/`](prompts) | The four messages you send, in order: review first, one epic, open questions, Excel |
| [`test-case-template.md`](test-case-template.md) | The columns of a test case, and what makes each one runnable |
| [`lead-review-checklist.md`](lead-review-checklist.md) | What to check before the test cases go to the testers |
| [`check_testcases.py`](check_testcases.py) | Checks Claude's test case file against the requirements |
| [`example-reach/`](example-reach) | The episode's example: the requirements, every message sent and both outputs |

## How to use it

1. **Set up a Claude Project** for the product. Paste [`project-instructions.md`](project-instructions.md) into its instructions, with your product in WHO.
2. **Add a short context file** to the Project: what the product does today, its constraints and what's being tested. [`example-reach/reach-context.md`](example-reach/reach-context.md) shows the idea.
3. **Review first.** Start a chat in the Project, attach the requirements file and any sample file its criteria use, and send [`prompts/1-review-first.md`](prompts/1-review-first.md). Claude lists what can't be tested as written, what contradicts what and what's missing, with IDs. It writes no test cases yet.
4. **One epic first.** Send [`prompts/2-one-epic.md`](prompts/2-one-epic.md) and check the format and the expected results on one epic before the rest.
5. **Park the open questions.** Send [`prompts/3-open-questions.md`](prompts/3-open-questions.md). Every question goes into one Excel file for the BA and the developers, with who answers and which test cases wait on it, so testing doesn't stop.
6. **The testers' file.** Send [`prompts/4-excel.md`](prompts/4-excel.md): the test cases for every epic, a Coverage sheet and a Test data sheet, in one Excel file.
7. **Check it** with [`lead-review-checklist.md`](lead-review-checklist.md), and run [`check_testcases.py`](check_testcases.py) on the file.

## Check the file

The script needs Python 3 and openpyxl (`pip install openpyxl`):

```text
python3 check_testcases.py "example-reach/outputs/Reach report card v1 test cases.xlsx" "example-reach/Reach report card v1 requirements.xlsx"
```

It prints `ok` or `!!` for each check: every acceptance criterion has a test case, the Coverage sheet agrees, the IDs are unique, every test case has steps, test data and an expected result, Won't stories only check that the feature isn't there, no expected result uses vague words, and the open questions file names only test cases and criteria that exist. The requirements file uses BA mode's layout (a Stories sheet with one row per acceptance criterion).

A few checks are only for the Reach example: its sample file's numbers and messages (`KEYS` and `MSGS` in the script). Change them for your project, or delete them.

## Before you start

- Put work data only into AI tools your company allows.
- Reach, the bakery and every number in the example are fictional.
- The episode was recorded with Claude Opus 5.5.

## Next

Claude for BAs · 02 turns the same requirements into a clickable prototype.

## Licence

MIT: use it, change it and share it. See [`LICENSE`](LICENSE).

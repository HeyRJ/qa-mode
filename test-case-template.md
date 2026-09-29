# Test case template

One row per test case. These are the columns from the episode, and what makes each one runnable by a tester who wasn't in the room.

| Column | What goes in it |
|---|---|
| TC ID | TC-001, TC-002…, never reused |
| Story | The story ID from the requirements, e.g. RC-01 |
| AC | The acceptance criterion ID(s) it tests, e.g. RC-01.1 |
| Type | **Positive:** valid input, the right result. **Negative:** invalid input, the exact message. **Edge:** a value on a boundary, or a case the criteria don't mention. |
| Title | What it checks, in a few words |
| Preconditions | Everything true before step 1: the page, the device, the date, what's already loaded |
| Test data | The sample file by name, or a file listed in the Test data sheet |
| Steps | Numbered actions, one per step |
| Expected result | Exactly what the tester sees: numbers, grades and messages copied from the requirements |
| Priority | From the story: Must, Should or Could |
| Rules | The business rule IDs it depends on, e.g. BR-10 |
| Status | Not run, then Pass, Fail or Blocked |

## An example from the episode

| Column | TC-100 |
|---|---|
| Story | RC-15 |
| AC | RC-15.5 |
| Type | Edge |
| Title | 2.95% rounds up to 3.0% and gets B |
| Preconditions | Report card page open on a laptop; device date 28-09-2026; no report showing |
| Test data | ep3-rate-2-95.csv |
| Steps | 1) Click "Choose CSV file" and pick ep3-rate-2-95.csv. 2) Look at the Overall section. |
| Expected result | Overall: 3.0% (59 ÷ 2,000 = 2.95%), B |
| Priority | Must |
| Rules | BR-04, BR-05 |
| Status | Not run |

And its row in the Test data sheet:

| File name | Exactly what's in it | Used by |
|---|---|---|
| ep3-rate-2-95.csv | `Date,Platform,Caption,Views,Likes,Comments,Shares,Saves` then `10-09-2026,Instagram,Boundary test,2000,59,0,0,0` | TC-100 |

## Vague or exact

A tester can mark an exact result Pass or Fail without asking anyone.

| Vague | Exact |
|---|---|
| The report card is shown correctly | Overall: 10.5%, A+; Instagram: 11.1%, A+; YouTube: 2.6%, C |
| An error is shown | Row 8: Views must be a full number, like 12400 or 12,400. "12.4K" is not accepted. |
| The rate is rounded properly | Overall: 3.0% (59 ÷ 2,000 = 2.95%), B |

## The testers' Excel file

- **Test cases:** one row per test case, with the columns above.
- **Coverage:** every AC ID in the requirements, with the TC IDs that cover it. An AC without a test case is flagged.
- **Test data:** every file the test cases need: its name, exactly what's in it, how to make it and the TC IDs that use it.

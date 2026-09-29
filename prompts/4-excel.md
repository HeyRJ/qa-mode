# 4 · The testers' file

Send this once the format is right. Claude writes the test cases for every epic and builds one Excel file for the testers.

```text
Now write the test cases for every epic in the same format, and put them in one Excel file for the testers:
- Sheet "Test cases": one row per test case, with the columns above plus Status
- Sheet "Coverage": every AC ID in the requirements, with the TC IDs that cover it. Flag any AC without a test case.
- Sheet "Test data": every file the test cases need: the file name, exactly what's in it, and the TC IDs that use it
Set every Status to Not run and freeze the header rows. Add any new open questions to Open questions for BA and devs.xlsx, not to this file.
```

**Why it works:** the Coverage sheet shows at a glance that every criterion has a test. The Test data sheet means nobody has to guess what goes in each file. New questions go to the BA and dev file, so there's one list to chase. Then check the file yourself with [`check_testcases.py`](../check_testcases.py).

The file from the episode: [`example-reach/outputs/Reach report card v1 test cases.xlsx`](../example-reach/outputs), with 138 test cases (52 positive, 41 negative, 45 edge), all 87 criteria covered and 65 test data files.

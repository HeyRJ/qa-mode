# 4 · The testers' Excel file

The last message. Claude made [`Reach report card v1 test cases.xlsx`](outputs): 138 test cases, Coverage for all 87 criteria and 65 test data files. Its new open questions went into the BA and dev file, which ended with 44.

```text
Now write the test cases for every epic in the same format, and put them in one Excel file for the testers:
- Sheet "Test cases": one row per test case, with the columns above plus Status
- Sheet "Coverage": every AC ID in the requirements, with the TC IDs that cover it. Flag any AC without a test case.
- Sheet "Test data": every file the test cases need: the file name, exactly what's in it, and the TC IDs that use it
Set every Status to Not run and freeze the header rows. Add any new open questions to Open questions for BA and devs.xlsx, not to this file.
```

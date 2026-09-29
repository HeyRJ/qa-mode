# 1 · Review first

Attach the requirements file and any sample file its criteria refer to, then send this. Claude reviews the requirements the way a test lead would, before it writes a single test case.

```text
The requirements for <the feature> are baselined as <version>. The BA's handoff file is attached, with the sample file its criteria refer to.

Before you write any test cases, review the requirements as a test lead:
1. Anything a tester can't check exactly as written
2. Anything that contradicts another story, rule or the field spec
3. Anything missing that the testers will need

Name the story, AC or rule ID for each point, and mark it Blocking or Not blocking. Don't write test cases yet, and don't answer your own questions.
```

**Why it works:** "Before you write any test cases" gets the gaps found while they're cheap to fix. The three groups are what stop a tester: a criterion too vague to check, two rules that disagree, and something nobody wrote down. "Blocking or Not blocking" tells the BA what to answer first. In the episode, this got 33 points, 4 of them Blocking, including a contradiction in the BA's handoff: BR-13 compares Notes when it looks for duplicates, and BR-15 says Notes never count.

**Review it yourself too.** Before you read Claude's review, write down the gaps you expect. In the episode, it caught 7 of the 9 noted before the take. It missed the speed and privacy requirements, and counts written in Hindi digits.

**Check the attachments.** In the episode, only the CSV attached the first time. Claude didn't review without the handoff file; it said the file was missing and asked for it.

As sent in the episode: [`example-reach/1-review-first.md`](../example-reach/1-review-first.md)

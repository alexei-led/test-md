# test-md syntax specification

## Revision History

| Date      	| Revision  | Author   |
|---          |---        |---       |
| 2011-12-01  | 0.1       | @alexei  |


## Intro

**The Concept**
**test-md** is a manual testing framework, where test cases and test results are defined as a plain text files. **test-md** syntax essentially a convention, which is built around markdown syntax.

**As fast as you can type**
Markdown allows you to produce formatted text as fast as you can type. This allows you to create test case, test suite and test run without even clicking a mouse!

**Flexibe format**
Since test case is a plain text file, it does not have any restriction on style, format, links, images, [emoji](http://www.emoji-cheat-sheet.com), language and encoding. If you follow the convention, any **test-md** runner should be able to understand your test case and execute it.

**Scannability**
It's possible to organize test cases either into multiple folders and/or within same file. So, to view your test cases you can just scroll up and down inside file or use any file search tools.

**Flexible storage**
As a file, you can decide to keep it within any version control system, like Git or Mercurial; any cloud storage, like Dropbox and Google Drive and just on your disk. It's your decision. You can easily share your test cases with other users, using standard file sharing approaches.

## Syntax

As stated above, the **test-md** sytax is not a new syntax, but a convention above existing markdown syntax.

### Test case defintion

The double hashtag ``## `` (with space before name) defines a test case.
Test case lasts till next test case or till end of file. Test case might contain test description and steps.

```
## Minimalistic Test Case

This is the minimal test case. It does nothing at all.
```

### Test case step defintion

The dash ``-`` defines a test case step step. Steps can be hierarchical: use ``tab`` character do define a next level.
There are two types of steps: ***action*** and ***validation***. ***Action*** step represents an action, user should take, where ***validation*** step is a checkpoint, where user must state if step passed or failed. To define a ***validation*** step it should start with exclamation mark emoji ``!``.

```
## Test Case with Steps

This test contains multiple steps. Any bullet or number list considered as steps list. Steps can be defined as hierarchical list too.

- This is the first step
- And this is the second step
  - This is a sub-step of second step
  - Additional sub-step to be completed
- ! Now it's time to validate something
- And the final step
```

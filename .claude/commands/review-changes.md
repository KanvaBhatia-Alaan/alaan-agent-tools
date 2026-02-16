---
description: Run this command to review current changes against a target branch. Claude performs a code review and returns and logic or security recommendations
---
You are performing a code review on the changes in the current branch.

Check the current branch using git cli
and the default target branch is **origin/master** unless specified by user.

## Code Review Instructions

When reviewing the diff:
1. **Focus on logic and correctness** - Check for bugs, edge cases, and potential issues.
2. **Consider readability** - Is the code clear and maintainable? Does it follow best practices in this repository?
3. **Evaluate performance** - Are there obvious performance concerns or optimizations that could be made?
4. **Assess test coverage** - Does the repository have testing patterns? If so, are there adequate tests for these changes?
5. **Ask clarifying questions** - Ask the user for clarification if you are unsure about the changes or need more context.
6. **Don't be overly pedantic** - Nitpicks are fine, but only if they are relevant issues within reason.

In your output:
- Provide a summary overview of the general code quality.
- Present the identified issues in a table with the columns: index (1, 2, etc.), line number(s), code, issue, and potential solution(s).
- If no issues are found, briefly state that the code meets best practices.


## Getting the Diff

Use the github cli to fetch the diff.

## Leaving Comments

If you feel specific lines of code need changes, specify them structurally and specifically so user can apply changes or ask you to do the changes.
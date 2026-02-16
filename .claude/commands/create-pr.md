---
description: This command commits and pushes code to create a PR with relevant title and descriptiion.
---
The user likes the state of the code.

There are n uncommitted changes. - get from github cli
get the current branch from github cli .
The target branch is origin/master unless specified by uesr.

There is no upstream branch yet.
The user requested a PR unless user specified a draft PR.

Follow these **exact steps** to create a PR:

- Run `git diff` to review uncommitted changes
- Commit them. Follow any instructions the user gave you about writing commit messages.
- Push to origin.
- Use the github cli to review the PR diff
- Use `gh pr create --base master` to create a PR onto the target branch. Keep the title under 80 characters and the description under five sentences (unless the user has given you other instructions).

If any of these steps fail, ask the user for help.

---
description: This command commits and pushes code to create a PR with relevant title and descriptiion against uat or staging by creating an intermediate branch with perfect reverse merges and merge conflict resolution.
---
The user wants to create an intermediate branch to the target mentioned because the target branch is ahead from master and needs some merge conflicts to be resolved

Follow these **exact steps** to create a PR:

- Make sure current branch is either a feature/ or hotfix/ branch and is not behind master.
- If it is behind, reverse merge master into the current branch - git merge master
- Get the latest pull of the target branch, so that locally latest of the target is there.
- Then create a new branch with current feature or hotfix branch as the base, name it intermediate/[current branch name]_[target] 
    - for example intermediate/feature/aim-123-abc-xyz_uat or intermediate/hotfix/aim-123-abc-xyz_staging.
- Then in thie new intermediate branch, reverse merge the target, git merge staging or git merge uat etc.
- merge might have merge conflicts, so resolve the conflicts and commit the merge. 
- This new branch is supposed to contain the hotfix/feature changes and also not behind the target.
- Push the branch and proceed to create the PR
- Use `gh pr create --base master` to create a PR onto the target branch. Keep the title under 80 characters and the description under five sentences (unless the user has given you other instructions).

If any of these steps fail, ask the user for help.

# Incorrect Unpushed Git Commit
There is wrong commits that are not pushed yet.

## Root Cause
There is something wrong about the unpushed commit that needs to be reverted.

## Resolution
1. Go to the location of the repo.
2. Type the following repo to revert the changes.
```
git reset --soft HEAD~1
```

## Reference
[https://stackoverflow.com/questions/15289768/github-commits-arent-recorded-in-the-your-contributions-calendar

git reset --soft HEAD~1](https://stackoverflow.com/questions/3197413/how-do-i-delete-unpushed-git-commits)

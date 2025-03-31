# Missing GitHub Contribution
There is/are missing contributions for some dates even there is git commit found on that day.

## Root Cause
The commit is performed by another email, go to the specific commit and add .patch at the end to search for the email at **From** column to get the wrong email. <br/>
For example: https://github.com/soongxian/HandyTool/commit/da21884c49808ca8976b308f2e92714921e060df.patch

## Resolution
1. Open Git Bash
2. Clone a bare repository
```
git clone --bare https://github.com/user/repo.git
cd repo.git
```
3. Paste the following code into the git bash console and press enter to run the script after changing the variables WRONG_EMAIL, CORRECT_NAME and CORRECT_EMAIL:
```
#!/bin/sh

git filter-branch --env-filter '

WRONG_EMAIL="wrong-email@example.com"
CORRECT_NAME="Correct Name"
CORRECT_EMAIL="correct-email@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
export GIT_COMMITTER_NAME="$CORRECT_NAME"
export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
export GIT_AUTHOR_NAME="$CORRECT_NAME"
export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```
4. Push the corrected history to GitHub
```
git push --force --tags origin 'refs/heads/*'
```

## Reference
https://stackoverflow.com/questions/15289768/github-commits-arent-recorded-in-the-your-contributions-calendar

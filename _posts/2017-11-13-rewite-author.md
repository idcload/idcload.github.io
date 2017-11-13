Useful: [GitHub: Changing author info](https://help.github.com/articles/changing-author-info/)

```bash
#!/bin/sh

git filter-branch --env-filter '

OLD_EMAIL="your-old-email@example.com"
CORRECT_NAME="Your Correct Name"
CORRECT_EMAIL="your-correct-email@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```
Missing in the article is a fix for the <code>git pull</code> error: <code>fatal: refusing to merge unrelated histories</code>.
Anwser is here: [Stackoverflow: Git refusing to merge unrelated histories](https://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories)

```git
git pull --allow-unrelated-histories
Merge made by the 'recursive' strategy.
```

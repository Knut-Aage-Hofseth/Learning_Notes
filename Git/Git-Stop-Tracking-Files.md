## How to stop git from tracking a file you want included in the repository

```
git update-index –skip-worktree <Specify file>
```

This makes git skip the specified file when building the change index. This is useful for settings files that needs to be inclded in the project, but where you do not want passwords to be in the repository.

Possible other solutions can be found [here.](https://alphaefficiency.com/git-stop-tracking-file)

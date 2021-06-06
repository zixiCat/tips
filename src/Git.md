- Use `git stash` to save code temporarily, you could restore it by u1sing `git stash apply index` or `git stash pop index`. Of course there is `git stash list` or `git stash clear`...[ref](https://www.git-scm.com/docs/git-stash)
- Use `git reflog show`, and then you could recover from `git reset --hard` you had done.
- Use this following command line:
  ```bash
  git ls-remote --tags --refs origin | cut -f2 | xargs git push origin --delete
  ```
  Then your all remote tags will be removed in one go, but when you use this command line:
  ```bash
  git tag -l | xargs -n 1 git push --delete origin
  ```
  It will delete remote tags every 2 seconds for one, really trash! The following command line could be used to delete all local tags...[ref](https://stackoverflow.com/questions/19542301/delete-all-tags-from-a-git-repository)
  ```bash
  git tag | xargs git tag -d
  ```
- Use `git reset HEAD@{1}`, and you can recover your code from git-reset-hard, see more...[ref](https://stackoverflow.com/questions/5788037/recover-from-git-reset-hard)
- To authenticate with GitHub, use this one: `https://[USERNAME]:[TOKEN]@[GIT_ENTERPRISE_DOMAIN]/[ORGANIZATION]/[REPO].git`...[ref](https://stackoverflow.com/questions/18935539/authenticate-with-github-using-a-token?answertab=votes#tab-top)
- The similarities and differences between monorepo and polyrepo...[ref](https://github.com/joelparkerhenderson/monorepo_vs_polyrepo)
- Use `git config --local --get core.hookspath`, and then terminal will show the value.
- `git commit -m "subject" -m "body" -m "footer"`
- We can get the committed message via `$(cat $1)` in `commit-msg`, `prepare-commit-msg` of git hooks, but the message isn't accessible to `pre-commit` hook
- To make your committed message awesome, there are some packages to help you like `husky`, `commitizen`. You can also customize hooks files or config the hooksPath to directory you want...[ref](https://backlog.com/blog/git-commit-messages-bold-daring/)
- `git commit -a/--all` will tell the command to automatically stage files that have been modified and deleted, but new files you have not told Git about are not affected...[ref](https://git-scm.com/docs/git-commit/en)
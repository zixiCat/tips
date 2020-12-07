- Use `git stash` to save code temporarily, you could restore it by u1sing `git stash apply index` or `git stash pop index`. Of course there is `git stash list` or `git stash clear`...[ref](https://www.git-scm.com/docs/git-stash)
- Use `git reflog show`, and then you could recover from `git reset --hard` you had done.
- Use this following command line:
  ```bash
  git ls-remote --tags --refs origin | cut -f2 | xargs git push origin --delete
  ```
  And your all remote tags will be remove in one go. But when you use this command line:
  ```bash
  git tag -l | xargs -n 1 git push --delete origin
  ```
  It will delete remtoe tags every 2 seconds for one, really trash! The following command line is used to delete all local tags...[ref](https://stackoverflow.com/questions/19542301/delete-all-tags-from-a-git-repository)
  ```bash
  git tag | xargs git tag -d
  ```

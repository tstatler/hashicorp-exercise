## Comparing git push, pull, and fetch commands

You use the `git push,` `git fetch,` and `git pull` commands to synchronize changes between local and remote repositories.

- [`git push`](#git-push) - Uploads changes from your local branch to the remote branch.
- [`git fetch`](#git-fetch) — Retrieves changes from the remote branch into the remote-tracking branch without merging them into your local branch.
- [`git pull`](#git-pull) - Retrieves changes from the remote branch into the remote-tracking branch and merges them into your local branch.

### Git push

The `git push` command uploads changes in your local branch to the remote branch. This operation makes the remote branch identical to your local branch. It first checks that there is a remote-tracking branch for the remote repository connected to your local branch and then synchronizes local changes with the remote branch.

If not all commits in the remote branch are in your local branch, the remote will reject the push operation, as shown below:

```bash
git push
To https://github.com/example/example.git
! [rejected]        feature-branch -> feature-branch
```

In this case, you need to first synchronize your branch with the remote branch by either running `git pull` or `git fetch` followed by `git merge`. S

## Git fetch

`git fetch` again takes our current branch, and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch, and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch - probably also called "master".

## Git pull

Often `git push` and `git pull` are described as equivalent. This isn't entirely correct, since `git pull` does two things: it calls `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge happens.
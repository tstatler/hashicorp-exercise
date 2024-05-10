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

In this case, you need to first synchronize your branch with the remote branch by either running `git pull` or `git fetch` followed by `git merge`. See [`git pull`](#git-pull) and [`git fetch`](#git-fetch) for details on each approach.

## Git fetch

The `git fetch` command updates your remote-tracking branch with changes from the remote branch, but does not merge those changes into your local branch. This allows you to review the incoming changes before updating your working branch. It first checks for the existence of a corresponding remote-tracking branch (`origin/main,` for example). If one exists, it updates the tracking branch with the changes from the remote branch.

```bash
git fetch
...
From https://github.com/example/example-repo
   cc57037..f91adc6  main       -> origin/main
```

Assuming you had the `main` branch checked out locally and `origin` was the remote name, you would run the following command to merge the fetched changes:

```bash
git merge origin/main
```

If you don't need or want to review remote changes before merging, you can use the [`git pull`](#git-pull) command, which combines `git fetch` and `git merge` in a single operation.

## Git pull

Often `git push` and `git pull` are described as equivalent. This isn't entirely correct, since `git pull` does two things: it calls `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge happens.
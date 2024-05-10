## Comparing git push, pull, and fetch commands

- `git push` - sent changes from a local branch to a remote repo
- `git fetch` - get changes from a remote repo into your tracking branch
- `git pull` - will get changes from a remote branch into your tracking branch and merge them into a local branch

## Git push

`git push` takes our current branch, and checks to see whether or not there is a tracking branch for a remote repository connected to it. If so, our changes are taken from our branch and pushed to the remote branch. This is how code is shared with a remote repository, you can think of it as "make the remote branch resemble my local branch". This will fail if the remote branch has diverged from your local branch: if not all the commits in the remote branch are in your local branch. When this happens, your local branch needs to be synchronized with the remote branch with git pull or git fetch and git merge.

## Git fetch

`git fetch` again takes our current branch, and checks to see if there is a tracking branch. If so, it looks for changes in the remote branch, and pulls them into the tracking branch. It does not change your local branch. To do that, you'll need to do `git merge origin/master` (for the "master" branch) to merge those changes into your branch - probably also called "master".

## Git pull

Often `git push` and `git pull` are described as equivalent. This isn't entirely correct, since `git pull` does two things: it calls `git fetch` followed immediately by `git merge`. This is often what we desire to do, but some people prefer to use `git fetch` followed by `git merge` to make sure they understand the changes they are merging into their branch before the merge happens.
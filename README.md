# Publishing the `main` branch

The push failed with:

```text
error: src refspec main does not match any
```

Git prints this when it cannot find a local commit to push for the branch named
in the command. In this checkout, `main` was an unborn branch: it had no
commits, and the remote's existing `main` branch had not been fetched into the
local repository. This is why `git push -u origin main` had no local `main`
ref to publish.

The local branch has now been fast-forwarded to `origin/main`, so it contains
the remote history and tracks the remote branch. To synchronize an existing
remote branch before pushing in the future, run:

```sh
git fetch origin
git switch main
git merge --ff-only origin/main
git push -u origin main
```

If the remote does not have a branch yet, make at least one local commit first:

```sh
git add .
git commit -m "Initial commit"
git push -u origin main
```

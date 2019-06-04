# Git

Ignore changes to a tracked file.

```bash
git update-index --assume-unchanged <file>
```

Start tracking changes to an ignored file (above).

```bash
git update-index --no-assume-unchanged <file>
```

Undo the last commit.

```bash
git reset HEAD~1 --soft
```

Undo the first (unpushed) commit of a repository.

```bash
git update-ref -d HEAD
```

Verify objects in database and optimize.

```bash
git fsck && git gc --aggressive --prune=now
```

Change branch.

```bash
git checkout <branch name>
```

Create a new local branch based off your current one.

```bash
git checkout -b <branch name>
```

Water current branch with changes from other branch.

```bash
git merge <other branch name>
```

Squash feature branch changes into current one.

```bash
git merge --no-commit --squash <feature branch name>
```

Delete an unmerged local branch, i.e. force delete.

```bash
git branch -D <branch name>
```

Delete a remote branch.

```bash
git push <remote name> :<branch name>
```

# SVN

Pull latest changes from remote:

```bash
svn update
```

Undo local changes to file:

```bash
svn revert <file path>
```

Undo all local changes:

```bash
svn revert --recursive .
```

Note: For merging and conflict resolution use a GUI (e.g. SmartSVN), and everything else use git-svn

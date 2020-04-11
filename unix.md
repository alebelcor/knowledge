# Unix/Unix-like

List files/processes on port `80`:

```bash
sudo lsof -Pni | grep :80
```

Remove `.DS_Store` files from the current and descendant folders:

```bash
find . -name '.DS_Store' -type f -delete
```

Get the size of a file/folder:

```bash
du --summarize --human-readable <file/folder path>
du -sh <file/folder path>
```

List out dependencies in `node_modules` sorted (descending) by disk space size:

```bash
du --summarize --human-readable ./node_modules/* | sort --numeric-sort --reverse | grep --perl-regexp --color=never '\dM.*'
du -sh ./node_modules/* | sort -nr | grep -P --color=never '\dM.*'
```

## Links

* [`du` manual](https://www.gnu.org/software/coreutils/manual/html_node/du-invocation.html)
* ["findutils" manual](https://www.gnu.org/software/findutils/manual/find.html)
* [`grep` manual](https://www.gnu.org/software/grep/manual/)
* [`lsof` manual](https://www.unix.com/man-page/mojave/8/lsof)

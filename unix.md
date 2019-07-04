# Unix/Unix-like

List files/processes on port `80`:

```bash
sudo lsof -Pni | grep :80
```

Remove `.DS_Store` files from the current and descendant folders:

```bash
find . -name '.DS_Store' -type f -delete
```

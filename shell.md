# Shell

Redirect `stdout`:

```bash
command > file
command 1> file
```

Redirect `stderr`:

```bash
command 2> file
```

Redirect `stderr` to `stdout`:

```bash
command 2>&1 file
```

Redirect `stderr` and `stdout`:

```bash
command > file 2>&1
command &> file # non-POSIX, i.e. less compatible
```

Clear a file:

```bash
:> file
true > file # same as above
```

Make file executable:

```bash
chmod +x <file>
```

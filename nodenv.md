# [nodenv](https://github.com/nodenv/nodenv)

Display available versions to install:

```bash
nodenv install --list
```

Get the latest definitions:

```bash
brew update && brew upgrade node-build
```

Install a version:

```bash
nodenv install <version number>
```

Set a specific version to be used on a folder:

```bash
nodenv local <version number>
```

Note: This will create a `.node-version` file on the folder.

Set a specific version to be used globally:

```bash
nodenv global <version number>
```

Note: Avoid using `nodenv shell` as this overrides all versions, including the "local" one.

Uninstall a version:

```bash
nodenv uninstall <version number>
```

Display version currently used:

```bash
nodenv version
```

Note: Use this instead of `node --version`.

Display all installed versions:

```bash
nodenv versions
```

# Yarn

## v1

Install dependencies:

```bash
yarn
yarn install # or this
yarn install --frozen-lockfile # for CI
```

Add a dependency:

```bash
yarn add <package name>
yarn add <package name> --dev # for a dev dependency
yarn global add <package name> # for a global install
```

Upgrade a dependency:

```bash
yarn upgrade <package name>
yarn upgrade-interactive # interactive way of upgrading
```

Remove a dependency:

```bash
yarn remove <package name>
```

Note: No need to specify a flag, e.g. `--dev`.

Run a user-defined script:

```bash
yarn dev # for a `dev` entry in `scripts` in `package.json`
yarn run dev # or this
```

Note: To pass arguments just add them like so: `yarn dev --foo --bar`

Run locally installed CLIs:

```bash
yarn speed-test # for running `speed-test` if specified in `package.json`
```

Generate a `yarn.lock` file from a `package-lock.json`:

```bash
yarn import
```

Note: Delete the `package-lock.json` file if you intend to use Yarn (v1), and use the `yarn.lock` file instead.

Generate a list of licenses from your dependencies:

```bash
yarn licenses generate-disclaimer
```

Check if installed packages are currently outdated:

```bash
yarn outdated
```

Enforce usage of a specific version of Yarn:

```bash
yarn policies set-version <version>
```

Note: This will generate a `.yarnrc` file, and download a Yarn executable to `.yarn/releases/`. These should be committed to source control.

Enable PnP (i.e. Plug’n’Play):

```bash
rm -rf node_modules
yarn --pnp
```

Note: This will remove the `node_modules` folder (unnecessary), create a `yarn.lock` (if not already present), add `installConfig.pnp: true` to `package.json`, and generate a `.pnp.js` file and a `.pnp/` folder. You should commit the `.pnp/` folder to source control, and ignore the `.pnp.js` file.

## Links

* [Yarn v1](https://classic.yarnpkg.com/lang/en/)
* [Migrating from npm – CLI commands comparison (v1)](https://classic.yarnpkg.com/en/docs/migrating-from-npm#toc-cli-commands-comparison)
* [Plug’n’Play (v1)](https://classic.yarnpkg.com/en/docs/pnp)
* [CLI commands (v1)](https://classic.yarnpkg.com/en/docs/cli/)

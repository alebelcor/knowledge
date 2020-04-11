# [npm](https://docs.npmjs.com/)

Open a package's repository page in the browser:

```bash
npm repo <package name>
```

Simplify and flatten dependencies:

```bash
npm dedupe
```

Garbage collect unneeded data and verify contents/integrity of cache folder:

```bash
npm cache verify
```

Note: `npm cache clean` will delete all cache data.

Install dependencies (for CI) with a clean slate:

```bash
npm ci
```

`npm install` and `npm test` in one command:

```bash
npm install-test
```

`npm ci` and `npm test` in one command:

```bash
npm install-ci-test
```

Check if installed packages are currently outdated:

```bash
npm outdated
```

## Links

* [`npm cache`](https://docs.npmjs.com/cli/cache.html)
* [`npm ci`](https://docs.npmjs.com/cli/ci.html)
* [`npm dedupe`](https://docs.npmjs.com/cli/dedupe.html)
* [`npm install-ci-test`](https://docs.npmjs.com/cli-commands/install-ci-test.html)
* [`npm install-test`](https://docs.npmjs.com/cli-commands/install-test.html)
* [`npm outdated`](https://docs.npmjs.com/cli-commands/outdated.html)
* [`npm repo`](https://docs.npmjs.com/cli/repo.html)

# macOS

Unload a user agent:

```bash
launchctl unload <.plist file path>
```

Or just use [LaunchControl](https://www.soma-zone.com/LaunchControl/)

Remove a user agent:

```bash
trash <.plist file path>
```

This assumes the [trash](https://github.com/sindresorhus/trash-cli) command exists.

Get domain name of an app:

```bash
mdls -name kMDItemCFBundleIdentifier -raw <app path>
```

Get all preferences for a certain domain:

```bash
defaults read <domain>
```

Get a certain preference value:

```bash
defaults read <domain> <preference>
```

Write (or update) a preference value:

```bash
defaults write <domain> <preference> <type> <value>
```

Get UTI (Uniform Type Identifier) of a file:

```bash
mdls -name kMDItemContentType -raw <file path>
```

## Links

- [A launchd Tutorial](https://www.launchd.info)
- [defaults (Software)](https://en.wikipedia.org/wiki/Defaults_(software))

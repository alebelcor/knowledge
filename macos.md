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

## Links

- [A launchd Tutorial](https://www.launchd.info)

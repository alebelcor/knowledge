# [nodemon](https://github.com/remy/nodemon)

Watch for file changes and run a command:

```bash
nodemon --watch <folder> --exec <command> --ext <extension>
```

<details><summary>Example</summary>
On the <code>app</code> folder, watch for changes on <code>.rb</code> files, and run <code>./bar.sh</code> when that happens:

<pre>
nodemon --watch "app" --exec "./bar.sh" --ext ".rb"
</pre>
</details>

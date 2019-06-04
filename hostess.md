# [hostess](https://github.com/cbednarski/hostess)

Set domains from file (silently):

```bash
sudo hostess -s apply <.json file>
```

<details><summary>Details</summary>
The JSON format should be something like:

<pre>
[
  {
    "domain": "localhost",
    "ip": "127.0.0.1",
    "enabled": true
  },
  ...
]
</pre>
</details>

Clean up (silently):

```bash
sudo hostess -s fix
```

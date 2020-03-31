# SSH

## How to use separate accounts for different repositories on GitHub

Let's say we want to use separate GitHub accounts. One user for personal use and a different one for work.

Assuming you have keys for each (e.g. `~/.ssh/personal_id_rsa`, and `~/.ssh/work_id_rsa`).

On your `~/.ssh/config`, you should have:

```
Host personal.github.com
  HostName github.com
  IdentityFile ~/.ssh/personal_id_rsa

Host github.com
  HostName github.com
  IdentityFile ~/.ssh/work_id_rsa
```

And when you want to clone a repository for personal use:

```bash
git clone git@personal.github.com:username/repo
```

And when you want to clone a repository for work:

```bash
git clone git@github.com:username/repo
```

## Links

* [SSH Setup for Multiple Github Accounts](https://www.bendb.com/blog/ssh-with-multiple-github-accounts/)

---
id: 533f3444-2b18-41f0-9284-c31d87eedd08
title: Multiple Accounts
desc: ""
updated: 1621709268301
created: 1621709263959
---

Add multiple github account, same machine to avoid conflicts when pushing or pulling repositories

```bash
Host me.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/me_rsa

Host work.github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/work_rsa
```

## Reference

https://stackoverflow.com/questions/3225862/multiple-github-accounts-ssh-config

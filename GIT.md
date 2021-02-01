Cloning a specific branch:

`git clone --branch <repo url>`

Rebase forked repo:

```bash
git remote add upstream <original-repo>
git fetch upstream
<make sure you are in the appropriate branch!>
git rebase upstream/<branchname>
git push origin <branchname> --force
```

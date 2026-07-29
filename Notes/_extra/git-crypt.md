```sh
# Create a Private Repository, clone to local
# git config core.autocrlf false
git init
git branch -M main
git remote add origin https://github.com/<user>/<repo>
vim .gitattributes
```

```
# Don't include .gitattributes
<secretfile> filter=git-crypt diff=git-crypt
<secretdir/**> filter=git-crypt diff=git-crypt
```

```sh
git-crypt init
git-crypt add-gpg-user <gnupg_email@exaple.com>
git-crypt status
git add .gitattributes
git commit -m "Enable git-crypt"
git push -u origin main
```

```sh
git-crypt export-key <path_to>/<name>.git-crypt
```

```sh
git-crypt unlock <path_to>/<name>.git-crypt
```
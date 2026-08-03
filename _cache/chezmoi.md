```sh
# rm -rf ~/.local/share/chezmoi
# rm -rf ~/.config/chezmoi
chezmoi init
vim ~/.local/share/chezmoi/.chezmoiignore
```

```
<ignore_file>
<ignore_dir>/
```

```sh
chezmoi add <dotfiles>
chezmoi cd
```

```sh
git remote add origin https://github.com/<user>/<repo>
git branch -M main
git add .
git commit -m "<commit>"
git push -u origin main
```

On another PC:

```sh
chezmoi init https://github.com/<user>/<repo>
chezmoi diff
chezmoi apply -v
# Pull updates
chezmoi update -v
```
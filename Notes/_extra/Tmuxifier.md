---
tags: arch
---

```sh
git clone --depth=1 https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
git clone --depth=1 https://github.com/jimeh/tmuxifier ~/.tmuxifier
chmod +x ~/.tmuxifier/bin/tmuxifier
~/.tmux/plugins/tpm/bin/install_plugins
```

```sh
# .zshrc
export PATH="$HOME/.tmuxifier/bin:$PATH"
export TMUXIFIER_LAYOUT_PATH="$HOME/Usr/Git/Shell/_arch/tmuxifier"
export TMUXIFIER_TMUX_OPTS=""
eval "$(tmuxifier init -)"
```
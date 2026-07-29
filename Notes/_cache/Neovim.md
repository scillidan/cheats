Build from source on Ubuntu 22 ARM[^1][^2][^3]\:

```sh
sudo apt-get install ninja-build gettext cmake unzip curl
```

1. Get `Source code` from [Neovim - Releases](https://github.com/neovim/neovim/releases)
2. Decompress it to `neovim/`

```sh
cd neovim
# rm -r build
make CMAKE_EXTRA_FLAGS="-DCMAKE_INSTALL_PREFIX=$HOME/neovim"
make install
ln -s ~/neovim/bin/nvim ~/.local/bin/
# rm -rf ~/.local/share/nvim/lazy/
nvim
```

[^1]: [PPA not working with lazy.nvim](https://www.reddit.com/r/neovim/comments/166fpfb/ppa_not_working_with_lazynvim/)
[^2]: [Neovim - Build prerequisites](https://github.com/neovim/neovim/blob/master/BUILD.md#build-prerequisites)
[^3]: [Install from source](https://github.com/neovim/neovim/blob/master/INSTALL.md#install-from-source)
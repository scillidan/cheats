## install

```sh
# Windows 10
git clone --depth=1 https://github.com/denizsafak/abogen
cd abogen
uv venv
source .venv/bin/activate
uv pip install torch torchaudio torchvision --index-url https://download.pytorch.org/whl/cu128
uv pip install abogen
abogen
```

```sh
# Arch
python -m venv .abogen
source .abogen/bin/activate
pip3 install abogen
```

```sh
# For AMD GPU
pip3 uninstall torch 
pip3 install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/rocm6.4
ln -sfn $(pwd)/.abogen/bin/abogen ~/.local/bin/abogen
deactivate
```

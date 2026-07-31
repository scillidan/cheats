## With Nvidia

```sh
git clone --depth=1 https://github.com/comfyanonymous/ComfyUI
cd ComfyUI
python -m venv .venv
.venv\Scripts\activate
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
pip install -r requirements.txt
```

```sh
python main.py
```

## With AMD[^1]

```sh
git clone --depth=1 https://github.com/comfyanonymous/ComfyUI
cd ComfyUI
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
pip install torch-directml
set HSA_OVERRIDE_GFX_VERSION=10.3.0
```

```sh
python main.py --directml
```

## Usage

- ComfyUI → Manager
	- Custom Nodes Manager → Search → Install
	- Install Missing Custom Nodes

[^1]: [Installing ComfyUI on Windows for AMD GPUs](https://atlassc.net/2025/01/15/installing-comfyui-on-windows-for-amd-gpus)
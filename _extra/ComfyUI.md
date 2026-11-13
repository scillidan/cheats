## With Nvidia

```sh
git clone --depth=1 https://github.com/comfyanonymous/ComfyUI
cd ComfyUI
python -m venv .venv
.venv/Scripts/activate
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
.venv/Scripts/activate
pip install -r requirements.txt
pip install torch-directml
set HSA_OVERRIDE_GFX_VERSION=10.3.0
```

## With plugins

```sh
# ComfyUI Easy Use
git clone --depth=1 https://github.com/yolain/ComfyUI-Easy-Use custom_nodes/comfyui-easy-use
pip install -r custom_nodes/comfyui-easy-use/requirements.txt
```

```sh
# ComfyUI Manager
git clone --depth=1 https://github.com/ltdrdata/ComfyUI-Manager custom_nodes/comfyui-manager
pip install -r custom_nodes/comfyui-manager/requirements.txt
```

```sh
# ComfyUI-GGUF
git clone --depth=1 https://github.com/city96/ComfyUI-GGUF custom_nodes/comfyui-gguf
pip install -r custom_nodes/comfyui-gguf/requirements.txt
```

```sh
# ComfyUI-Impact-Pack
git clone --depth=1 https://github.com/ltdrdata/ComfyUI-Impact-Pack custom_nodes/comfyui-impact-pack
pip install -r custom_nodes/comfyui-impact-pack/requirements.txt
```

```sh
# KJNodes for ComfyUI
git clone --depth=1 https://github.com/kijai/ComfyUI-KJNodes custom_nodes/comfyui-kjnodes
pip install -r custom_nodes/comfyui-kjnodes/requirements.txt
```

```sh
# WAS Node Suite v3
git clone --depth=1 https://github.com/WASasquatch/was-node-suite-comfyui custom_nodes/was-node-suite-comfyui
pip install -r custom_nodes/was-node-suite-comfyui/requirements.txt
pip install -r custom_nodes/was-node-suite-comfyui/requirements/llm.txt
```

```sh
# WhiteRabbit
git clone --depth=1 https://github.com/Artificial-Sweetener/WhiteRabbit custom_nodes/WhiteRabbit
pip install "torchlanc>=1.1.0" -r custom_nodes/WhiteRabbit/requirements.txt
```

```sh
python main.py
```

## Usage

- ComfyUI → Manager
	- Custom Nodes Manager → Search → Install
	- Install Missing Custom Nodes

## Cache

```sh
# ComfyUI Frame Interpolation
git clone --depth=1 https://github.com/Fannovel16/ComfyUI-Frame-Interpolation custom_nodes/comfyui-frame-interpolation
pip install -r custom_nodes/comfyui-frame-interpolation/requirements-with-cupy.txt
```


```sh
# ComfyUI-RMBG
git clone --depth=1 https://github.com/1038lab/ComfyUI-RMBG custom_nodes/comfyui-rmbg
# https://github.com/IDEA-Research/GroundingDINO/issues/347
pip install groundingdino-py-0.4.0.zip
pip install -r custom_nodes/comfyui-rmbg/requirements.txt
```


```sh
# ComfyUI-Trellis2
pip install torch==2.8.0 torchvision==0.23.0 torchaudio==2.8.0 --index-url https://download.pytorch.org/whl/cu128
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/cumesh-1.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/nvdiffrast-0.4.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/nvdiffrec_render-0.0.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/flex_gemm-0.0.1-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/o_voxel-0.0.1-cp312-cp312-win_amd64.whl
pip install -r custom_nodes/ComfyUI-Trellis2/requirements.txt
python -c "import torch; print(torch.__version__); import cumesh, o_voxel, flex_gemm; print('OK')"
```

[^1]: [Installing ComfyUI on Windows for AMD GPUs](https://atlassc.net/2025/01/15/installing-comfyui-on-windows-for-amd-gpus)
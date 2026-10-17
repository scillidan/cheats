```sh
cd ComfyUI
.venv\Scripts\activate
pip install torch==2.8.0 torchvision==0.23.0 torchaudio==2.8.0 --index-url https://download.pytorch.org/whl/cu128
```

```sh
git clone --depth=1 https://github.com/visualbruno/ComfyUI-Trellis2 custom_nodes/ComfyUI-Trellis2
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/cumesh-1.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/nvdiffrast-0.4.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/nvdiffrec_render-0.0.0-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/flex_gemm-0.0.1-cp312-cp312-win_amd64.whl
pip install custom_nodes/ComfyUI-Trellis2/wheels/Windows/Torch280/o_voxel-0.0.1-cp312-cp312-win_amd64.whl
pip install -r custom_nodes/ComfyUI-Trellis2/requirements.txt
```

```sh
python -c "import torch; print(torch.__version__); import cumesh, o_voxel, flex_gemm; print('OK')"
```
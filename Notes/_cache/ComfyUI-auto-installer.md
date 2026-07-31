See https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer

## Install (Cache)

Put `file.json` into `ComfyUI/user/default/workflows/`.

```sh
git clone --depth=1 https://github.com/ltdrdata/ComfyUI-Manager custom_nodes\comfyui-manager
pip install -r custom_nodes\comfyui-manager\requirements.txt
git clone --depth=1 https://github.com/ltdrdata/ComfyUI-Impact-Pack custom_nodes\comfyui-impact-pack
pip install -r custom_nodes\comfyui-impact-pack\requirements.txt
git clone --depth=1 https://github.com/ltdrdata/ComfyUI-Impact-Subpack custom_nodes\comfyui-impact-subpack
pip install -r custom_nodes\comfyui-impact-subpack\requirements.txt
git clone --depth=1 https://github.com/city96/ComfyUI-GGUF custom_nodes\comfyui-gguf
pip install -r custom_nodes\comfyui-gguf\requirements.txt
git clone --depth=1 https://github.com/Smirnov75/ComfyUI-mxToolkit custom_nodes\comfyui-mxtoolkit
git clone --depth=1 https://github.com/pythongosssss/ComfyUI-Custom-Scripts custom_nodes\comfyui-custom-scripts
git clone --depth=1 https://github.com/kijai/ComfyUI-KJNodes custom_nodes\comfyui-kjnodes
pip install -r custom_nodes\comfyui-kjnodes\requirements.txt
git clone --depth=1 https://github.com/kijai/ComfyUI-WanVideoWrapper custom_nodes\comfyui-wanvideowrapper
pip install -r custom_nodes\comfyui-wanvideowrapper\requirements.txt
git clone --depth=1 https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite custom_nodes\comfyui-videohelpersuite
pip install -r custom_nodes\comfyui-videohelpersuite\requirements.txt
git clone --depth=1 https://github.com/Fannovel16/ComfyUI-Frame-Interpolation custom_nodes\comfyui-frame-interpolation
pip install -r custom_nodes\comfyui-frame-interpolation\requirements-with-cupy.txt
git clone --depth=1 https://github.com/rgthree/rgthree-comfy custom_nodes\rgthree-comfy
pip install -r custom_nodes\rgthree-comfy\requirements.txt
git clone --depth=1 https://github.com/yolain/ComfyUI-Easy-Use custom_nodes\comfyui-easy-use
pip install -r custom_nodes\comfyui-easy-use\requirements.txt
git clone --depth=1 https://github.com/lldacing/ComfyUI_PuLID_Flux_ll custom_nodes\comfyui_pulid_flux_ll
pip install -r custom_nodes\comfyui_pulid_flux_ll\requirements.txt
pip install insightface==0.7.3
pip install git+https://github.com/rodjjo/filterpy
pip install onnxruntime==1.19.2 onnxruntime-gpu==1.17.1
git clone --depth=1 https://github.com/facok/ComfyUI-HunyuanVideoMultiLora custom_nodes\comfyui-hunyuanvideomultilora
git clone --depth=1 https://github.com/WASasquatch/was-node-suite-comfyui custom_nodes\was-node-suite-comfyui
pip install -r custom_nodes\was-node-suite-comfyui\requirements.txt
git clone --depth=1 https://github.com/kijai/ComfyUI-Florence2 custom_nodes\comfyui-florence2
pip install -r custom_nodes\comfyui-florence2\requirements.txt
git clone --depth=1 https://github.com/yuvraj108c/ComfyUI-Upscaler-Tensorrt custom_nodes\comfyui-upscaler-tensorrt
pip install -r custom_nodes\comfyui-upscaler-tensorrt\requirements.txt
git clone --depth=1 https://github.com/pollockjj/ComfyUI-MultiGPU custom_nodes\comfyui-multigpu
git clone --depth=1 https://github.com/Flow-two/ComfyUI-WanStartEndFramesNative custom_nodes\comfyui-wanstartendframesnative
git clone --depth=1 https://github.com/alexopus/ComfyUI-Image-Saver custom_nodes\comfyui-image-saver
git clone --depth=1 https://github.com/ssitu/ComfyUI_UltimateSDUpscale custom_nodes\comfyui_ultimatesdupscale
git clone --depth=1 https://github.com/Fannovel16/comfyui_controlnet_aux custom_nodes\comfyui_controlnet_aux
pip install -r custom_nodes\comfyui_controlnet_aux\requirements.txt
git clone --depth=1 https://github.com/XLabs-AI/x-flux-comfyui custom_nodes\x-flux-comfyui
pip install -r custom_nodes\x-flux-comfyui\requirements.txt
git clone --depth=1 https://github.com/1038lab/ComfyUI-RMBG custom_nodes\comfyui-rmbg
# https://github.com/IDEA-Research/GroundingDINO/issues/347
pip install groundingdino-py-0.4.0.zip
pip install -r custom_nodes\comfyui-rmbg\requirements.txt
```

```sh
git clone https://github.com/NVIDIA/apex
cd apex
git branch -a
git checkout -b 24.04.01-devel origin/24.04.01-devel
pip install -v --no-cache-dir --no-build-isolation .
cd ..
# Download .whl from https://hf-mirror.com/UmeAiRT/ComfyUI-Auto_installer/tree/main/whl
pip install triton-3.3.0-py3-none-any.whl
pip install triton-windows
pip install mpmath==1.3.0 xformers==0.0.30
# Download .whl from https://huggingface.co/Panchovix/sageattention2.1.1-blackwell2.0-windows-nightly/blob/main/sageattention-2.1.1-cp312-cp312-win_amd64.whl
pip install sageattention-2.1.1-cp312-cp312-win_amd64.whl
# pip install apex-0.1-py3-none-any.whl mpmath-1.3.0-py3-none-any.whl sageattention-2.1.1-cp312-cp312-win_amd64.whl triton-3.3.0-py3-none-any.whl xformers-0.0.30%2B3abeaa9e.d20250426-cp312-cp312-win_amd64.whl
python main.py --windows-standalone-build --lowvram --use-sage-attention
```

## Download models

```
# From https://hf-mirror.com/UmeAiRT/ComfyUI-Auto_installer/tree/main/models/diffusion_models/FLUX
# From https://hf-mirror.com/UmeAiRT/ComfyUI-Auto_installer/tree/main/models/unet/FLUX
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip/clip_l.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip/longclip-L.pt?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip/t5-v1_1-xxl-encoder-Q3_K_L.gguf?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip/t5xxl_fp8_e4m3fn.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip/ViT-L-14-TEXT-detail-improved-hiT-GmP-TE-only-HF.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip_vision/clip_vision_h.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/clip_vision/sigclip_vision_patch14_384.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/controlnet/diffusion_pytorch_model_promax.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/controlnet/Shakker-LabsFLUX1-dev-ControlNet-Union-Pro.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/pulid/pulid_flux_v0.9.0.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/style_models/flux1-redux-dev.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/upscale_models/RealESRGAN_x4plus.pth?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/upscale_models/RealESRGAN_x4plus_anime_6B.pth?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/vae/ae.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/xlabs/controlnets/flux-canny-controlnet-v3.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/xlabs/controlnets/flux-depth-controlnet-v3.safetensors?download=true
https://huggingface.co/UmeAiRT/ComfyUI-Auto_installer/resolve/main/models/xlabs/controlnets/flux-hed-controlnet-v3.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Ume_Sky/resolve/main/ume_sky_v2.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Modern_Pixel_art/resolve/main/ume_modern_pixelart.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Romanticism/resolve/main/ume_classic_Romanticism.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Impressionism/resolve/main/ume_classic_impressionist.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Ume_J1900/resolve/main/umej1900.safetensors?download=true
https://huggingface.co/UmeAiRT/FLUX.1-dev-LoRA-Ume_Knight/resolve/main/ume_gachaak.safetensors?download=true
```

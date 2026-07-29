```sh
git clone --depth=1 https://github.com/fishaudio/fish-speech
cd fish-speech
uv venv --python 3.12
.venv/Scripts/activate
uv pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
uv pip install https://github.com/AnyaCoder/fish-speech/releases/download/v0.1.0/triton_windows-0.1.0-py3-none-any.whl
uv pip install -e .
uv pip install hf_transfer
```

1. Create folder `checkpoints/`.
2. Download [fishaudio/openaudio-s1-mini](https://huggingface.co/fishaudio/openaudio-s1-mini/tree/main) into `checkpoints\openaudio-s1-mini`.

```sh
python -m tools.run_webui --llama-checkpoint-path "checkpoints/openaudio-s1-mini" --decoder-checkpoint-path "checkpoints/openaudio-s1-mini/codec.pth" --decoder-config-name modded_dac_vq
```
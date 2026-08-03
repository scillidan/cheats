```sh
git lfs install
git clone --depth=1 https://github.com/index-tts/index-tts
cd index-tts
git lfs pull
uv sync --all-extras
uv tool install "huggingface-hub[cli,hf_xet]"
hf download IndexTeam/IndexTTS-2 --local-dir=checkpoints
```

```sh
uv run tools/gpu_check.py
```

```sh
uv run webui.py
```
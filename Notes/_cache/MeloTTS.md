---
description: High-quality multi-lingual text-to-speech library by MyShell.ai
tags: audio
---

```sh
git clone --depth=1 https://github.com/myshell-ai/MeloTTS
uv venv --python 3.10
.venv\Scripts\activate
uv pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
uv pip install -e .
uv pip install hf_transfer
python -m unidic download
```

```sh
melo "Hello" temp.wav --language EN
melo --device cuda --language EN "<text>" temp.wav && ffplay -autoexit temp.wav
```

```sh
# With Web UI
python melo/app.py
```
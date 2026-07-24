---
description: A deep learning toolkit for Text-to-Speech, battle-tested in research and production
tags: audio
---

```sh
# https://stackoverflow.com/questions/66726331/how-can-i-run-mozilla-tts-coqui-tts-training-with-cuda-on-a-windows-system
git clone --depth=1 https://github.com/coqui-ai/TTS
uv venv --python 3.10
.venv\Scripts\activate
uv pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
uv pip install -e .
uv pip install transformers==4.40.2
```
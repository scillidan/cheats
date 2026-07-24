---
description: Quick CLI for local text-to-speech using Qwen3-TTS or Kokoro TTS
tags: audio
---

```sh
git clone --depth=1 https://github.com/fcjr/ltts
cd ltts
uv venv .venv --python 3.12
.venv\bin\activate
uv pip install hf_transfer hf-xet
uv sync
```

```sh
ltts $1 -v af_bella --say
ltts $1 -v af_bella -o $2.mp3
```
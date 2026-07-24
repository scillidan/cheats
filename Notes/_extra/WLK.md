---
description: Ultra-low-latency, self-hosted speech-to-text pipeline
tags: audio
---

```sh
git clone --depth=1 https://github.com/QuentinFuxa/WhisperLiveKit
cd WhisperLiveKit
uv venv --python 3.12
uv pip install -e .
uv pip uninstall torch
uv pip install torch --index-url https://download.pytorch.org/whl/cu129
```

```sh
# Optional
uv pip install faster-whisper
uv pip install nllw
# uv pip install git+https://github.com/NVIDIA/NeMo.git@main#egg=nemo_toolkit[asr]
uv pip install nemo_toolkit[asr]
```

```sh
wlk --model base --language en
wlk --host localhost --port 8000 --model large --diarization
```
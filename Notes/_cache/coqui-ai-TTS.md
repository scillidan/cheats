---
description: A deep learning toolkit for Text-to-Speech
tags: audio
---

```sh
git clone --depth=1 https://github.com/idiap/coqui-ai-TTS
uv venv --python 3.10
.venv\Scripts\activate.bat
uv pip install torch --index-url https://download.pytorch.org/whl/cu124
uv pip install -e .
```

```sh
tts --list_models
tts --model_name "tts_models/multilingual/multi-dataset/xtts_v2" --list_language_idxs
tts --model_name "tts_models/multilingual/multi-dataset/xtts_v2" --list_speaker_idxs
tts --text "<text>" --model_path "<path_to>" --config_path "<path_to>\config.json" --language_idx "en" --speaker_wav "<path_to>\ref.wav" --out_path output.wav
```
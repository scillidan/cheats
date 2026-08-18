```sh
# https://stackoverflow.com/questions/66726331/how-can-i-run-mozilla-tts-coqui-tts-training-with-cuda-on-a-windows-system
git clone --depth=1 https://github.com/coqui-ai/TTS
uv venv --python 3.10
.venv/Scripts/activate
uv pip install torch --index-url https://download.pytorch.org/whl/cu124
uv pip install -e .
```

```sh
tts --list_models
tts --model_name "tts_models/multilingual/multi-dataset/xtts_v2" --list_language_idxs
tts --model_name "tts_models/multilingual/multi-dataset/xtts_v2" --list_speaker_idxs
tts --device cuda --model_name "tts_models/multilingual/multi-dataset/xtts_v2" --language_idx "<lang>" --speaker_idx "<speaker>" --out_path <wav> --text "<text>"
tts --device cuda --model_path "<path>" --language_idx "<lang>" --config_path "<path>/config.json" --speaker_wav "<path>/ref.wav" --out_path <wav> --text "<text>"
```

## Speakers

```
Suad Qasim         # female, low voice, 2
Ana Florence       # female, low voice, 3
Zacharie Aimilios  # male, low voice, 2
Eugenio Mataracı   # male, low voice, 3
Dionisio Schuyler  # male, low voice, 4
Viktor Eka         # male, low voice, 5
...
```
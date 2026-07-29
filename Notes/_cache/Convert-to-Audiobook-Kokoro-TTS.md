```sh
git clone --depth=1 https://github.com/Pazran/audiobook-kokoro-tts
cd audiobook-kokoro-tts
cp convert_to_audiobook.py convert_to_audiobook_user.py
subl convert_to_audiobook.py
```

```py
VOICE = "af_bella"
MODEL_FILE = "<path_to>\\kokoro-v1.0.onnx"
VOICES_FILE = "<path_to>\\voices-v1.0.bin"
```

```sh
python convert_to_audiobook.py <path_to_book>
```
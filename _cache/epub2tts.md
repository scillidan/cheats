```sh
git clone --depth=1 https://github.com/aedocw/epub2tts
cd epub2tts
uv venv --python 3.11
.venv\Scripts\activate
uv pip install torch torchaudio --index-url https://download.pytorch.org/whl/cu121
uv pip install coqui-tts --only-binary spacy
uv pip install -e .
```

```sh
# Extract epub contents to text
epub2tts <epub> --export txt
# https://github.com/aedocw/epub2tts?tab=readme-ov-file#extract-epub-contents-to-text
```

```sh
# Coqui TTS 
epub2tts <formatted_txt> --engine tts --language en --speaker "Suad Qasim" --cover cover-image.jpg --sayparts
```

Edit `requirements.txt`[^1]\:

```
# deepspeed
```

[^1]: ["Unable to import torch" error on Windows](https://github.com/aedocw/epub2tts/issues/218)
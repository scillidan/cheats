```sh
# Pip
uv tool install kokoro-tts --python 3.12
```

1. Download voice data (bin format is preferred) from [here](https://github.com/nazdridoy/kokoro-tts/releases/download/v1.0.0/voices-v1.0.bin)
2. Download the model from [here](https://github.com/nazdridoy/kokoro-tts/releases/download/v1.0.0/kokoro-v1.0.onnx)

```sh
# https://github.com/nazdridoy/kokoro-tts#usage
echo "<content>" | kokoro-tts - --stream --voice "af_bella" --voices <path_to>\voices-v1.0.bin --model <path_to>\kokoro-v1.0.onnx
```
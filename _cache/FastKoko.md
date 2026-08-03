```sh
git clone --depth=1 https://github.com/remsky/Kokoro-FastAPI
cd Kokoro-FastAPI
```

```sh
uv venv --python 3.10
.venv/Scripts/activate
# set PHONEMIZER_ESPEAK_LIBRARY="<path_to>\libespeak-ng.dll"
# set PHONEMIZER_ESPEAK_PATH="<path_to>\espeak-ng.exe"
set PYTHONUTF8=1
set PROJECT_ROOT=%cd%
set USE_GPU=true
set USE_ONNX=false
set PYTHONPATH=%PROJECT_ROOT%;%PROJECT_ROOT%\api
set MODEL_DIR=src\models
set VOICES_DIR=src\voices\v1_0
set WEB_PLAYER_PATH=%PROJECT_ROOT%\web
uv pip install torch --index-url https://download.pytorch.org/whl/cu129
uv pip install -e ".[gpu]"
```
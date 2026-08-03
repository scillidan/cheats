```sh
git clone --depth=1 https://github.com/dmMaze/BallonsTranslator
cd BallonsTranslator
uv venv --python 3.12
.venv\Scripts\activate
uv pip install torch torchvision --index-url https://download.pytorch.org/whl/cu124
uv pip install -r requirements.txt
uv pip install pip
launch_win.bat
```

```sh
python launch.py
```

- Setting
	- DL Module → Translator
	- General → Typesetting → Auto layout (Off)

```batch
REM start_ballonstranslator.bat
@echo off

cd C:\Users\User\Usr\OptWeb\SakuraLLM
start .venv\Scripts\python.exe server.py --trust_remote_code --model_name_or_path models/sakura-13b-lnovel-v0.9b-Q2_K.gguf --model_version 0.9 --no-auth --llama_cpp --use_gpu --log debug

cd C:\Users\User\Usr\OptWeb\BallonsTranslator
start .venv\Scripts\python.exe launch.py

pause
```
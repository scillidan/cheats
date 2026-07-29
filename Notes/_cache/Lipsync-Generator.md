```sh
git clone --depth=1 https://github.com/fralapo/LipSyncify
cd LipSyncify
uv venv
.venv\Scripts\activate
uv pip install torch torchaudio torchvision --extra-index-url https://download.pytorch.org/whl/cu121
uv pip install -r requirements.txt
```

```sh
python3 generate_lipsync.py --background yellow
```
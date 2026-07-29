```sh
git clone --depth=1 https://github.com/p0n1/epub_to_audiobook
cd epub_to_audiobook
uv venv
.venv/Scripts/activate
uv pip install -r requirements.txt
```

```sh
python main.py --tts edge --language en-US <epub> <output_folder>
```
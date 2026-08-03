```sh
git clone --depth=1 https://github.com/bashexplode/sf2-to-sfz
cd sf2-to-sfz
uv venv
.venv/Scripts/activate
uv pip install sf2utils
```

```sh
python sf2_to_sfz.py file.sf2 file.sfz
```
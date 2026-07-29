```sh
git clone --depth=1 https://github.com/sedthh/pyxelate
uv venv .venv --python 3.9
.venv/Scripts/activate
uv pip install -r requirements.txt
uv pip install -e .
```

```sh
pyxelate $1 _pyxelate.png --factor 9 --upscale 5 --palette 10 --nosvd
```
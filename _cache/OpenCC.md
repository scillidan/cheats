```sh
# Arch
sudo pacman -S opencc
opencc -c /usr/share/opencc/t2s.json -i input.txt -o output.txt
```

```sh
# uv
uv venv .opencc --python 3.10
.opencc/Scripts/activate
uv pip install opencc
.opencc/Lib/site-packages/opencc/clib/bin/opencc -c .opencc/Lib/site-packages/opencc/clib/share/opencc/t2s.json -i input.txt -o output.txt
```
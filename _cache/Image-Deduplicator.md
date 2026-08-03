```sh
git clone --depth=1 https://github.com/idealo/imagededup
cd imagededup
uv python install 3.8.*
uv venv --python 3.8.*
.venv/Scripts/activate
uv pip install "cython>=0.29" setuptools
python setup.py install
```
```sh
git clone --depth=1 https://github.com/pkhungurn/talking-head-anime-4-demo
cd talking-head-anime-4-demo
uv venv
.venv\Scripts\activate
uv pip install poetry
cd poetry
poetry install
```

```sh
cd ..
python src\tha4\app\character_model_ifacialmocap_puppeteer.py
```
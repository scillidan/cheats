---
description: A desktop app that translates books, subtitles, and documents with AI - local or cloud. Drop a file, pick a language, get the result
tags: text
---

```sh
git clone --depth=1 https://github.com/hydropix/TranslateBooksWithLLMs
cd TranslateBooksWithLLMs
uv venv --python 3.12
.venv\Scripts\activate
uv pip install -r requirements.txt
```

```sh
python translation_api.py
```
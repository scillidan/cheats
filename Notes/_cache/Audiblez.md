---
description: Generate audiobooks from e-books
tags: audio
---

```sh
# https://github.com/santinic/audiblez
uv venv .audiblez --python 3.12
.audiblez\Scripts\activate.bat
python -m ensurepip --upgrade
python -m spacy download xx_ent_wiki_sm
```

```sh
audiblez-ui
```
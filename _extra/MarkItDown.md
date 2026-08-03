---
tags: pdf
---

```sh
git clone --depth=1 https://github.com/microsoft/markitdown
cd markitdown
uv venv --python 3.12
.venv/Scripts/activate
uv pip install -e "packages/markitdown[all]"
```
---
tags: project, translation, cli
---

# https://github.com/yihong0618/bilingual_book_maker

```bash
uv venv .bilingual_book_maker --python 3.12
.bilingual_book_maker\Scripts\activate
uv pip install -U bbook_maker
bbook_maker --ollama_model gemma3:12b --book_name <epub>
deactivate
cd .bilingual_book_maker
uv pip install -U bbook_maker
uv run bbook_maker --ollama_model gemma3:12b --book_name <epub>
```

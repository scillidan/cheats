---
description: Transforms complex documents like PDFs and Office docs into LLM-ready markdown/JSON for your Agentic workflows
tags: text
---

```sh
# https://opendatalab.github.io/MinerU/quick_start
git clone --depth=1 https://github.com/opendatalab/MinerU
cd MinerU
uv venv .mineru --python 3.12
source .venv/bin/activate
uv pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
uv pip install -U "mineru[all]"
uv pip install hf_transfer
```

```sh
uv run mineru -p <input> -o <output>
uv run mineru-gradio --server-name 0.0.0.0 --server-port 7860
```
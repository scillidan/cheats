---
description: Efficient Portrait Animation with Stitching and Retargeting Control
tags: video
---

```sh
git clone --depth=1 https://github.com/KwaiVGI/LivePortrait
cd LivePortrait
conda create -n LivePortrait python=3.10
conda activate LivePortrait
pip install torch==2.3.0 torchvision==0.18.0 torchaudio==2.3.0 --index-url https://download.pytorch.org/whl/cu121
pip install -r requirements.txt
pip install hf_transfer
pip install -U "huggingface_hub[cli]"
# set HF_ENDPOINT=https://hf-mirror.com
huggingface-cli download KwaiVGI/LivePortrait --local-dir pretrained_weights --exclude "*.git*" "README.md" "docs"
```

```sh
# https://github.com/gradio-app/gradio/issues/10662
python inference.py
```

```sh
pip install pydantic==2.8.2
python app.py --flag_do_torch_compile
```
---
description: Intelligent OCR System · Vue 3 Modern UI · Batch Processing · Multi-Mode Support
tags: text
---

```sh
git clone --depth=1 https://github.com/neosun100/DeepSeek-OCR-WebUI
uv venv --python 3.12
source .venv/bin/activate.bat
uv pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
uv pip install -w fastapi uvicorn python-multipart -r requirements.txt
python web_service_gpu.py
deactivate.bat
cd DeepSeek-OCR-WebUI
uv run python web_service_gpu.py
```

```sh
uv tool install modelscope
mkdir ./deepseek-ocr-2
modelscope download --model deepseek-ai/DeepSeek-OCR-2 --local_dir ./deepseek-ocr-2
git clone --depth=1 https://github.com/fufankeji/DeepSeek-OCR-2-Studio-Web
uv venv --python 3.12
source .venv/bin/activatea
uv pip install torch==2.6.0 torchvision==0.21.0 torchaudio==2.6.0 --index-url https://download.pytorch.org/whl/cu118
uv pip install ./packages/vllm-0.8.5+cu118-cp38-abi3-manylinux1_x86_64.whl
cd ./DeepSeek-OCR/
uv pip install -r requirements.txt
pip install flash-attn==2.7.3 --no-build-isolation
vim .env
```

```
MODEL_PATH=/your/path/to/deepseek-ocr-2
```

```sh
cd backend
uvicorn main:app --host 0.0.0.0 --port 9002
```

```sh
cd frontend
npm install
npm run dev
```
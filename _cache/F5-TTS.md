```sh
git clone --depth=1 https://github.com/SWivid/F5-TTS
cd F5-TTS
conda create -n f5-tts python=3.11
conda install ffmpeg
conda activate f5-tts
pip install torchcodec==0.7 torch==2.8.0+cu128 torchaudio==2.8.0+cu128 --extra-index-url https://download.pytorch.org/whl/cu128
pip install -e .
pip install hf_transfer
```

```sh
f5-tts_infer-gradio
```
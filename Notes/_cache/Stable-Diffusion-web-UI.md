```sh
git clone --depth=1 https://github.com/AUTOMATIC1111/stable-diffusion-webui
cd stable-diffusion-webui
python -m venv venv
venv\Scripts\activate
pip install torch torchvision torchaudio xformers --index-url https://download.pytorch.org/whl/cu121
subl webui-user.bat
```

```
set COMMANDLINE_ARGS=--xformers --port <port>
set XFORMERS_MORE_DETAILS=1
```

Download type `Checkpoint *` and put file `*.safetensors` into `models/Stable-diffusion`. Liked [Earth Satellite Image Map Generator Mix](https://civitai.com/models/18022/earth-satellite-image-map-generator-mix).

```sh
pip install hf_transfer
webui-user.bat
```

## Install extensions

1. Extensions → Available → Load from → Search and Install.
2. Extensions → Install from URL.
3. Extensions → Installed → Apply and restartUI.

## Note

```
,   提示词分隔符
_   连词
75 	最好控制在75单词以内
() 	控制权重；格式为`提示词:权重`；数值建议为0.3-1.5
1   默认权重；提示词在数组中越靠前权重越高
[] 	控制生效时间；格式为`提示词:0-1`，表示时间外生效；或者`提示词::0-1`，表示时间内生效；或者`提示词1:提示词2:0-1`
\| 	交替采样
<> 	控制Lora；格式为`lora:触发词:权重`
```

[^1]: [Manual Installation](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs#manual-installation)
[^2]: [How on earth can I install xformers?](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/9802#discussioncomment-5894895)
[^3]: [Installing xFormers](https://github.com/facebookresearch/xformers#installing-xformers)
[^4]: [Command Line Arguments and Settings](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Command-Line-Arguments-and-Settings)
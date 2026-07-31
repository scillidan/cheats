## Build Distributions on Windows 10

1. Download `SDK.zip` from [Download Ren'Py](https://www.renpy.org/latest.html)
2. Decompress it to `renpy-*-sdk\`
3. Run `renpy-*-sdk\renpy.exe`
4. preferences → General → Projects Directory → `<path_to>\proj_renpy` → Return
5. `cd <path_to>\proj_renpy`
6. `git clone --depth=1 https://codeberg.org/fhs/katawa-shoujo-re-engineered`
7. Renpy → PROJECTS → refresh → Select `katawa-shoujo-re-engineered`
8. Build Distributions → Build

## Build Android on Windows 10

1. Install [JDK](https://www.oracle.com/java/technologies/downloads/) and [Gradle](https://gradle.org/). For example:
  1. Download and Decompress `OpenJDK21U-jdk_x64_windows_hotspot_21.0.4_7.zip` to `jdk-21.04\`
  2. Download and Decompress `gradle-8.5-bin.zip` to `gradle-8.5\`. Or put `gradle-8.5-bin.zip` into `%USERPROFILE%\.gradle\wrapper\dists\gradle-8.5-bin\<some_string>\`
2. Add `jdk-21.04\bin`, `gradle-8.5\bin` into PATH
3. Restart Renpy

- Renpy → Android → Build
  1. Install SDK
  2. Generate Keys
  3. Build Package

## Build renpy documentation on Ubuntu 24.04 ARM[^1]

```sh
sudo apt install virtualenvwrapper python3-dev libavcodec-dev libavformat-dev libswresample-dev libswscale-dev libharfbuzz-dev libfreetype6-dev libfribidi-dev libsdl2-dev libsdl2-image-dev libsdl2-gfx-dev libsdl2-mixer-dev libsdl2-ttf-dev libjpeg-dev
. /usr/share/virtualenvwrapper/virtualenvwrapper.sh
mkvirtualenv renpy
pip install -U setuptools future six typing pefile requests ecdsa
pip install -U "cython<3.0.0"
```

```sh
git clone --depth=1 https://www.github.com/renpy/pygame_sdl2
pushd pygame_sdl2
python setup.py install
python install_headers.py $VIRTUAL_ENV
popd
```

```sh
LATEST_RELEASE=$(curl -s https://api.github.com/repos/renpy/renpy/releases/latest | jq -r .tag_name)
wget https://github.com/renpy/renpy/archive/refs/tags/$LATEST_RELEASE.zip
unzip $LATEST_RELEASE.zip
pushd renpy-*
pushd module
python setup.py install
cd ..
pushd sphinx
pip install -U sphinx sphinx_rtd_theme sphinx_rtd_dark_mode
./build.sh
```

[^1]: [renpy - Compiling the Modules](https://github.com/renpy/renpy#compiling-the-modules)
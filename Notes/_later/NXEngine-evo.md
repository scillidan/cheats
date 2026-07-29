---
description: A somewhat upgraded/refactored version of NXEngine by Caitlin Shaw
tags: game
---

## Build local-data

```sh
# Arch
git clone --depth=1 https://github.com/nxengine/translations
cd translations
cp build-local.sh build-local.sh.bak
vim build-local.sh
```

```
# Comment them
# wget https://github.com/nxengine/tsc-converter/releases/download/v1.1/tsc.tar.gz
# tar -zxf tsc.tar.gz
# rm -f tsc.tar.gz
# 
# wget https://github.com/nxengine/nx-fontgen/releases/download/v1.3/fontbm.tar.gz
# tar -zxf fontbm.tar.gz
# rm -f fontbm.tar.gz

# rm -f fontbm
# rm -f fontbm.bin
# rm -f tsc
# rm -rf assets
# rm -rf lib
```

```sh
cd local
wget https://github.com/nxengine/tsc-converter/releases/download/v1.1/tsc.tar.gz
tar -zxf tsc.tar.gz
wget https://github.com/nxengine/nx-fontgen/releases/download/v1.3/fontbm.tar.gz
tar -zxf fontbm.tar.gz
```

```sh
mv <font.ttf> assets/
```

```sh
git clone --depth=1 https://github.com/nxengine/lang_chinese lang_chinese
cp lang_chinese/metadata lang_chinese/metadata.bak
vim lang_chinese/metadata
# Replace `unifont-10.0.06.ttf` to `ark-pixel-12px-proportional-zh_cn.ttf`
```

```sh
cd ..
./build-local.sh
```

## Build game[^1]

```sh
git clone --depth=1 https://github.com/nxengine/nxengine-evo
cd nxengine-evo
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DPORTABLE=ON ..
make
cd ..
wget https://www.cavestory.org/downloads/cavestoryen.zip
unzip cavestoryen.zip
cp -r ../translations/local/data/lang/chinese/* CaveStory/data/
cp -r CaveStory/Doukutsu.exe CaveStory/data ./
build/nxextract
mkdir desk
cp -r build/nxengine-evo data desk/
desk/nxengine-evo
```

[^1]: [Building on Linux](https://github.com/nxengine/nxengine-evo/wiki/Building-on-Linux)
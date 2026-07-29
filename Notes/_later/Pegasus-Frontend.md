---
description: A cross platform, customizable graphical frontend for launching emulators and managing your game collection
tags: game
---

1. Get `pegasus-fe*.zip` from releases of [Pegasus Frontend](https://github.com/mmatyas/pegasus-frontend).
2. Decompress it to `pegasus-fe/`.
3. Get portable [RetroArch](https://www.retroarch.com/index.php?page=platforms), liked the `Download (64bit)`.
4. Decompress it to `pegasus-fe/RetroArch/`.
5. Get [K-Lite Codec Pack Basic](https://codecguide.com/download_k-lite_codec_pack_basic.htm).
6. Install it.

1. See [天马G PC+安卓双平台 精简Rom整合包 + 8大主题功能演示教程](https://www.bilibili.com/video/BV1vg4y1V7TB).
2. Download the `跳坑者联盟 PegasusG v1.2 完整版`.
3. Goto `【1】安装程序（安卓+PC）\【PC】专用安装包`.
4. Decompress `【Win 10及以上专用】天马G_PC主程序 v1.2 230605.7z`.
5. In `RetroArch`, copy these dirs to `pegasus-fe/RetroArch/`:
	 ```
	 cheats
	 config
	 cores
	 downloads
	 system
	 ```
6. In `config`, copy `*.txt` to `pegasus-fe/config/`.
7. Goto `【2】数据文件（安卓+PC）\【1】基础包_110GB`.
8. Decompress `基础包_110GB Roms.zip.*` to `pegasus-fe/Roms`.
9. Goto `【3】数据列表（安卓+PC）\【PC】metadata数据列表`.
10. Replace `pegasus-fe/Roms/**/metadata.pegasus.txt` with them.
11. If don't lanch game in pegasus-fe, check the line that write `launch: ...` of `metadata.pegasus.txt`. See more on [Metadata files](https://pegasus-frontend.org/docs/user-guide/meta-files/).
12. Clone some themes from [Pegasus Theme Gallery](https://pegasus-frontend.org/tools/themes) to `pegasus-fe\config\themes`.
13. Lanch `pegasus-fe.exe`.

```sh
subl roms/<platform>/metadata.pegasus.txt
```

```
# Windows 10
launch: "{env.PEGASUS_HOME}\RetroArch\retroarch.exe" -L "{env.PEGASUS_HOME}\RetroArch\cores\flycast_libretro.dll" "{file.path}"
```

```
# Arch
launch: "/home/<user>/RetroArch/retroarch" -L "/home/<user>/RetroArch/cores/flycast_libretro.so" "{file.path}"
```
---
tags: game
---

```sh
# https://egordorichev.itch.io/curse-of-the-arrow
unzip CurseOfTheArrow-V1.8.3-universal.love -d CurseOfTheArrow-V1.8.3-universal
cd CurseOfTheArrow-V1.8.3-universal
vim conf.lua
```

```lua
t.window.width = 96*5
t.window.height = 64*5
t.window.minwidth = 96
t.window.minheight = 64
```

```sh
7z a -tzip CurseOfTheArrow-V1.8.3-universal-640x480.love *
mv CurseOfTheArrow-V1.8.3-universal-640x480.love <RetroPie>/home/pi/RetroPie/roms/love/
```
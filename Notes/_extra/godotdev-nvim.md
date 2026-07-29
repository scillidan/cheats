---
tags: config
---

```sh
uv tool install gdtoolkit
uv tool install neovim-remote
```

- Godot → Editor → Editor Settings → Text Editor → External
	- Use External Editor (On)
	- Exec Path `/usr/bin/neovide`
	- Exec Flag `--frame=none {file}`
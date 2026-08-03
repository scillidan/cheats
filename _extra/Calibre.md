---
tags: config
---

## With Docker[^1]

```sh
mkdir calibre
cd calibre
vim docker-compose.yml
# Copy from https://docs.linuxserver.io/images/docker-calibre/#docker-compose-recommended-click-here-for-more-info
```

```yaml
		volumes:
			# Save calibre config (Including Cablire Library) on mount disk
			- /mnt/<mount_name>/local/share/calibre/config:/config
			- /mnt/<mount_name>/<book_storage>:/<book_storage>
```

```sh
sudo docker compose up -d
```

1. Cabibre → Preferences → Sharing → Sharing over the net → Run server automatically when calibre starts (On) → Start server.
2. The opds serve is on `http://<your_host>:8081/opds`.

## Config

### Main window

- Calibre → Preferences
	- Look & feel
		- Enable system tray icon (needs restart) (On)
		- Toolbar → Icon size → Small
	- Toolbars & menus → Current actions:
		```
		Add books
		Get books
		Choose library
		Create catalog
		--- Separator ---
		Preferences
		Help
		```

### Viewer toolbar[^2][^3]

1. Calibre → Select a book → View → View with calibre E-book viewer.
2. At the top of the reader → Show controls → Preferences
	- Miscellaneous
		- Show a toolbar with the most useful actions (On)
		- Customize toolbar → Current actions:
			```
			Switch color scheme
			Toggle paged mode
			Table of Contents
			Search
			Read aloud
			Lookup words
			```
	- Selection behavior
		- Current actions:
			```
			Looup/search selected word
			Read aloud
			Create a bookmark
			Highlight selection
			Remove this highlight
			```

### Read aloud

```sh
# Arch
yay -S --noconfirm piper-voices-en-us
```

- viewer → Toolbar → Read aloud → Configure
	- Text-to-Speech engine → `The Piper Neural Engine`.
	- Voices → English → `libritts (United States) [High quality]` → Download voice.

_But I can't download voice successes. So I put files liked `en_US-libritts-high.onnx`, `en_US-libritts-high.onnx.json` into `~/.cache/calibre/piper-voices/`._

### Lookup words

Lookup words → Add sources → For example, Add:

```
Name: etymonline.com
URL: https://www.etymonline.com/search?q={word}
```

```
# https://github.com/Crissium/SilverDict
Name: silverdict_<dict_group>
URL: http://<your_host>:2628/api/query/<dict_group>/{word}
```

```
# https://github.com/open-webui/open-webui
Name: open-webui_librarian
URL: http://<your_host>:<port>/?models=librarian-answer-in-zh&q={word}
```

## Usage

1. Calibre → Get books → Configure → `Project Gutenberg` (Enable).
2. Title → Entry `<book_name>` → Search.
3. Select a book → Enter → Check book format → Download.
4. Select book → View → View with calibre E-book viewer.

[^1]: [linuxserver/calibre](https://docs.linuxserver.io/images/docker-calibre)
[^2]: [How To Enable Sidebar in Calibre Ebook Viewer](https://www.youtube.com/watch?v=rJfbcTlvujQ)
[^3]: [Adding Dictionary In Calibre Ebook](https://www.youtube.com/watch?v=_lN1N90c8zw)
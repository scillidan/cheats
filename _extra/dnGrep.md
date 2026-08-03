---
tags: config, usage, windows
---

## Config

- dnGrep
	- Settings → Options
		- New versions → Check automatically every 10 days (Off)
		- Application fonts
			- Use default font (Off)
			- Font family → `Sarasa Term SC Nerd`
			- Results font family → `Sarasa Term SC Nerd`
		- Custom editor → Add
			- Sublime Text
				```
				Lable: Sublime Text
				Command: C:\Program Files\Sublime Text\subl.exe
				Arguments: %file:%line:%column
				```
		- Compare application
			```
			Command: WinMergeU.exe
			Arguments: /e /u /x
			```
	- Search results
		- Sort results automatically when search completes (On)
		- Show results tree expanded (On)
	- Search in
		- Patterns to match → `*.md;*.txt`
		- Patterns to exclude → `.git\*;node_modules;public;site;_build;_gen`
	- Results
		- Preview file (Off)

## Usage

- dnGrep
	- Results panel → More → Copy results
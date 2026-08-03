---
tags: config
---

```sh
mpv --input-ipc-server=/./pipe/kamite-mpvsocket --sub-file="$2" --sid=2 --secondary-sid=1 --secondary-sub-visibility=no --save-position-on-quit "$1"
```

## Config

`config.hocon`:

```
# https://github.com/fauu/Kamite/blob/master/config/config.default.hocon
# The modified lines, for example
lookup {
  targets = [
    ${LOOKUP_TARGETS.deepl}
    ${LOOKUP_TARGETS.reverso}
  ]
}

ocr: {
  engine: mangaocr
  tesseract: {
    path: "tesseract"
  }
  mangaocr: {
    pythonPath: "<path_to>/manga-ocr/Scripts/python.exe"
  }
  ocrspace: {
    engine: 1
  }
}

LOOKUP_TARGETS {
  deepl {
    symbol = DEP
    name = DeepL
    url = "https://www.deepl.com/translator#ja/en/{}"
  }
  reverso {
    symbol = REV
    name = Reverso
    url = "https://www.reverso.net/text-translation#sl=jpn&tl=eng&text={}"
  }
}

integrations: {
  agent: {
    enable: no
    host: "127.0.0.1:9001"
  }
}
```
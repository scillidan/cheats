---
tags: config, windows
---

- JPEGView → MBtm
  - Display order → File name
  - Zoom → Fit window to image (On)
  - Settings/Admin
    - Edit user settings    
      ```
      ShowFullScreen=false
      ShowNavPanel=false
      DefaultSaveFormat=png
      ```
    - Manage 'Open image with' menu → New
      ```
      Title: Fast Stone Viewer
      Application → Brower → `<path_to>/krita.exe`
      Shortcut key: Shift+p
      ```
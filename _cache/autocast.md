```sh
autocast input.yaml output.cast
```

```yaml
# starfetch.yaml
settings:
  width: 132
  height: 24
  # width: 151
  # height: 36
  title: starfetch
  type-speed: 150ms
  timeout: 90s

instructions:
  - !Marker Install
  - !Wait 1s
  - !Command
    command: "git clone --depth=1 https://github.com/Haruno19/starfetch"
  - !Wait 1s
  - !Command
    command: "cd starfetch"
  - !Wait 1s
  - !Command
    command: "make -j8"
  - !Wait 1s
  - !Command
    command: "# sudo make install"
  - !Wait 1s
  - !Clear

  - !Marker Usage
  - !Command
    command: "./starfetch -h"
  - !Wait 3s
  - !Clear
  - !Wait 3s
  - !Command
    command: "./starfetch -r"
  - !Wait 3s
  - !Command
    command: "./starfetch -n orion"
  - !Wait 3s

  # Cleanup
  - !Command
    command: "rm -rf starfetch"
    hidden: true
```

```yaml
# yt-dlp.yaml
# Record with https://github.com/Watfaq/PowerSession-rs.
settings:
  width: 151
  height: 36
  title: yt-dlp
  shell:
    program: pwsh
    prompt: "PS "
    line_split: ' \'
    quit_command: exit
  type-speed: 150ms
  timeout: 90s

instructions:
  - !Wait 1s
  - !Command
    command: "yt-dlp -F https://www.youtube.com/watch?v=LZ2kSbSrDLs"
  - !Wait 2s
  - !Clear
  - !Command
    command: "# yt-dlp -f bestvideo+bestaudio https://www.youtube.com/watch?v=LZ2kSbSrDLs"
  - !Wait 1s
```
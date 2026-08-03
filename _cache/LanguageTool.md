## On Ubuntu 22 ARM[^1][^2][^3]

Decompress `ngrams-en-*.zip` to `/mnt/<disk>/share/ngrams/`.

```sh
sudo apt install openjdk-21-jdk
sudo unzip LanguageTool-stable.zip
sudo mv LanguageTool-* /opt/languagetool
```

```sh
sudo apt install make g++
git clone --depth=1 https://github.com/facebookresearch/fastText
cd fastText
make
sudo vim /opt/languagetool/server.properties
```

```
fasttextModel=fasttext/lid.176.bin
fasttextBinary=fasttext/fasttext
```

```sh
sudo vim /etc/systemd/system/languagetool.service
```

```
[Unit]
Description=LanguageTool Service
After=network.target

[Service]
ExecStart=java -cp /opt/languagetool/languagetool-server.jar org.languagetool.server.HTTPServer --languagemodel /mnt/<nvme>/share/ngrams --port 8040 --allow-origin --public
WorkingDirectory=/opt/languagetool
Restart=on-abnormal

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl enable --now languagetool.service
```

1. Get `ngrams-en-*.zip` from [here](https://languagetool.org/download/ngram-data/)
2. Get `LanguageTool Desktop version for offline use` from [LanguageTool embedded HTTP Server](https://dev.languagetool.org/http-server)

## On Windows 10

1. Install [OpenJDK](https://jdk.java.net)，I tested it on [openjdk17](https://jdk.java.net/17/)
2. Decompress `ngrams-en-*.zip` to `ngrams/`
3. Decompress `LanguageTool-stable.zip` to `LanguageTool/`

```sh
unzip LanguageTool-stable.zip
java.exe -cp LanguageTool\languagetool-server.jar org.languagetool.server.HTTPServer --languagemodel <ngrams_dir> --port <port> --allow-origin
```

For running it liked service, create `languagetool_service.cmd` from the command above. Then create `languagetool_service.vbs`:

```
Set WshShell = CreateObject("WScript.Shell")
	WshShell.Run chr(34) & "languagetool_service.cmd" & Chr(34), 0
Set WshShell = Nothing
```

Create shortcut of `languagetool_service.vbs`, put it into `C:\Users\User\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\`.

## Browser Extension

1. Install [Browser Extension](https://languagetool.org/services#browsers)
2. Browser Extension → Settings → Advanced settings → Other server → `http://<your_host>:<port>/v2`
3. General settings → Show in right-click menu (On)

[^1]: [LanguageTool embedded HTTP Server](https://dev.languagetool.org/http-server)
[^2]: [Anyone self-hosting languagetool?](https://www.reddit.com/r/selfhosted/comments/ksvmii/anyone_selfhosting_languagetool/)
[^3]: [Finding errors using n-gram data](https://dev.languagetool.org/finding-errors-using-n-gram-data)
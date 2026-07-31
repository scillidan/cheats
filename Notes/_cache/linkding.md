## Install[^1][^2]

```sh
git clone --depth=1 https://github.com/sissbruecker/linkding
cd linkding
nvm install 18.*
nvm use 18.*
npm install
npm run build
```

```sh
uv venv
.venv\Scripts\activate
uv python -m pip install -r requirements.txt
uv python -m pip install -r requirements.prod.txt
uv pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser --username=<user> --email=<email>
```

## usage

```sh
cd linkding
npm run dev
```

```sh
# In a new terminal session
python manage.py runserver 8002
```

Visit `http://localhost:8002` to try it.

## Deploy with PM2[^3]

```sh
# Ubuntu 22 ARM
npm install -g concurrently
cp requirements.dev.txt requirements.dev.txt.bak
vim requirements.dev.txt
```

```
rcssmin
```

```sh
vim package.json
```

```json
{
  "scripts": {
    "start": "concurrently \"rollup -c -w\" \"python manage.py runserver 0.0.0.0:8060\""
```

```sh
pm2 start npm --name "linkding" -- run start
pm2 save
```

## Autorun at startup on Windows 10?

1. Create `start_linkding.bat`:
   ```batch
   @echo off
   setlocal
 
   cd linkding
   set LD_SUPERUSER_NAME=<user>
   set LD_SUPERUSER_PASSWORD=<password>
   start npm run dev
   timeout 5
   start .venv\Scripts\python.exe manage.py runserver 8002
 
   endlocal
   pause
   ```
2. Create `start_linkding.vbs`:
   ```vbs
   Set WshShell = CreateObject("WScript.Shell")
     WshShell.Run chr(34) & "<path_to>\start_linkding.cmd" & Chr(34), 0
   Set WshShell = Nothing
   ```
3. Create shortcut of `start_linkding.vbs`.
4. Put the shortcut into `C:\Users\User\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\`.

[^1]: [Development](https://github.com/sissbruecker/linkding#development)
[^2]: [linkding - Setup](https://github.com/sissbruecker/linkding/blob/master/README.md#setup)
[^3]: [ModuleNotFoundError: No module named 'ruamel'](https://github.com/fair-workflows/nanopub/issues/106)
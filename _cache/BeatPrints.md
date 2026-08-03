1. Visit [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).
2. Create app `BeatPrints`, add `http://localhost` on `Redirect URIs (required)`.
3. Go `Settings`, get `Client ID`, `Client secret`.
4. Add `SPOTIFY_CLIENT_ID`, `SPOTIFY_CLIENT_SECRET` into PATH.

```sh
git clone --depth=1 https://github.com/TrueMyst/BeatPrints
cd BeatPrints
uv venv
.venv/Scripts/activate
uv pip install -e .
uv pip install python-dotenv
```

```sh
# Windows 10
mkdir C:\Users\User\AppData\Roaming\BeatPrints
subl C:\Users\User\AppData\Roaming\BeatPrints\config.toml
```

```toml
[general]
search_limit = 7
output_directory = "C:\\Users\\User\\Downloads"

[credentials]
client_id = "SPOTIFY_CLIENT_ID"
client_secret = "SPOTIFY_CLIENT_SECRET"
```

```sh
beatprints
```
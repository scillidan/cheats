```sh
# On Linux
git clone git://git.codemadness.org/stagit
cd stagit
sudo apt install libgit2-dev
make
ln -s stagit ~/.local/bin/
ln -s stagit-index ~/.local/bin/
```

```sh
mkdir <dir>
cd <dir>
cp <path_to_stagit>/style.css ./
mkdir <subdir1>
mkdir <subdir2>
mkdir source
git clone <repo1> source/<subdir1>
git clone <repo2> source/<subdir2>
cd <subdir1>
stagit ../source/<subdir1>
cd ../<subdir2>
stagit ../source/<subdir2>
cd ..
stagit-index source/<subdir1> source/<subdir2> > index.html
```

```sh
magick convert image.png -resize 96x96 favicon.png
magick convert image.png -resize 96x96 logo.png
ln -s favicon.png <subdir1>/
ln -s favicon.png <subdir2>/
ln -s logo.png <subdir1>/
ln -s logo.png <subdir2>/
```
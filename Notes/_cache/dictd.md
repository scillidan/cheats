## On Ubuntu 22 ARM

[^1]

```sh
sudo apt install dictd
sudo vim /etc/dictd/dictd.conf
```

```
global {
    listen_to 0.0.0.0
    port 2628
}

access {
  allow *
}

include /var/lib/dictd/db.list

#LASTLINE
```

```sh
sudo vim /var/lib/dictd/db.list
```

```
# For example
database ecdict {
	data <path_to>/dictd/ecdict.dict.dz
	index <path_to>/dictd/ecdict.index
}
...
```

```sh
sudo systemctl enable --now dictd.service
systemctl status dictd.service
```

## On Arch

```sh
sudo pacman -S dictd
yay -S --noconfirm dictd-wn
```

```sh
sudo vim /etc/dict/dictd.conf
```

```
global {
    listen_to localhost
    port 2628
}

access {
  allow *
}

# For example
database wn {
	data /usr/share/dictd/wn.dict.dz
	index /usr/share/dictd/wn.index
}

#LASTLINE
```

```sh
sudo vim /etc/dict/dict.conf
```

```sh
server localhost
# server dict.org
```

```sh
sudo systemctl enable --now dictd.service
```

## usage

```sh
dict --host localhost --port 2528 -I -v
dict -h localhost -p 2528 -d <database> <word>
```

[^1]: [dictd.conf](https://gist.github.com/wind0204/d65c7d1b5d7794c4c7fa1a02d5151acc)
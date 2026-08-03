## On Ubuntu 22/24 ARM[^1]

```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
sudo apt-get update
sudo apt-get install ca-certificates wget
sudo install -m 0755 -d /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/docker.asc https://download.docker.com/linux/ubuntu/gpg
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
	"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
	$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
	sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## On Arch

```sh
sudo pacman -S docker docker-compose
sudo systemctl enable --now docker.service
```

## Use repository mirror[^2][^5]

```sh 
sudo mkdir -p /etc/docker
sudo vim /etc/docker/daemon.json
```

```
# Add <docker_status_monitor> site to your bookmark. If failed, you can visit the web page and modify them
{
	"dns": ["8.8.8.8", "8.8.4.4"],
	"registry-mirrors": [
		"https://docker.1ms.run",
		"https://docker.1panel.live",
		"https://docker.ketches.cn"
	]
}
```

```
# Optional
	"experimental": true,
	"default-runtime": "nvidia",
	"runtimes": {
		"nvidia": {
			"path": "/usr/bin/nvidia-container-runtime",
			"runtimeArgs": []
		}
	}
```

```sh
sudo mkdir -p /etc/containers/registries.conf.d
sudo vim /etc/containers/registries.conf.d/docker.conf
```

```
unqualified-search-registries = ["docker.io"]

[[registry]]
location = "docker.io"

[[registry.mirror]]
location = "https://docker.1panel.live"
```

```sh
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## Usage[^3][^4]

```sh
# Do a test
sudo docker run -p 8080:80 --rm nginx
# sudo ufw allow 8080
# Visit http://<docker_host>/8080
```

```sh
# Do a text for NVIDIA Container Toolkit
sudo docker run --gpus all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark
```

[^1]: [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
[^2]: [Docker / Podman 安装与换源](https://wcbing.top/linux/containers/install/)
[^3]: [Docker Hub - Quickstart](https://docs.docker.com/docker-hub/quickstart/)
[^4]: [Container Runtime Initialization Errors](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#container-runtime-initialization-errors)
[^5]: [Using the NVIDIA Container Runtime for Docker](https://docs.nvidia.com/dgx/nvidia-container-runtime-upgrade/index.html#using-nv-container-runtime)
# podman

```bash
sudo pacman -S podman podman-compose aardvark-dns
```

### Зеркало

```bash
sudo nano /etc/containers/registries.conf
```

```editorconfig
unqualified-search-registries = ["docker.io", "quay.io"]

[[registry]]
prefix = ""
location = "docker.io"

[[registry.mirror]]
location = "dockerhub.timeweb.cloud"
insecure = false

[[registry]]
prefix = ""
location = "quay.io"
```

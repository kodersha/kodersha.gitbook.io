# 📦 Разработка

### podman

```bash
sudo pacman -S podman podman-compose aardvark-dns
```

#### Зеркало docker

На случай блокировки docker.io. Отредактируйте конфигурацию:

{% tabs %}
{% tab title="registries.conf" %}
```bash
sudo nano /etc/containers/registries.conf
```
{% endtab %}

{% tab title="→" %}
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
{% endtab %}
{% endtabs %}

### github

```bash
sudo pacman -S --needed git github-cli gitui
```

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.compression 0
```

### visual studio code

{% code overflow="wrap" %}
```bash
yay -S visual-studio-code-bin
```
{% endcode %}

### figma

```bash
yay -S figma-linux figma-agent-linux
```

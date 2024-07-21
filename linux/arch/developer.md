---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# 📦 Разработка

### podman

```bash
sudo pacman -S podman podman-compose aardvark-dns
```

#### Конфигурация:

{% tabs %}
{% tab title="registries.conf" %}
```bash
sudo nano /etc/containers/registries.conf
```
{% endtab %}

{% tab title="→" %}
```editorconfig
unqualified-search-registries = ["docker.io", "quay.io"]
```

На случай блокировки docker.io добавьте:

```ini
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

{% tabs %}
{% tab title="Установить" %}
```bash
sudo pacman -S --needed git github-cli gitui
```
{% endtab %}

{% tab title="→" %}
Конфигурация, укажите имя и email как у вашего аккаунта на github.

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.compression 0
```
{% endtab %}
{% endtabs %}



### visual studio code

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.visualstudio.code
```
{% endcode %}
{% endtab %}

{% tab title="AUR" %}
{% code overflow="wrap" %}
```bash
pikaur -S visual-studio-code-bin
```
{% endcode %}
{% endtab %}
{% endtabs %}



### figma

{% code title="figma font helper" overflow="wrap" %}
```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/neetly/figma-agent-linux/main/scripts/install.sh)"
```
{% endcode %}

{% embed url="https://github.com/neetly/figma-agent-linux" %}

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

# ☕ Разработка

### podman

{% code overflow="wrap" %}
```bash
aura -S podman podman-compose
```
{% endcode %}

#### Конфигурация:

{% tabs %}
{% tab title="registries.conf" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/containers/registries.conf
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
{% code overflow="wrap" %}
```editorconfig
[registries.search]
registries = ['docker.io']
```
{% endcode %}

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
{% tab title="homebrew" %}
{% code overflow="wrap" %}
```bash
brew install gh gitui
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S --needed git github-cli gitui
```
{% endcode %}
{% endtab %}
{% endtabs %}

Конфигурация, укажите имя и email как у вашего аккаунта на github.

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.compression 0
```



### visual studio code

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A visual-studio-code-bin
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.visualstudio.code
```
{% endcode %}
{% endtab %}
{% endtabs %}



### figma

[figma font helper](https://github.com/neetly/figma-agent-linux)

{% code overflow="wrap" %}
```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/neetly/figma-agent-linux/main/scripts/install.sh)"
```
{% endcode %}

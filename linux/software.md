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
    visible: true
---

# Программы

### visual studio code

{% tabs %}
{% tab title="fedora" %}
Добавьте репозиторий:

{% code overflow="wrap" %}
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```
{% endcode %}

{% code overflow="wrap" %}
```bash
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
```
{% endcode %}

Установите `code`:

{% code overflow="wrap" %}
```bash
sudo dnf install code
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
yay -S visual-studio-code-bin
```
{% endcode %}
{% endtab %}
{% endtabs %}



### spotify

```bash
flatpak install spotify
```

Опционально AdBlock для Spotify:

```bash
bash <(curl -sSL https://spotx-official.github.io/run.sh)
```

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

# 📀 Приложения

### firefox

{% tabs %}
{% tab title="pacman" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S firefox firefox-i18n-ru
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install flathub org.mozilla.firefox
```
{% endcode %}
{% endtab %}
{% endtabs %}



### spotify

{% tabs %}
{% tab title="AUR" %}
{% code overflow="wrap" %}
```bash
yay -S spotify
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install flathub com.spotify.Client
```
{% endcode %}
{% endtab %}

{% tab title="AdBlock" %}
Опционально AdBlock для Spotify

{% code overflow="wrap" %}
```bash
bash <(curl -sSL https://spotx-official.github.io/run.sh)
```
{% endcode %}
{% endtab %}
{% endtabs %}

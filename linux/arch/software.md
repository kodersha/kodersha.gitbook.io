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
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install firefox
```
{% endcode %}
{% endtab %}

{% tab title="pacman" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S firefox firefox-i18n-ru
```
{% endcode %}
{% endtab %}
{% endtabs %}



### spotify

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install spotify
```
{% endcode %}

Опционально AdBlock для Spotify:

{% code overflow="wrap" %}
```bash
bash <(curl -sSL https://spotx-official.github.io/run.sh)
```
{% endcode %}
{% endtab %}

{% tab title="AUR" %}
{% code overflow="wrap" %}
```bash
pikaur -S spotify
```
{% endcode %}
{% endtab %}
{% endtabs %}

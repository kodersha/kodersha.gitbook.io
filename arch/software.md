---
icon: floppy-disk
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

# Приложения

### firefox

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install org.mozilla.firefox
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S firefox firefox-i18n-ru
```
{% endcode %}
{% endtab %}
{% endtabs %}



### spotify

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.spotify.Client
```
{% endcode %}

Опционально AdBlock для Spotify:

{% code overflow="wrap" %}
```bash
bash <(curl -sSL https://spotx-official.github.io/run.sh)
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A spotify
```
{% endcode %}

Опционально AdBlock для Spotify:

{% code overflow="wrap" %}
```bash
bash <(curl -sSL https://spotx-official.github.io/run.sh)
```
{% endcode %}
{% endtab %}
{% endtabs %}

---
icon: box
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Репозитории



### flatpak

Позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как `flathub`.

Установите `flatpak`:

{% code overflow="wrap" %}
```bash
aura -S flatpak
```
{% endcode %}

Добавьте репозиторий `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

{% embed url="https://flathub.org/" %}



### homebrew

[Homebrew](https://brew.sh/) для linux - это менеджер пакетов, изначально разработанный для macOS, который позволяет легко устанавливать, обновлять и управлять программным обеспечением на linux-системах.

{% code overflow="wrap" %}
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
{% endcode %}

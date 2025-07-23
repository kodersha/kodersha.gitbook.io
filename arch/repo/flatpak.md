---
description: >-
  Позволяет устанавливать и запускать приложения в изолированных контейнерах,
  обеспечивая совместимость между дистрибутивами, автоматическое управление
  зависимостями и безопасное обновление.
---

# Flatpak



### Установка

{% stepper %}
{% step %}
Установите `flatpak`:

{% code overflow="wrap" %}
```bash
aura -S flatpak
```
{% endcode %}
{% endstep %}

{% step %}
Добавьте [репозиторий](https://flathub.org/ru) `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}
{% endstep %}
{% endstepper %}



{% content-ref url="../terminal/cmd.md" %}
[cmd.md](../terminal/cmd.md)
{% endcontent-ref %}

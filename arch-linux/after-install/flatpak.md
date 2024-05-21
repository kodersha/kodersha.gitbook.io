---
description: >-
  Позволяет устанавливать изолированные в песочнице приложения, которые не
  влияют на основную систему.
---

# Flatpak

Установка flatpak

{% code overflow="wrap" %}
```bash
sudo pacman -S flatpak
```
{% endcode %}

Добавление репозитория flathub для system

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

Добавление репозитория flathub для user

{% code overflow="wrap" %}
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

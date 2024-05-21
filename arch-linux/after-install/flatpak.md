---
description: >-
  Позволяет устанавливать изолированные в песочнице приложения, которые не
  влияют на основную систему.
---

# Flatpak

{% code title="Установка flatpak" overflow="wrap" %}
```bash
sudo pacman -S flatpak
```
{% endcode %}

{% code title="Добавление репозитория flathub для system" overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

{% code title="Добавление репозитория flathub для user" overflow="wrap" %}
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

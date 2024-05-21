---
description: >-
  Пользовательский репозиторий Arch (Arch User Repository, AUR) — поддерживаемое
  сообществом хранилище программ для пользователей Arch.
---

# Пользовательский репозиторий AUR

Установка yay - менеджера пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}

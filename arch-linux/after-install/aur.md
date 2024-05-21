---
description: >-
  Пользовательский репозиторий Arch (Arch User Repository, AUR) — поддерживаемое
  сообществом хранилище программ для пользователей Arch.
---

# Пользовательский репозиторий AUR

{% code title="Установка yay - менеджера пакетов AUR." overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}
